---
title: "Unable to install mod_scgi"
date: 2010-01-23
forum: Server Platforms
---

### Post by emma_peel on 2010-01-23
Hello dear forum.

I'm facing an issue, which is probably stupid, but didn't find the way to correct it, even after a couple of researches.

I want to install mod_scgi. I have install the libapache2-mod-scgi package and changed the httpd.conf. When I try to restart the apache2 server, I got a syntax error :

```
arnaud@Alanine:~$ cat /etc/apache2/httpd.conf
SCGIMount /RPC2 127.0.0.1:5000
arnaud@Alanine:~$ sudo /etc/init.d/apache2 restart
[sudo] password for arnaud: 
 * Restarting web server apache2
Syntax error on line 1 of /etc/apache2/httpd.conf:
Invalid command 'SCGIMount', perhaps misspelled or defined by a module not included in the server configuration
   ...fail!
```

Any idea to make it work ? Thank's in advance for your support.

---

### Post by emma_peel on 2010-01-25
I finally found the way the correct it :

```
sudo a2enmod scgi
```

That may help someone one day.

---

### Post by wt1 on 2010-02-13
I thought you might like to know that this helped me out with my problem. I was about to smash my computer so... THANKS!!!

---

### Post by emma_peel on 2010-02-15
Absolutely, thank you for your post. That may be obvious afterward, but this is the kind of issue that makes you lose time.

---

### Post by n4h0j on 2010-03-28
Thx alot for this one! =)

---

### Post by mazid on 2010-05-16
> **emma_peel said:**
> I finally found the way the correct it :

```
sudo a2enmod scgi
```That may help someone one day.

really thanks, 
it helped me alot

---

### Post by benow on 2010-08-28
some one, some day.  thx.

---

### Post by freeqaz on 2010-12-31
Helped me.

---

### Post by fongmh on 2012-03-20
Still helpful two years later... :D

---

