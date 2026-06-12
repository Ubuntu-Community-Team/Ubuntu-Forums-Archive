---
title: "Suggestions for ideal LVM setup"
date: 2010-04-03
forum: Server Platforms
---

### Post by nerr on 2010-04-03
Hey everyone, I'd like to set up LVM on my Ubuntu 9.10 server, and am looking for ways to optimize the setup for future growth and mass-storage.  Currently I am running the following setup:

1TB HDD (32MB cache): 20 GB /, 1GB /boot, 20GB /home, 8GB swap, remaining goes to /srv
1TB HDD (8MB cache): backup drive (images /, /boot, /home, and rsync on /srv twice a week)
640GB HDD (16MB cache): rtorrent drive (dedicated entirely to downloading/seeding)

Overall, all three drives are nearing approximately 80% of their maximum capacity, hence why the time has come to upgrade the array.  I will likely be purchasing a Sans Digital TR4M-B eSATA enclosure to add four extra drive bays to my server (Acer easyStore H340), in addition to the four built-in bays.

I plan on buying a 2TB HDD soon, most likely the Western Digital WD20EADS.  Here is my current proposed setup for LVM.

Non-LVM:
640GB HDD: 16GB /, 1GB /boot, 8GB /home, 4GB swap, remaining for rtorrent

LVM:
Volume Group "data" (mount on /srv): 1TB HDD + 1TB HDD + additional disks (ext4)
Volume Group "backup" (mount on /mnt/backup): 2TB HDD + additional disks as "data" grows (ext4)

I assume it would be wise to at least keep the operating system outside of LVM, but I am torn on whether or not to add rtorrent, as I suspect it may be a good idea to keep torrenting activity to its own drive (or the same drive as the OS, which also constantly runs).

Is my plan for LVM a viable and well-thought-out system to put in place?  If not, how could I improve it?  Thanks for your thoughts, and sorry for the lengthy post.

---

### Post by KB1JWQ on 2010-04-03
Do you care about your data? If so, you may want to consider some form of RAID.

---

### Post by nerr on 2010-04-03
I do have a regular backup scheme implemented and an external hard drive which makes a copy of the backup files.  In addition, I'm running all Western Digital Caviar Green drives, which I've heard can be a nightmare under RAID scenarios due to variable RPM rates and power-saving features.  I would prefer to avoid RAID unless the aforementioned statement can be completely debunked.

---

### Post by iissmart on 2010-04-04
I'd put rtorrent on "data" so it's out of the way of the OS drive. Ignore the extra space on the OS drive or if it really bothers you just get a smaller SSD for your OS so you don't have the space to worry about :p

Also, I would suggest XFS instead of ext4 for your LVMs, see here for how to optimize XFS for *speed*: [http://everything2.com/index.pl?node_id=1479435](http://everything2.com/index.pl?node_id=1479435)

---

### Post by nerr on 2010-04-05
I suppose buying some sort of small flash device for the OS isn't out of the question, especially since I'd prefer not to waste a hard drive which could be used for massive data storage.  I'll have to look into that option, or if all else fails, just find ways to put files that are mostly static on the OS drive. (such as system images from network machines which are made once a week)

I actually run XFS on my /srv partition right now and have been impressed with its performance, but I fear that because there is no way to shrink an XFS filesystem, I'll end up getting screwed over later if I really want/need to shrink a volume to grow another.  That's my only worry.

---

### Post by Niels_Andersen on 2011-01-18
Hello
I have another thought on this. My setup is like this (at the moment):
320gb sda
1tb sdb
1tb sdc
2tb sde

320gb sda:
250mb /boot, 1gb /swap, 8gb /root, 100gb /home, rest lvm (all except /boot is ext4)
sdb, sdc, sde is ext4 lvm.
This setup is my third or fourth try, still learning Linux/ubuntu ;), and i'm using Turnkey fileserver as my installmedia (basic ssh, webmin and other tools)
On one of my first tryouts i had 70-90mbps transfers over my lan, but with this setup i have only 30-50mbps transfers.
My guess is that the difference is that the fist install was a "total" lvm (all drives at the same volumegroup(VG), and the /boot /swap /root /home and data was logicalvolumes(LV) )

I know that this is not at all in lead of the original question, but could i be right on this assumption ?

---

