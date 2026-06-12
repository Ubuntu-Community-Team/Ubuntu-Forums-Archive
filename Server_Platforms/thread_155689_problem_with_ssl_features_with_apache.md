---
title: "problem with ssl features with apache"
date: 2006-04-05
forum: Server Platforms
---

### Post by Rollo Tamasi on 2006-04-05
Hi guys, i'm following the perfect server setup on howtoforge and when i get to the part for apache ssl i am required to do the following.

> Now we have to enable some Apache modules (SSL,  rewrite and suexec):

cd /etc/apache2/mods-enabled
ln -s /etc/apache2/mods-available/ssl.conf ssl.conf
ln -s /etc/apache2/mods-available/ssl.load ssl.load
ln -s /etc/apache2/mods-available/rewrite.load rewrite.load
ln -s /etc/apache2/mods-available/suexec.load suexec.load
ln -s /etc/apache2/mods-available/include.load include.load

Restart Apache:

/etc/init.d/apache2 restart



i can get into the directory no problem. But then i type ln -s /etc/apache2/mods-available/ssl.conf ssl.conf into the termainal and i get the following error message 
"ln: creating symbolic link `ssl.conf' to `/etc/apache2/mods-available/ssl.conf': Permission denied"
 
The termainal screen looks like this:
> 
cormac@server:~$ cd /etc/apache2/mods-enabled
cormac@server:/etc/apache2/mods-enabled$ ln -s /etc/apache2/mods-available/ssl.conf ssl.conf
ln: creating symbolic link `ssl.conf' to `/etc/apache2/mods-available/ssl.conf': Permission denied


I am logged in as SU, does anyone know what i need to do to reslove the problem?

---

