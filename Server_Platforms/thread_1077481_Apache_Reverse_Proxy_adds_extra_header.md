---
title: "Apache Reverse Proxy adds extra header"
date: 2009-02-22
forum: Server Platforms
---

### Post by lucas42 on 2009-02-22
Hi,

   I've set up a reverse proxy in apache so that a program which runs on another port appears to run on port 80.

I enabled the modules proxy and proxy_http
and added this to my apache.conf file: 
```
<VirtualHost *>

ProxyRequests Off

<Proxy *>
   Order deny,allow
   Allow from all
</Proxy>
ServerName some.example.com

ProxyPass / http://some.example.com:55802/
#ProxyPassReverse /  http://some.example.com:55802/


</VirtualHost>
```
(I've tried with and without ProxyPassReverse but that didn't seem to make a difference)

The Proxy works fine, the only problem is that Apache adds an extra header to the page.
The other program already includes a header, so now there's two, which browsers take to mean that the second one is part of the body.

How do I get Apache to send the page As-is without adding or altering anything?

Cheers.

---

### Post by Thirtysixway on 2009-02-22
What header is it adding?

---

### Post by lucas42 on 2009-02-22
It seems to depend on the page, for example, for a css stylesheet it adds:
```
HTTP/1.1 200 OK
Date: Sun, 22 Feb 2009 16:56:25 GMT
Transfer-Encoding: chunked
Content-Type: text/css

```

I don't know if it copies Content-type from the original header, or works it out based on the file extension.

---

### Post by mhausherr on 2009-06-15
Hello 
 
Has anyone found a solution to this problem? I'm dealing with the exact same issue.

Thanks - and greetings from Switzerland
Michael

---

