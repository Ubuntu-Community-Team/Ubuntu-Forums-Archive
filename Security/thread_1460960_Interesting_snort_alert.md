---
title: "Interesting snort alert"
date: 2010-04-23
forum: Security
---

### Post by noway2 on 2010-04-23
I received the following snort alert today: SPYWARE-PUT Trackware casalemedia runtime detection (SID 5910).

As I understand it, this indicates that packet inspection saw an attempt to do a PUT of a tracking cookie to me.  However, my searching isn't finding a whole lot on this. Is my understanding of this alert correct and is there anything I should do besides clear out the cookies?

A little background: the server running snort does not have a true "browser"  The most it has is Lynx.  At the time of the alert, I was using the server as a socks proxy for a remote browser.  I am assuming that the remote browser would be where the cookie was going?  I looked in ther snort logs and it showed the packet as being from a website that I did access via the proxy, however the snort IP address appears to be a TW road runner address(?).

---

### Post by OpSecShellshock on 2010-04-23
Were you able to see the payload? That would list the http request, with the headers. If your IP was the source, try to see if it was a POST or GET request. These particular Snort rules will match on either of them. Most likely, it was just a tracking cookie or script, and can be dumped manually or after the session is terminated. I doubt it's actual spyware.

As for the TWC address, I know that part of their service is that they maintain server farms full of cached data that they sometimes deliver content from instead of sending traffic all the way to the requested web server. It approximates an increase in throughput speed. It's pretty trustworthy since they'll refresh the cache whenever a change is made to the content on the original server. Technically, though, it is a MITM.

---

### Post by noway2 on 2010-04-24
Here is what I have from the log.  It was a cookie from some place called as.casalemedia.com.  I think your right about it being a simple cookie.  It just caught my attention because I had never seen that particular alert before.

HTTP/1.1 302 Moved Temporarily
Server: Apache
P3P: policyref="/w3c/p3p.xml", CP="NOI DSP COR DEVa TAIa OUR BUS UNI"
Location: [http://as.casalemedia.com/s?s=112243&u=http%3A//www.whatismyip.com/&f=1&id=5672234518.796508&C=1](http://as.casalemedia.com/s?s=112243&u=http%3A//www.whatismyip.com/&f=1&id=5672234518.796508&C=1)
Content-Length: 296
Content-Type: text/html; charset=iso-8859-1
Expires: Fri, 23 Apr 2010 18:40:54 GMT
Cache-Control: max-age=0, no-cache, no-store
Pragma: no-cache
Date: Fri, 23 Apr 2010 18:40:54 GMT
Connection: keep-alive
Set-Cookie: CMID=xHO--0o0WqoAACr3XAwAAABD;domain=casalemedia.com;path=/;expires=Sat, 23 Apr 2011 18:40:54 GMT
Set-Cookie: CMPS=202;domain=casalemedia.com;path=/;expires=Thu, 22 Jul 2010 18:40:54 GMT
Set-Cookie: CMPP=014;domain=casalemedia.com;path=/;expires=Thu, 22 Jul 2010 18:40:54 GMT
^M
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>302 Found</title>
</head><body>
<h1>Found</h1>
<p>The document has moved <a href="http://as.casalemedia.com/s?s=112243&amp;u=http%3A//www.whatismyip.com/&amp;f=1&amp;id=5672234518.796508&amp;C=1">here</a>.</p>
</body></html>

---

### Post by OpSecShellshock on 2010-04-24
Looks to me like a geolocation cookie, or perhaps that in combination with an ISP identifier. Your session has been given a unique ID so that all sites visited during that session that are partners with or serving content of that ad company will know that it's your computer and which ad content you've seen or clicked on.

---

### Post by noway2 on 2010-04-26
I think you are right.  It looks that way to me too, now that I have a better understanding of how to read the data.

Thank you for your assistance.

---

