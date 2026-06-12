---
title: "Ubuntu 10.04 (lucid) home web server error 255 on file sharing"
date: 2011-06-20
forum: Server Platforms
---

### Post by powerwatt on 2011-06-20
Day 2 of my Ubuntu saga.

I am trying to set up a simple web server on my backup server.

Everything is installed (mysql, apache2, php, etc)

I now need to share /var/www however I can't seem to be able to do this I get the error message when I try to share the folder
[quote=]'net usershare' returned error 255: net usershare add: failed to add share www. Error was Operation not permitted[/quote]

So far I have added the line to smb.conf
[quote=]usershare owner only = false[/quote]

I have tried chmod -R 777 /var/www and still I get the error coming up.

Does anyone know what I can do to find what I am doing wrong?

---

### Post by collisionystm on 2011-06-20
These links might be of some use.

[http://www.jonathanmoeller.com/screed/?p=3005](http://www.jonathanmoeller.com/screed/?p=3005)

[http://www.itchyhippo.com/?p=157](http://www.itchyhippo.com/?p=157)

I followed the 2 of these guides to build my wordpress server. It is all similar because its web. Just follow the permissions sections

---

### Post by powerwatt on 2011-06-20
Thanks I will give them a go

---

### Post by powerwatt on 2011-06-21
I have followed these instructions to the letter [http://www.ubuntugeek.com/installing-wordpress-3-0-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/installing-wordpress-3-0-on-ubuntu-10-04-lucid-lynx.html)

Up to where I get to enter the address after changing wp-config.php.

I get a blank page loading (0.02kb of white screen goodness). I am assuming I have done something wrong with regard to setting up my database in phpmyadmin?

---

