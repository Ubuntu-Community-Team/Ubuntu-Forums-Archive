---
title: "Main apachee2 configuration file"
date: 2009-11-28
forum: Server Platforms
---

### Post by U-boy on 2009-11-28
In my text book it says that /etc/apache2/httpd.conf is Apache's main configuration file. Bun on my Ubuntu Server 9.10 it is empty. All the info is in apache2.conf file in the same directory. Is that OK? I mean, will things work smoothly?

---

### Post by Iowan on 2009-11-29
It seems to work on mine...

---

### Post by Juliano Dasilva on 2009-12-01
I have the same question. I thought the configuration file would be httpd.conf. Is apache2.conf the configuration file?

---

### Post by rudy.b on 2009-12-01
Ya, it's supposed to be that way.  Now all the general server configuration stuff goes in /etc/apache2/apache2.conf and site-specific stuff each go in their own config files under /etc/apache2/sites-available/.  That way, instead of having one giant httpd.conf file, it's split up over several files.  Also, making it easier to enable/disable virtual sites with the a2ensite/a2dissite commands.  

Once I got used to the setup, I found it quite handy.

---

### Post by munky99999 on 2009-12-02
Ya I noticed this on 9.1. Everything has been put into apache2.conf


Also ya that a2ensite and a2dissite feature is nice. Though really only forgoes a cp command :)

similarly you can use "service apache2 restart" instead of the /etc/init.d/apache2 restart. Which is really nice because init.d doesnt tabcomplete easily :)

---

