---
title: "ProFTPd won't list"
date: 2010-05-25
forum: Server Platforms
---

### Post by knewmocker on 2010-05-25
Hi, I have set up proftpd many times now one Ubuntu 9.10 and never ran into any problems. I decided to go ahead and do a clean install of the new 10.04 and set everything back up (ie ssh ftp apache... ect)

I got done with ssh with no problems and started working on getting proftpd up and running just like I've always have. But now every time I try to login it gets to where it should list all the files in my dir and it just times out. If I connect through my network (192.168.1.101) everything works fine so I dont think its my .conf file.

All ports are open that are needed and I even tried opening up the passive ports to see if that would help but it does not. I have no firewalls running on my machine and I am just out of ideas. Thanks

---

### Post by knewmocker on 2010-05-26
Ok, I went through a whole lot with the passive ports and it turned out that they were being used by my UPnP on my router for other ip address on my network. Im not exactly sure why this was never a problem untill now.

So basicly I just turned off my UPnP and turned it back on to clear the list and now I can connect just fine now. Hope this helps anyone else out with the same problem as me.

---

