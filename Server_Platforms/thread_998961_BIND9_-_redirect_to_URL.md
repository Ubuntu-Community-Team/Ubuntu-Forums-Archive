---
title: "BIND9 - redirect to URL ???"
date: 2008-12-01
forum: Server Platforms
---

### Post by eufran on 2008-12-01
Hello, I´m using BIND9 and Ubuntu, my problem is:

My domain in bind is "iesfran.com" and i like when clients in firefox puts "mail.iesfran.com" redirect to "mail.iesfran.com/correoweb"

Is possible????


Thanks

---

### Post by cdenley on 2008-12-01
> **eufran said:**
> Hello, I´m using BIND9 and Ubuntu, my problem is:

My domain in bind is "iesfran.com" and i like when clients in firefox puts "mail.iesfran.com" redirect to "mail.iesfran.com/correoweb"

Is possible????


Thanks

You would have to configure that with the web server listening on mail.iesfran.com. DNS has nothing to do with request URI's or HTTP redirection headers.

---

### Post by eufran on 2008-12-01
I dont understand.

My resolv.conf:
search iesfran.com

But i like when clients goes to mail.iesfran.com redirect to mail.iesfran.com/correoweb


THANKS

---

### Post by hictio on 2008-12-01
Its like cdenley told you.
The Bind part of the solution will make that anyone on the internet that types "mail.iesfran.com" will be directed to the correct server.
And the Apache part of the solution will be in charge -with a redirect, or an alias- to conduct all the traffic that reaches "http://mail.iesfran.com" goto "http://mail.iesfran.com/correoweb"

---

### Post by cdenley on 2008-12-01
> **eufran said:**
> I dont understand.

My resolv.conf:
search iesfran.com

But i like when clients goes to mail.iesfran.com redirect to mail.iesfran.com/correoweb


THANKS

Then configure your web server to do so. This is the way it works:
-your user enters [http://mail.iesfran.com/](http://mail.iesfran.com/)
-your user's computer sends a DNS query, and resolves mail.iesfran.com to an IP address. This fails for me, so I'll use this example: 123.123.123.123.
-the user's browser now knows where to connect. It connects to the web server listening on 123.123.123.123 port 80. It then sends an HTTP request, such as "GET / HTTP/1.1".
-the web server listening on port 80 (NOT BIND) would accept the connection, receive the request, then send a redirect response.

I can't tell you how to configure your web server if you don't tell me what you're using. Once again, http redirection has nothing to do with bind or dns. Are you using apache? Is it running on the same ubuntu server with bind you referred to in your first post?

---

