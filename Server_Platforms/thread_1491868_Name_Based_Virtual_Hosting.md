---
title: "Name Based Virtual Hosting"
date: 2010-05-24
forum: Server Platforms
---

### Post by Doulos1 on 2010-05-24
LAN IP loads default page, but "localhost" says > Not Found
The requested URL / was not found on this server.

---

### Post by macmike on 2010-05-26
I have the same problem.

---

### Post by Iowan on 2010-05-26
[Here]("http://httpd.apache.org/docs/2.0/vhosts/name-based.html") is an article I bookmarked awhile back...

---

### Post by Doulos1 on 2010-05-26
Thank you for the reply, Iowan.  I have read what you suggested and it does not address why using "http://localhost" does not work anymore.  I have the named based virtual server running fine.  All the domains go to the appropriate virtual host on my server.  Connecting to the server from inside the network using 192.68.1.2, or from outside using my actual IP address brings up the default site, but using localhost, or 127.0.0.1 for the server box itself returns "Not Found.  The requested URL / was not found on this server."

This does not seem to cause a problem since all the sites on that box are working fine from both inside and outside the network.  I am just curious if I did something wrong or if what is happening is normal.  This is my first attempt at a self-managed virtual machine so I have nothing to compare it to.

Thanks again for your replies.

---

