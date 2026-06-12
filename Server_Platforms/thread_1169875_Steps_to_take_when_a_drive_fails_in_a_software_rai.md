---
title: "Steps to take when a drive fails in a software raid array"
date: 2009-05-25
forum: Server Platforms
---

### Post by crmccreary on 2009-05-25
I have the following setup:
Ubuntu server 8.04 (Hardy)
md0 - Raid 1, ext3, mounted on /, sda1 + sdb1
md1 - Raid 1, swap, sda2 + sdb2
md2 - Raid 5, ext3, mounted on /home, sdc1 + sdd1 + sde1 with sdf1 as spare
All drives scsi

I had installed a similar setup (no spare on md2) a few days ago and then moved the box into a rack. Upon booting up, the scsi controller stalled while checking one of the drives comprising md2 and would not go any further. Oh well, pull offending drive and replace with a spare. 

Upon boot up, md2 of course won't mount and I am offered a choice of dropping into a shell or continuing. Rather than learning what to do, I re-installed and I'm all set (for now). Since drives from the same lot/make/etc. tend to fail in clusters, I would like to be prepared.

I would like to know what steps to take when a drive fails in the raid1 array and in the raid5 array (short of buying a box with a good raid controller and hot-swap drives). I have been googling quite a bit and I have not found a resource with the requisite steps all in one place. I went through the O'Reilly linux raid book which was very informative about setup but had very little on recovery. I don't intend to use raid as a substitute for backup, I just want the redundancy for system recovery.

Suggestions? Pointers to resources?

<update>
I may have answered my own question:
[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

---

