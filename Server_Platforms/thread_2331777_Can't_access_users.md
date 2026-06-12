---
title: "Can't access users"
date: 2016-07-25
forum: Server Platforms
---

### Post by ray397 on 2016-07-25
Total noob here!
I just completed installing ubuntu server/ LAMP. I can access 192.168.1.230 (/var/www/html) and 192.168.1.230/phpmyadmin.  When attempting 192.168.1.230/user (any user), webadmin, or webalizer I get "Page not found".   What should I look for?

It is installed on a clean sys with no other OS. Just a learning machine behind an ATT router.
Thanks

---

### Post by SeijiSensei on 2016-07-25
If you run the command
```
sudo a2enmod userdir
```
and restart Apache, you can create a directory called /home/username/public_html.  Files placed there should appear under [http://server/~username/](http://server/~username/).

By default only files in /var/www/html and directories below it are visible via the web server.

---

### Post by howefield on 2016-07-26
Thread moved to the "*Server Platforms*" forum.

---

### Post by ray397 on 2016-07-26
> **SeijiSensei said:**
> If you run the command
```
sudo a2enmod userdir
```
and restart Apache, you can create a directory called /home/username/public_html.  Files placed there should appear under [http://server/~username/](http://server/~username/).

By default only files in /var/www/html and directories below it are visible via the web server.

Thanks for your help.
I clearly have much reading to do!  I created a couple of user directories but don't have permissions to access them and can't ftp to them.

---

