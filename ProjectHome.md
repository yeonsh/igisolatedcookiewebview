# IGIsolatedCookieWebView #

**A WebView subclass that uses its own internal non-permanent cookie storage and does not access or affect the system-wide shared cookie storage.**

## Inner Workings ##

As per [this StackOverflow answer](http://stackoverflow.com/questions/364219/how-can-i-have-multiple-instances-of-webkit-without-sharing-cookies/365080#365080), this is a WebView subclass that automatically instantiates a resource loading delegate (a private class), which implements webView:resource:willSendRequest:redirectResponse:fromDataSource: to block normal cookie handling and insert the proper cookies and webView:resource:didReceiveResponse:fromDataSource: to capture returned cookies.  Cookies are only stored in memory, not written to disk, and each instance has its own cookie storage, so cookies only exist while the instance of IGIsolatedCookieWebView exists and only exist for a particular instance of IGIsolatedCookieWebView.

### Comments, etc.: [the blog](http://2718.us/blog/tag/igisolatedcookiewebview/) ###