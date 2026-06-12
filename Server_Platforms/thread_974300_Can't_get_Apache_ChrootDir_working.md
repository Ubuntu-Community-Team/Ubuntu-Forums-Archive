---
title: "Can't get Apache ChrootDir working"
date: 2008-11-07
forum: Server Platforms
---

### Post by WhiteShepherd on 2008-11-07
I'm running Ubuntu Server 8.04LTS.  I installed libapache2-mod-chroot  and added 
ChrootDir "/wwwpages" 
to my httpd.conf .   The problem is every time I add this line the server stops accepting connections: "Failed to Connect".  The ChrootDir does not give any errors and Apache accepts it.  However if I change Document root: /wwwpages to / it gives me a path error.

What am I missing and can someone tell me how to get this up and running?

  Thanks!

---

