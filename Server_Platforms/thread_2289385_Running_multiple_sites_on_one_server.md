---
title: "Running multiple sites on one server"
date: 2015-08-03
forum: Server Platforms
---

### Post by koozoop on 2015-08-03
Hello. I'm trying to figure out if there is a way to host multiple sites on one pc running ubuntu server 14.04.2 but allowing ssl only to one of them eg. I want to host an owncloud installation with ssl and two sites without ssl. Is that possible?

Thank u in advance!

---

### Post by Lars Noodén on 2015-08-03
Yes, if you are using Apache2, set up multiple virtual hosts (vhosts) and apply SSL to only one of them.  

[https://help.ubuntu.com/lts/serverguide/httpd.html](https://help.ubuntu.com/lts/serverguide/httpd.html)
[https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts)
[http://httpd.apache.org/docs/2.4/vhosts/](http://httpd.apache.org/docs/2.4/vhosts/)

---

### Post by koozoop on 2015-08-03
But isn't SSL on one apache instance applied globally, ie if for example I have an SSL for say, owncloud this will be applied for the other sites as well, right?

---

### Post by Lars Noodén on 2015-08-03
It's applied (or not) for each individual virtual host.

---

### Post by koozoop on 2015-08-03
Thank you. I will give it a try on a virtual machine.

---

### Post by Lars Noodén on 2015-08-03
A virtual machine would be different and inefficient.  Try the links above for virtual hosts.  A virtual host is where one machine is running multiple sites from a single installation of the web server.

---

