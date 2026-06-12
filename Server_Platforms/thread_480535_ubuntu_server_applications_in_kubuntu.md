---
title: "ubuntu server applications in kubuntu"
date: 2007-06-21
forum: Server Platforms
---

### Post by smartduck on 2007-06-21
Hi! Is there a way to install ubuntu's server's applications in kubuntu environment?
I want to keep kubuntu and at the same time I want to have a server running in kubuntu environment.
So is there a simple way of installing PHP,MYSQL,APACHE? Or must I use adept package manager? If I need adept - which packages must I choose for LAMP?
Where can I get further instructions about configuring these (server) packages?

K~Ubuntu is great! Thanks to the developers and to everybody contributing to this communitee.

Yours in faith, Grega, the Smart duck from Peace refuge:KS

---

### Post by dmizer on 2007-06-22
server applications are gui independant.  they are (for the most part) configured via command line only, so it doesn't matter if you use gnome, or kde, or xfce, or iceWM ... or even nothing at all.

here is some good information on how to install and configure your lamp server:
feisty: [http://easylinux.info/wiki/Ubuntu:Feisty#Servers](http://easylinux.info/wiki/Ubuntu:Feisty#Servers)

upon installing your lamp server, it is configured and ready to host connections on port 80.

you can upload html into the /var/www/ and it will display on [http://localhost](http://localhost)

---

