---
title: "Apache - Reverse Proxy - cross domain issue"
date: 2008-10-19
forum: Server Platforms
---

### Post by ampo on 2008-10-19
Hello.

I'm trying to use reverse proxy to overcome cross server issue.
There is HTML page from server1 and ASP on server2.
Can't request directly from browser to server2 (using xmlHTTPRequest).

This is the JS code:
[I]var oXmlHttpRequest = new ActiveXObject("MSXML2.XMLHTTP");
oXmlHttpRequest.open("GET", "http://MyPC.aabbcc.com/RemoteServerTest/RemoteServer.asp", false);
oXmlHttpRequest.send(null);
sRemoteServerRespons = oXmlHttpRequest.responseText;[/I]

This is the code in httpd.conf:
[I]ProxyRequests Off
ProxyPass aabbcc.com/ [http://ServerName.xxyyzz.com/](http://ServerName.xxyyzz.com/)[/I]

do I miss something?

Thanks.

---

