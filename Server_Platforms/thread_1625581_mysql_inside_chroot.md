---
title: "mysql inside chroot"
date: 2010-11-19
forum: Server Platforms
---

### Post by qlimax on 2010-11-19
Hello.

My problem is the following:

I would like to configure mysql server in a chrooted environment.
I've created the chrooted enviroment with schroot

On the **host** machine I have a mysql-server instance running on **3306** port

On the **guest** machine I would like to have another instance(completely separated) of mysql on the **3307** port

I've successfully installed mysq-lserver on the guest machine and configured my.cnf with the 3307 port. 
However when I start the mysql service with /etc/init.d/mysql start  into the chrooted environment, the mysqld service comes up on the 3306 port... 

It seems that I'm acting on the host mysql service and not on the guest one... :(


The same procedure works with apache, but not with mysql... don't know why.


Thanks for your support

---

### Post by HermanAB on 2010-11-19
Howdy,

Please note that chroot is a late 20th century concept that is mostly a waste of time.  It doesn't really provide any extra security (since it is easy to subvert) and instead provides a huge maintenance problem (as you have now found).

Soooo...., uhmmm..., good luck with that...

---

### Post by qlimax on 2010-11-19
My use case of chroot is not a lot about security.

The problem is that on the same server machine, I have many virtualhosts on apache and many databases on mysql.


I'm now facing with an "experimental" project on the same machine.
However, this project requires to install several apache_mods and make a lots of qps on the db.

For this reason I want to keep things separate.

Have you any others ideas on how to acheive my objective?


Maybe run multiple instances of mysql-server on different ports And multiple apache instances as well on different ports? 

Thank you for answering.

Ps: Old thigs are sometimes better than new ones ;)

---

