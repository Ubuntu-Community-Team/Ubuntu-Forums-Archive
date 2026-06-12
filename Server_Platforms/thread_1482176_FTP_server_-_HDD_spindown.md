---
title: "FTP server - HDD spindown"
date: 2010-05-13
forum: Server Platforms
---

### Post by freeangel on 2010-05-13
Hi *,
 
 
I have a FTP server (normal computer with ubuntu setup acting as ftp server).
btw-there is raid 0 and raid1 in some combination.
However the disks are pretty loud so I want to spin them down until some ftp connection arrives. then they should wake up and work like needed. after disconnecting they should spindown again.
I care only about the disks (not the whole system) as the machine is near (inside my living room) :(
 
One thing to mention is that I know one way how to spindown the disk:
hdparm -S <xxx> /dev/sda  
the problem is that is starts IMMEDIATELY again (looks like some system process access the disk all the time but I have nothing running). How to check that and is the hdparm the right way?
 
gurus and all other who knows more, please help:)  is there any possibility to arrrange this ? (some setting or even with some software).
any help really appreciated.
 
 
thanks a lot
free

---

