---
title: "A remote MySQL Host"
date: 2007-10-17
forum: Server Platforms
---

### Post by Dr Small on 2007-10-17
I want to be able to use my MySQL Databases across my network (and possibly later, on one of my websites on the internet without MySQL), and use it as a "remote host", and not just local.

I have been searching the web, but can not find any good information on how to accomplish this.

I am running Xampp (ApacheFriends.org), it has MySQL, it works on localhost, and I just basically want to be able to use MySQL on another local machine, or over the internet later.

Any suggested reading, or examples on how to do this ?
Thanks.

Dr Small

---

### Post by foxylad on 2007-10-17
See [http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html](http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html)

Basically you need to set up the server to listen on a given port and allow access through your firewall for that port.

---

