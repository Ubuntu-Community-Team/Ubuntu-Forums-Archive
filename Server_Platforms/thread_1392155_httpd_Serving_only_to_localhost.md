---
title: "httpd Serving only to localhost"
date: 2010-01-27
forum: Server Platforms
---

### Post by iXombie on 2010-01-27
For whatever reason I can only view a locally served web page through the Lynx browser on the system, but I can't bring up the page on another computer that is on the same network. Any input on how to make the page serve to the rest of the network?

---

### Post by jbruced on 2010-01-27
Can you ping the server from the other on-network PC?

Got firewall settings set?

I used fire starter to firewall my PC, then installed a lamp server.

I needed to change rules to allow port 80 to be open so my other local netwok PCs could find the server.

Just some random thoughts on it.

GL Bruce

---

### Post by iXombie on 2010-01-27
Thanks for the quick reply

I am running the box headless and working through SSH. I can ping the machine. It is a very fresh ultra-light install running only IPtables for a firewall. IPtables is currently accepting all incoming connections.

---

### Post by Iowan on 2010-01-28
[Here]("https://help.ubuntu.com/community/ApacheMySQLPHP#Securing%20Apache") is a LAMP help page - perhaps use the information in reverse:> Change ports.conf so that it contains:
Listen 127.0.0.1:80 Instead, change the line to match your server IP address.

---

