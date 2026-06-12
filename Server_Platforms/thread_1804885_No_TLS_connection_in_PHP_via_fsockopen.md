---
title: "No TLS connection in PHP via fsockopen"
date: 2011-07-15
forum: Server Platforms
---

### Post by lanthaler on 2011-07-15
Hello,
 
I'm trying since a couple of days to establish a TLS connection to a SMTP server in PHP via fsockopen(). I tried almost everything and googled for hours but still I didn't get it working.
 
The PHP code looks as follows:
 
[PHP]
$fp = fsockopen("tls://smtp.xxxx.com", 25, $errno, $errstr, 30);
if (!$fp) {
    echo "$errstr ($errno)<br />\n";
} else {
 // some other stuff
}
[/PHP]
 
The output is just (0), i.e., $errstr = null and $errno = 0.
 
OpenSSL is installed and enabled:
[INDENT]OpenSSL support: enabled 
OpenSSL Library Version: OpenSSL 0.9.8o 01 Jun 2010 
OpenSSL Header Version: OpenSSL 0.9.8o 01 Jun 2010 
[/INDENT]and the following stream socket transports are registered:
[INDENT]tcp, udp, unix, udg, ssl, sslv3, sslv2, tls.
[/INDENT]The port is open as a telnet from the console works.
 
Any ideas what's wrong or how I could at least get some more debug output?
 
 
Thanks,
Markus

---

### Post by lanthaler on 2011-07-15
Btw. I just tested it from the command line and it works from there but not when executed via Apache. So it has to be either a Apache or PHP configuration issue IMHO.

---

