---
title: "Wamp server"
date: 2014-02-05
forum: Server Platforms
---

### Post by kewal on 2014-02-05
can we use wamp server in ubuntu operating system for run php code

---

### Post by lisati on 2014-02-05
*Thread moved to **Server Platforms**.*

Welcome to the forum.

There is a server edition of Ubunu, sometimes referred to as a LAMP server rather than a WAMP server. WAMP is designed for Windows systems, and won't run on Ubuntu without help.

---

### Post by Lars Noodén on 2014-02-05
You can install the full LAMP stack easily:

```

sudo apt-get update
sudp apt-get install lamp-server^

```

Or you can pick the components individually using the Software Center or Synaptic.  

If the PHP code was written properly it should run on any system.  If not, you'll have to look under the hood to see how much work is needed to port it to a modern system.

---

### Post by fdrake on 2014-02-05
some intalllation guides:
lamp :[https://www.digitalocean.com/community/articles/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu](https://www.digitalocean.com/community/articles/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu)
server setup: [https://www.digitalocean.com/community/articles/initial-server-setup-with-ubuntu-12-04](https://www.digitalocean.com/community/articles/initial-server-setup-with-ubuntu-12-04)
phpMyAdmin: [https://www.digitalocean.com/community/articles/how-to-install-and-secure-phpmyadmin-on-ubuntu-12-04](https://www.digitalocean.com/community/articles/how-to-install-and-secure-phpmyadmin-on-ubuntu-12-04)

---

