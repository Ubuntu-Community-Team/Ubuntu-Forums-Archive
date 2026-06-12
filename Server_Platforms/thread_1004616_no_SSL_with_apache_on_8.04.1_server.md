---
title: "no SSL with apache on 8.04.1 server"
date: 2008-12-07
forum: Server Platforms
---

### Post by lucloubier on 2008-12-07
Hi!
I installed apache on Ubuntu server 8.04.1.
I am not able to run SSL. I checked the intall doc on this site and followed the install procedure.

I am able to get the "It works!" page both using [http://ip/](http://ip/) and [http://ip:443/](http://ip:443/) but not [https://ip/](https://ip/) ( I get an 'ssl_error_rx_record_too_long' error).

80 and 443 ports are open

Looking at error log I see this each time I try https:
Invalid method in request \x16\x03\x01  

Anyone has an idea on how to fix this ?

---

### Post by Dr Small on 2008-12-07
Did you enable mod_ssl?
```
sudo a2enmod ssl
```

Also, don't forget to setup a VirtualHost container for the SSL site, and setup the SSL certificate/keyfile


Edit: Even though this was a thread asking for support (by me), there was nothing wrong with the process of setting up SSL for apache, by my instructions:
[http://ubuntuforums.org/showpost.php?p=6127001&postcount=1](http://ubuntuforums.org/showpost.php?p=6127001&postcount=1)

---

### Post by lucloubier on 2008-12-13
Hi Dr Small!

I started from scratch with a new ubuntu server install and I get the same error after following your instructions ([http://ubuntuforums.org/showpost.php...01&postcount=1](http://ubuntuforums.org/showpost.php...01&postcount=1))

Looking at the error log, I see this :
[Sat Dec 13 07:15:48 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g configured -- resuming normal operations
[Sat Dec 13 07:15:51 2008] [error] [client 192.168.10.55] Invalid method in request \x16\x03\x01

Got an idea ?

---

