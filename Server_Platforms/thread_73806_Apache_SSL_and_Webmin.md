---
title: "Apache SSL and Webmin"
date: 2005-10-10
forum: Server Platforms
---

### Post by gos on 2005-10-10
Hit there !

I´m running a server with Webmin listening on default port 10000 (SSL) and Apache listening on port 80.  The problem is that after installing Webmin (via sudo apt-get install webmin) Apache always displays "This web server is running in SSL mode..:" when i try to connect to the server with a browser.  Apache is started with -DSSL an I can´t see anything about SSL in the httpd.conf, apache2.conf or anywhere alse.  How do I run apache in non SSL?  Alsa webin doesn´t seem to detect postfix, apache2 - does it support Ubuntu and the latest appls?

best regards, gos

---

### Post by mfigueredo on 2005-10-25
Hi, I'm a newbie but I was getting that message too when trying to open webmin, just put "https://" in front of your webmin address like:

```
https://yourhost:10000
```

My understanding is that webmin runs its own little webserver, so your apache conf doesn't really matters. 

Hope it helps cheers

---

### Post by Pekz0r on 2006-03-30
Had the same probelm.
Some progress with the https:// but now i get access denied

How can i grant my self access to webmin form a remote computer?

I've added this to the /etc/webmin/miniserv.conf file. But no result
allow=127.0.0.1
allow=*
allow=<my IP>

---

