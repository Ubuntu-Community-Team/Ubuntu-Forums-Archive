---
title: "hot backup from root USB drive to another USB drive"
date: 2010-02-17
forum: Server Platforms
---

### Post by dehcbad25 on 2010-02-17
I have an Ubuntu server. This server I use it at work for file server and to host xymon network monitoring and a helpdesk system.
It does it job adecuately but I am trying to improve the file sharing so it is more transparent like windows 2003/2008 servers.
Because of this, quite often I end up braking the system and having to re-install everything, so I finally decided to setup a hot backup if possible but I can't find how to do it.
My setup is this
MS wind PC, this has an Atom 330 (dual core) cpu, 2 GB of RAM, and 2x1TB hard drive. The 2 drives are in a RAID thru mdam.
The OS, Ubuntu server 9.10 is installed in a 16 GB USB drive, which works pretty good (a little slow on Gnome, but works OK.
I have another USB drive (8GB), where I just installed ubuntu server LAMP packages (basic) so I can use it as the hot backup
I tried to use this solution
[http://programs.rcrnet.net/backup/](http://programs.rcrnet.net/backup/)
but I must be doing something wrong because after a backup both USB drive won't boot, and I need to recover the system from a image that I created recently using clonezilla.
I think most likely the problem is that I am also backing up files that I should not.
It is also possible that the problem is in the boot partition. since the RAID are actual SATA drives, they are usually /dev/sda and /dev/sdb while the usb is /dev/sdc
When I look in the disk utility I can see that both USB drives have a MBR, which they should, but maybe when I am running the utility is overwritting the MBR and thus corrupting my boot.
Suggestions?

---

### Post by dehcbad25 on 2010-03-04
Anyone knows of a way??

---

