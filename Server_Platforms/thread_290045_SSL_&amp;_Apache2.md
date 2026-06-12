---
title: "SSL &amp; Apache2"
date: 2006-10-31
forum: Server Platforms
---

### Post by DannyG on 2006-10-31
Hello,

I am trying to get SSL working on my Apache2 webserver. I followed the "Perfect Ubuntu Setup" guide on howtoforge.com.

Basically, I have OpenSSL installed. I have edited "/etc/apache2/ports.conf" and added "Listen 443".

I then did

```
a2enmod ssl
a2enmod rewrite
a2enmod suexec
a2enmod include
```

and then

```
/etc/init.d/apache2 force-reload
```

But when I try and navigate to [https://www.mydomain.com/](https://www.mydomain.com/) I get a 

"mydomain.com has sent an incorrect or unexpected message. Error code: -12263" in my browser (Firefox 2.0, for the record).

Does anyone have any idea how I get SSL working? I am using Webmin to admin the server, and I can connect to the Webmin control panel with SSL on port 10000, so I know OpenSSL is installed and working.

Thanks in advance,

Daniel.

---

### Post by DannyG on 2006-10-31
Sorted, found this great Wiki entry:

[https://help.ubuntu.com/community/forum/server/apache2/SSL](https://help.ubuntu.com/community/forum/server/apache2/SSL)

Everything I needed.

---

