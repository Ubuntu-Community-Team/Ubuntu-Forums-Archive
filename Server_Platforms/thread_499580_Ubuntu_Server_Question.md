---
title: "Ubuntu Server Question"
date: 2007-07-12
forum: Server Platforms
---

### Post by NautTboy on 2007-07-12
I'd tried Ubuntu Desktop and I like it.

A friend of mine just showed me his 450Mhz running a Ubuntu Server and now I'm interested.

So this ISO that i've download should have all the things(apache, sql, php etc) i need to start up my server and start hosting?  
Well, other than getting a domain.

It would be so cool if i can just inhouse host my own website.

---

### Post by Footballkid4 on 2007-07-12
You can install a server on desktop edition too, the difference really is what packages come ready on the cd.

From the desktop edition, however, you should be able to open a terminal and do:

```
sudo apt-get install apache2 mysql-server mysql-client php5 php5-common libapache2-mod-php5 php5-mysql ssh proftpd
```

If it asks for a password, it's your current account password.

From there, place your documents in /var/www, and you should be running a server.  Granted you can go a lot more in depth than that, but there are plenty of tutorials about this sort of thing.  If you really want the server feel with no GUI (no Gnome interface)

```
sudo apt-get remove gnome-desktop --purge gnome-desktop
```

Should get rid of the GUI for you...then you're down to just a terminal

---

