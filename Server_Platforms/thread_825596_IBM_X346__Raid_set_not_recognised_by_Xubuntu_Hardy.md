---
title: "IBM X346 : Raid set not recognised by Xubuntu Hardy."
date: 2008-06-11
forum: Server Platforms
---

### Post by Knightwise on 2008-06-11
Hey Guyz,

I was looking to run Ubuntu Hardy server (or XUBUNTU) on our IBM X346. It is running with 2 hard drives in RAID-1 (mirror) using the Adaptec HOSTRAID function. But when I install the server it sees 2 separate hard drives instead of the "One virtual " hard drive ( the two physical drives in mirror) it sees 2 physical drives. This probably means that the raid controller is not recognized by Ubuntu. Is their any fix to this ? I would like to use the server and have Mirrored drives.

---

### Post by Knightwise on 2008-06-18
OK , I found a way to solve my problem , 

thanx to Popey from #ubuntu-Uk on freenode (be sure to check out his website and great video tutorials too) 

Here is the video on how to do it : [http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2](http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2)

Here is some more info on how to setup raid on fedora
[http://www.texsoft.it/index.php?c=hardware&m=hw.storage.grubraid1&l=it](http://www.texsoft.it/index.php?c=hardware&m=hw.storage.grubraid1&l=it)

and the great manual on how to do it in Ubuntu
[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

So with all this i managed to get raid 1 working on my ibm server.

---

