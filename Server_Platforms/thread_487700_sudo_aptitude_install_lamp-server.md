---
title: "sudo aptitude install lamp-server"
date: 2007-06-29
forum: Server Platforms
---

### Post by smartduck on 2007-06-29
this command or sudo apt-get install lamp-server should install a LAMP on my KUBUNTU.
But it tells me that this lamp-server package does not exist.
Please help me!
Thanks!
smartduck

---

### Post by az on 2007-06-29
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

That will install the LAMP stack.

You may also run

sudo tasksel 
and pick LAMP.

---

