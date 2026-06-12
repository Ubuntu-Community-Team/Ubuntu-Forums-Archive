---
title: "Server question"
date: 2008-08-02
forum: Server Platforms
---

### Post by fedex1993 on 2008-08-02
Okay i have an old dell sitting next to me that has been used for a server in the past. My question is the wall plug that comes into my room the ethernet cord can i plug that into the back of the comp and then have another networkcard that carryies on the ethernet line, but while its going threw the server can i have the server monitor the inbound and outbount connections? and also have a working webserver and file server?

---

### Post by jimv on 2008-08-03
Yes.  Put a second NIC in it, and you can set it up to act as a router for your other machines.  Then you'd install Apache for the webserver, and set up SAMBA shares for the file server part.

About the network monitoring...was there something in particular you wanted to watch for?

---

### Post by Sef on 2008-08-03
Moved to server platforms.

---

### Post by cariboo on 2008-08-03
Have a look here:

[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

You should find something useful.

Jim

---

