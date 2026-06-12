---
title: "Ture Server Syncing"
date: 2009-08-29
forum: Server Platforms
---

### Post by agarza99 on 2009-08-29
Hi All, I been using Ubuntu for about a year now and have recently been looking to a true syncing solution.  I've tried rsync and unison and both have advantages and disadvantages but neither offers what I'm looking for.

I'm not sure if there is anything out there that does.

What im looking for is a syncing solution that will sync 2 file servers the moment someone saves a file. Sending only the bits that changed across to the other server.  Similar to the way dropbox works except using it in a private network.

[http://www.getdropbox.com]("http://www.getdropbox.com")

Another feature would be the ability to lock files that are in use... in order keep multiple people from editing the same file at the same time. 

I'm not sure if this is even possible but i thought I'd ask.  Any help would be greatly appreciated.

Thanks in advance

---

### Post by jay.parnaby on 2009-08-29
You could look at something like DRBD. I've not used it myself but there is a guide for making a "Highly Available NFS" server in the community documentation

[https://help.ubuntu.com/community/HighlyAvailableNFS]("https://help.ubuntu.com/community/HighlyAvailableNFS")

---

### Post by agarza99 on 2009-08-30
Do you know if this will work with remote servers.  We have 2 servers in different cities.

Thanks Again,
Albert

---

### Post by jay.parnaby on 2009-08-31
The feature list on the [DRBD Site]("http://www.drbd.org/home/feature-list/") says that an off-site node can be added for disaster recovery so it is possible, though you may need to look at DRBD Proxy, which looks to be a commercial product.

---

