---
title: "Disk raids"
date: 2005-12-21
forum: Server Platforms
---

### Post by svargas on 2005-12-21
First what a great forum....

My first question is setup raid 1+ or raid 5 using Ubuntu, I would like to use mdadm to setup a raid of disks for data purposes, without installing Ubuntu to another harddrive for the OS and use the liveCD. The problem is writing the config files needed to run the raid. How to config the liveCD to write to a USB drive or copy the LiveCD to a USB drive so that config file could be created.
This is a poor man disk array for storing MP3.

Thanks

---

### Post by poptones on 2005-12-21
mdadm puts the config info in the drives themselves. If you use mdadm to create a raid5 each partition making up that raid will have information on how it is used. When I (re)install ubuntu it automatically finds my raids right off the bat.

But why don't you want to put the OS on a drive? It's just 2gb, so in a raid5 with three partitions you'd lose all of 6gb. You can use one of those for /home and the other to experiement with other installations (that's sorta what I do, anyway).

---

### Post by svargas on 2005-12-22
Based on my reading if you use mdadm you should create a file /etc/mdadm.conf for keeping track of the raids like raidtools  you need to created /etc/raidtab.conf file. I would like to keep the OS separate from the data. This base on some booting issue with raid 5. Also the server will not have a monitor and keyboard once it is config and setup on the network. I guess I could purchase a little 10 gig drive for the OS and run it from the motherboard, I was just trying to use the liveCD.

---

### Post by arx-lupus on 2005-12-22
I was thinking of a similar thing for a fileserver setup - I didn't want to have OS and data affected by a failure and didn't really want to buy any extra hardware. 

I was thinking of making an install on some removeable media, CF on a CF IDE adapter (use this method for our ipcop firewall) and then use NFS on another server to store changing info to limit writes to CF. Or making a CD Image of filesystem and mounting changeable files on CF or even floppy if it came to it.

Got to be honest, in a brainstorming phase right now so none have this has been thought through to any level of detail. 

Any info on this type of setup would be great.

---

