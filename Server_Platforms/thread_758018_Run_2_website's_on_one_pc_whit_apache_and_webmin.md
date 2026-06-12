---
title: "Run 2 website's on one pc whit apache and webmin"
date: 2008-04-17
forum: Server Platforms
---

### Post by Erik. on 2008-04-17
Hi,

I already looked whit google and on thi website, i found one tutorial but thats does not work for me.

I now have one website running as localhost.

Settings:

Adres: Default
Port: Default
Documentroot: home/erik/webserver
Server name: Default


Could someone explain me how to fix it so i can run 2 website's on my owm pc.?

I need to create a new virtual host but when i do that and i change the settings nothing happens and i can not get on both website's

Hope you can help me

---

### Post by adamos on 2008-04-17
lack of info bro.

are they live websites? or is a testing environment


is it apache 1.3 or apache2

if its live you will need to add a a virtual host and new document root on your 000-default or httpd.conf.

or if its a testing environment just create a new dir on your var/www and go to your browser: localhost/newdir

but i cant say much since you didnt mention your info

---

### Post by PetePete on 2008-04-17
the way you phrase it makes me think that one problem could be that you are not restarting apache after updaing the config .... ?

---

### Post by Erik. on 2008-04-18
Hi,

It's just for testing but mabey i want to rent mij own server and host own website's

I tried what you say but it still does not work.

Firefox says the fage could not be found.

I stopped apache and started again, still the same.

When you are looking for an website that does not exist firefox needs some time to see that.

When i enter my adres it says it can not be found it does not take 1 sec.

What could be the problem? i am behind a router could it be that?

Edit: Apache version 2.2.4

---

### Post by AlphaWu on 2008-04-18
U can add virtual hosts to run many sites.

---

### Post by Erik. on 2008-04-18
Yeah i know, a already added a ertual host but it does not work for me, i don't know what i am doing wrong.

---

### Post by Dr Small on 2008-04-18
An example VirtualHost:
```
#Test.com
<VirtualHost *:80>
        ServerAdmin user@host
        DocumentRoot /path/to/document/root/
        ServerName test.com
        ServerAlias www.test.com
</VirtualHost>
```

---

### Post by Erik. on 2008-04-18
I use the webinterface Webmin, don't think it matters.

---

### Post by solcott on 2008-04-18
Your Apache configuration files are the same whether you are running Webmin or not, Webmin just makes managing the files easier if you aren't familiar with the way the config files work.

There is a pretty good tutorial on this [_**here**_]("http://www.serverwatch.com/tutorials/article.php/1127571"), and you could Google for things like 'Apache Virtual Hosting Tutorial'.

Also, just yesterday actually, I posted a script for automating the installation of Apache / Webmin / Virtualmin.  Virtualmin is an addon for Webmin meant for setting up virtual hosts in Webmin (multiple websites per machine) and you can find that script [_**here**_]("http://ubuntuforums.org/showthread.php?t=758148").

Another thing you could do, is go into your Webmin installation, click 'Servers' / 'Apache Webserver' / 'Edit Config Files' and look through your config files listed for one that contains something like what [_**Dr Small**_]("http://ubuntuforums.org/member.php?u=197439") posted and then post the contents of that file and I'm sure we can point out to you what's wrong with the it.

Good luck :-)

---

