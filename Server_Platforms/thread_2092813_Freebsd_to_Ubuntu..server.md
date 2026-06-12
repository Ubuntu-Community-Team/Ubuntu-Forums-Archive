---
title: "Freebsd to Ubuntu..server"
date: 2012-12-08
forum: Server Platforms
---

### Post by hawaiiman on 2012-12-08
Looking for some advice as to how to remove Freebsd from an IBM server so I can replace it with Ubuntu server 10.04 LTS. Machine is running RAID (5?) currently with 2 HDD and space for more. The IBM was replaced by an Ubuntu server machine when our ISP was changed and we lost our static IP. Obviously we don't have a qualified SA, and in our remote location the chances of either getting one, or hiring one as a temp are next to 0.

---

### Post by newbie-user on 2012-12-10
You could just install Ubuntu and wipe FreeBSD in the process. I'm not exactly sure what you are asking.

---

### Post by tgalati4 on 2012-12-10
Freebsd probably uses the ZFS file system which can't be read by Ubuntu, so proceed carefully.  You will need some way to back up all of your data to an ext4 filesystem before taking down the freebsd server.  Perhaps a large USB drive that is formatted to ext4 and do a large data dump to it.  Once you have verified that your data is secure, then you can wipe the disks and install Ubuntu server.  Then attach the backup drive and repopulate your data and start your services and verify that everything is working.  It's a lot of work.

It's not clear from your post if this is a spare machine.  If all of your services have already been migrated and this machine is just collecting dust, then a simple wipe of the drives using parted or fdisk and check the drives using badblocks should be all you need to get a clean start.

RAID5 normally requires 3 drives, so it's possible that you are running RAID1 with a simple mirrored drive setup.

---

### Post by hawaiiman on 2012-12-10
Yes, this server became obsolete when the isp was changed and static ip was lost. I realize that it could have been re-configured in more or less the same manner with which Ubuntu 10.04 server was set up. I had already started building the other machine (current server) from a spare windows machine. 
I have a 3rd drive for the ibm which isn't mounted.
There isn't any useful data on the old server I assume, as since I have defacto assumed control of the department there has been no desire expressed to recover anything from it. I may ask about that.
Yes, I want to set up the ibm with a clean install of ubuntu 10.04, and run raid. Right now the Samba share is ready to start functioning as a backup for data on individual machines (which also lack backuo btw). Right now, the samba share and how to use it is just being implemented. I have time, just planning ahead.
I'm only supposed to be teaching 6 one hour classes a week, so all this network activity is on my free time, so slowly slowly is ok.
BTW the current server has only one hdd and this week's project is installing a second drive and getting auto backup going on it.

---

