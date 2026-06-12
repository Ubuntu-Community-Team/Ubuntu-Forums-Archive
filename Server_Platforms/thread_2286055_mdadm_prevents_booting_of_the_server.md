---
title: "mdadm prevents booting of the server"
date: 2015-07-09
forum: Server Platforms
---

### Post by rogerappl on 2015-07-09
I have a 14.04.1 server that suddenly started trying to bring up a software raid - this prevents booting as it never fails.  I have used the Live CD and looked at all the files (fstab, /dev/mapper, init.d) and cannot see any reason for it to even try to use the raid. (this did happen after an update kernel).  Is there some way to prevent the mdadm from loading?  

Since I cannot boot, I will most likely have to edit a file - I can mount the LVM OK and I have a multipath device (which mounts automatically without issues - only the internal device - the system disk - has issues) - This is a mirrored device (Raid 0+1).  I am using an HP Blade with an MSA device.  The machine has been running fine for the past 5 years.

---

