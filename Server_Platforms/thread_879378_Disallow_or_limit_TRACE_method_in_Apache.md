---
title: "Disallow or limit TRACE method in Apache"
date: 2008-08-03
forum: Server Platforms
---

### Post by osjak on 2008-08-03
Hi All,

I have bee researching for a solution for my own server to disable TRACE method to enhance security. I have found that it cannot be turned off via Apache configuration, and using mod_rewrite seems to be the only option:

```
RewriteEngine On 
RewriteCond %{REQUEST_METHOD} ^TRACE 
RewriteRule .* - [F]
```
Source: [http://www.apacheweek.com/issues/03-01-24#news](http://www.apacheweek.com/issues/03-01-24#news)

[COLOR="Gray"]After this solution is applied, my server shuts down connections when TRACE is received:[/COLOR]
**EDIT:** Actually, paying more attention now, it looks like it didn't affect TRACE at all...

```
mypc:~# **telnet www.xxxxx.com 80**
Trying xxx.xxx.xxx.xxx...
Connected to www.xxxxx.com.
Escape character is '^]'.
**TRACE / HTTP/1.0**

HTTP/1.1 200 OK
Date: Mon, 04 Aug 2008 03:24:51 GMT
Server: Apache
Connection: close
Content-Type: message/http

TRACE / HTTP/1.0

Connection closed by foreign host.
```

[COLOR="Gray"]That is fine with me.[/COLOR] However, while poking around, I have found that some Apache servers respond differently:

```
mypc:~# **telnet www.zzzzz.com 80**
Trying zzz.zzz.zzz.zzz...
Connected to www.zzzzz.com.
Escape character is '^]'.
**TRACE / HTTP/1.0**

HTTP/1.1 405 Method Not Allowed
Date: Mon, 04 Aug 2008 03:19:27 GMT
Server: Apache/2.2.9 (Unix) mod_ssl/2.2.9 OpenSSL/0.9.8g DAV/2 mod_auth_passthrough/2.1 mod_bwlimited/1.4 FrontPage/5.0.2.2635
Allow:
Content-Length: 408
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html>
... HTML SNIPPED HERE ...
</html>
Connection closed by foreign host.
```
So it looks like there IS a way to turn TRACE off after all. Does anyone know anything about it?

---

### Post by StickyStyle on 2008-08-04
TraceEnable is what your looking for, [http://httpd.apache.org/docs/2.2/en/mod/core.html#traceenable](http://httpd.apache.org/docs/2.2/en/mod/core.html#traceenable)

The response that you saw in the second case is the result of TraceEnable Off

Also see here [http://www.ducea.com/2007/10/22/apache-tips-disable-the-http-trace-method/](http://www.ducea.com/2007/10/22/apache-tips-disable-the-http-trace-method/)

---

### Post by osjak on 2008-08-04
Thank you! Tt did it.

---

