---
title: "SSL setup problem"
date: 2011-02-10
forum: Server Platforms
---

### Post by 0sinner on 2011-02-10
Hello,

I am running an Ubuntu Server on a VirtualBox VM running on my windows machine.

So I've created a self-signed certificate using the following tutorial:
[https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html](https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html)

From this tutorial I'm left with 3 files:
server.key
server.csr
server.crt

Then I found this very similar tutorial that has an extra bit on installing the certificates in apache:
[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html)

So I followed it's instructions which boil down to this:
run "sudo a2enmod ssl"
copy server.crt to /etc/ssl/certs/
copy server.key to /etc/ssl/private/
Open ports.conf and add "Listen 443"

My ports.conf already includes the following, so I left it unchanged:
<IfModule mod_ssl.c>
 Listen 443
</IfModule>
<IfModule mod_gnutls.c>
 Listen 443
</IfModule>

So I'm thinking this should work now. However in Chrome I get:

SSL connection error
Unable to make a secure connection to the server. This may be a problem with the server, or it may be requiring a client authentication certificate that you don't have.
Error 107 (net::ERR_SSL_PROTOCOL_ERROR): SSL protocol error.

IE8 gives me a typical "Internet Explorer cannot display the webpage"

Note that [https://vmip/](https://vmip/) fails while [http://vmip/](http://vmip/) works fine, so it's definitely something in my ssl setup I'm thinking.


Any help or tips on how to troubleshoot would be appreciated,
~0

---

### Post by rudelgurke on 2011-02-11
What does your error_log or ssl_error_log report ?

---

### Post by 0sinner on 2011-02-11
Ok, so I looked up where the error logs are. I found them in /var/log/apache2/error.log and error.log.1

I visited the HTTPS site again (with chrome) and checked the error log again and the following lines came up:

[Fri Feb 11 13:12:35 2011] [error] [client 192.168.0.50] Invalid method in request \x16\x03
[Fri Feb 11 13:12:35 2011] [error] [client 192.168.0.50] Invalid method in request \x16\x03

What does that mean?

---

### Post by 0sinner on 2011-02-11
OK, so some quick googling tells me that my computer is trying to send unencrypted HTML where the browser is expecting SSL protocols.

However I'm still unsure how to diagnose where the configuration is incorrect.

I'll continue trying to get it with google and will let you know if I solve it.


~0

---

### Post by 0sinner on 2011-02-11
OK,

So after whole bunch of messing around, here is what I found.

I tried changing the default-ssl file in sites-available from:
<VirtualHost _default_:443>

to:
<VirtualHost *:443>
and
<VirtualHost 192.168.0.155:443>

After each change I did an apache2 restart. This changed nothing so I changed it back to "_default_"

As a part of the troubleshooting I telnetted from my windows PC to the server on port 443. Not only does it not send any encrypted transmission. When I type "GET /" or "GET /index.html" it just returns a standard HTML 404 page.

I wanted to set this up so I'd have 2 document roots. One would be for the regular site and the other for all SSL requests. So the document root in sites-available/default is "/mnt/serverroot" and the document root in sites-available/default-ssl is "/mnt/serverrootssl". Another oddity I noticed is that requests on 443 are NOT routed to /mnt/serverrootssl.

When I checked the error log after doing a telnet to 443 each request emits the same error:
[Fri Feb 11 14:39:22 2011] [error] [client 192.168.0.50] File does not exist: /etc/apache2/htdocs

Sounds like it's being forwarded to the wrong VHost. How do I troubleshoot from here?

---

### Post by 0sinner on 2011-02-11
OK,

So I figured it out. I am pretty new to linux and didn't know how a LAMP server works. I had no placed a soft link in sites-enabled to the default-ssl file in sites-available. Once I did this all works correctly.


Thanks,
~0

---

