---
title: "Wordpress crashes networking!"
date: 2012-09-26
forum: Server Platforms
---

### Post by mcc28x on 2012-09-26
Hi,

I have installed WordPress in /var/www on Ubuntu 12.04. My hostname is thaddeus.

I can browse to thaddeus/wordpress and everything looks okay, however if I sign into Dashboard and then click onto 'Updates' for some reason networking on the server goes down.

So if I'm on my laptop and I do the above all I get is 'waiting for thaddeus' in firefox status bar and then after a few mins I get a page  'The connection to the server was reset while the page was loading'.

My ssh connection goes down as does samba connection.

I have to go to the physical server to reboot.

I have checked Apache's log but the GET request doesn't even seem to be recorded.

I have other sites on the same server that work fine such as Joomla/Gallery/Ossec.

I'm not even sure how to troubleshoot this let alone solve it...can anyone help?

---

