---
title: "Ubuntu Server Lampp server"
date: 2012-08-28
forum: Server Platforms
---

### Post by magicofflight on 2012-08-28
I have an amazon ec2 small instance in which I have added ubuntu server. I have installed and almost configured lamp on the server. Now I am trying to move my [personal blog]("http://www.george.ind.in")(Not much traffic) to this ec2 instance. Has anybody done this before and what any links on securing the installation. Is it possible to install cpanel in this. I am anyways keeping backup just in case.

---

### Post by thnewguy on 2012-08-28
I have done migrations before and usually, so long as you can get the database transfered cleanly, everything falls into place. Depending on which blogging software you are using you may have to transfer your host name/URL too in order for your blog's links to work.

Regarding cPanel I think that only officially works on Red Hat and CentOS. I'm not aware of any Ubuntu ports of the cPanel, but check their website to confirm.

---

### Post by d4m1r on 2012-08-28
No, it is not possible to run CPanel on Ubuntu.

---

