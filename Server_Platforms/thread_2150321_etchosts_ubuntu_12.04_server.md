---
title: "/etc/hosts ubuntu 12.04 server"
date: 2013-05-31
forum: Server Platforms
---

### Post by lepidas on 2013-05-31
I have 3 websites under Ubuntu 12.04 dedicated server
website1.com
website2.com
website3.com

what the /etc/hosts file should be?

---

### Post by DaveyG on 2013-06-01
Hi lepidas, you would need to set up a DNS server to handle all of the domains records. Have a loot at [this thread]("http://ubuntuforums.org/showthread.php?t=236093"), you'd need to also set up the hosts in web server too. I'm gussing you're using Apache? Have a look at [this page in the Apache Docs]("http://httpd.apache.org/docs/2.2/vhosts/")

---

### Post by Cheesemill on 2013-06-01
What are you trying to achieve?

The hosts file does the same thing as on any other machine, it performs basic DNS resolution for the local machine.

---

### Post by SeijiSensei on 2013-06-01
The /etc/hosts file doesn't matter on the server.  It is used to supplement DNS queries on the client.  However adding the virtual web hosts to the server's /etc/hosts may help avoid problems when the server starts and cannot determine its name.

---

