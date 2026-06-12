---
title: "how can I make my computer a server?"
date: 2008-03-09
forum: Server Platforms
---

### Post by yousef156 on 2008-03-09
anyone knows how can i make my computer a server? I use Ubuntu 7.10 :)
Thanks in advanced..

---

### Post by fedex1993 on 2008-03-09
why do you want to make it into a server what do you want the server for like a file web or dhcp server or a proxy like what do you want it to be for

---

### Post by FakeOutdoorsman on 2008-03-09
I'm assuming you want a web server using Apache, mySQL, and php:
[Apache MySQL PHP]("https://help.ubuntu.com/community/ApacheMySQLPHP") [Ubuntu Wiki]

---

### Post by dacool25 on 2008-03-09
If you are going for a web server (to start a website) you'll have to download and configure apache. 

```
sudo apt-get install apache2 apache2-doc apache2-mpm-prefork apache2-utils libexpat1 ssl-cert
```

If you're going more for FTP (So that you can access files when you're not near your server i'd go with proftpd

```
apt-get install proftpd ucf
```

The guys over at [howtoforge.com]("http://howtoforge.com/perfect_server_ubuntu7.10") are great, they have a few how-to's but I'd build a new server if you're going to follow one of those.

Good luck!

---

### Post by Dr Small on 2008-03-09
Please tell us what you want to use this server for, so we can better assist you :)

---

### Post by marca311 on 2008-03-28
i think he means data server

---

