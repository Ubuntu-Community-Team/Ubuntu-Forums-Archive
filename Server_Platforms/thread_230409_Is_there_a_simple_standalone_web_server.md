---
title: "Is there a simple standalone web server?"
date: 2006-08-05
forum: Server Platforms
---

### Post by Jose Catre-Vandis on 2006-08-05
Looking for a simple standalone web server that provides a configurable html interface for file serving on my LAN. Some similar to **GNUMP3d** *(which is excellent for Music)*, or in Windows like the freeware HFS, or Easy File Sharing. Don't need the complexities of Apache/PHP/Mysql to run it.

Have searched repositories and Forum to no avail :)

---

### Post by sir_mud on 2006-08-05
Try dhttpd, it's pretty simple and should suit your needs. Not sure which repository its in, should be in universe. In synaptic, search for "webserver", it's fairly close to the top.

---

### Post by Jose Catre-Vandis on 2006-08-06
> **sir_mud said:**
> Try dhttpd, it's pretty simple and should suit your needs. Not sure which repository its in, should be in universe. In synaptic, search for "webserver", it's fairly close to the top.

Thanks, but dhttpd and its friend thttpd are OK as small web servers but do not, as far as I can see, generate directory listings in html. I would have to write all the pages and html myself :( Trying to avoid that :)

---

### Post by lamego on 2006-08-06
Give a try to:
```
apt-cache search light httpd
```
Anyway if you are looking for file sharing services httpd is not the best option, you should use something like SAMBA or SFTP .

---

### Post by stormblue on 2006-08-06
Have you tried [Ubuntu Center Hive]("http://icenterx.info/")  It might be what you're looking for although it does have apache/mysql

---

### Post by az on 2006-08-06
> **Jose Catre-Vandis said:**
> Looking for a simple standalone web server that provides a configurable html interface for file serving on my LAN. Some similar to **GNUMP3d** *(which is excellent for Music)*, or in Windows like the freeware HFS, or Easy File Sharing. Don't need the complexities of Apache/PHP/Mysql to run it.

Have searched repositories and Forum to no avail :)

You can just install apache2.  It does not require PHP nor Mysql, but you can use them together if you want.  By default, apache will serve directories the way you describe.

And by itself, apache does not take up a lot of memory or disk space.

---

### Post by fdoving on 2006-08-06
I strongly recommend 'lighttpd'.
It is in the archives, you can read about it at [http://www.lighttpd.net/](http://www.lighttpd.net/)

- Frode

---

### Post by Jose Catre-Vandis on 2006-08-06
> **azz said:**
> You can just install apache2.  It does not require PHP nor Mysql, but you can use them together if you want.  By default, apache will serve directories the way you describe.

And by itself, apache does not take up a lot of memory or disk space.

Yes Azz, I think that is going to be it. I had a look at a few php scripts, but I think fancy indexing and a few other options settings using Apache2 will be the best I can do. :grin:

---

