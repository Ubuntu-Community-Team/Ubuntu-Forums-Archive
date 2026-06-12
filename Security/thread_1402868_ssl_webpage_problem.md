---
title: "ssl webpage problem"
date: 2010-02-09
forum: Security
---

### Post by mickey13 on 2010-02-09
I have a security certificate installed on my Ubuntu server.  The main page is being transmitted via https, but the resources the main page accesses are being transmitted in http (no 's').  Using HttpWatch here is an example:

[https://example.com/](https://example.com/)
[http://example.com/stylesheets/main.css](http://example.com/stylesheets/main.css)
[http://example.com/scripts/main.js](http://example.com/scripts/main.js)

How do I get everything from the website to be sent over https?  The reason this is a problem is IE8 gives a warning each time a page is accessed on the site.  Thanks for the help.

---

### Post by mickey13 on 2010-02-10
IE8 is complaining that the page being navigated to is not transmitting all resources over port 443.  In fact only the page itself is, the other resources (scripts, stylesheets) are being transmitted over port 80.  Anyone know if this is a virtualhost problem?

---

### Post by yogesh.girikumar on 2010-02-11
Hi,

This could be a problem with the web page html coding. When calling for css files and js files, the
convention is to use a relative URI rather than a full address.

```
<link rel="stylesheet" href="http://something.com/css/cssfile.css">

```will fetch the stylesheet over http, because it has been explicitly given as a http address.

 Instead, you can try a relative URI

```
<link rel=stylesheet" href="/css/cssfile.css">
```without the [http://domainname.com](http://domainname.com) !

The browser will request for the resources ( js files, stylesheets etc., ) for the page from the server over the same protocol in which  the main page was received.

Hope this helps !

---

