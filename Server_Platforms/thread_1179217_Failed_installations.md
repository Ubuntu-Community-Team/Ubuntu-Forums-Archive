---
title: "Failed installations"
date: 2009-06-05
forum: Server Platforms
---

### Post by RayLab on 2009-06-05
I have a Gateway 960 Server PC that I would like to load Ubuntu on...

However Ubuntu Server only support x86 processors, this box has dual Xeon processors.  Tried the Ubuntu Server 9.04 install anyhow and sure enough, it failed.

Ubuntu 9.04 desktop also failed.  During the reboot after a full stand-alone install it fails with a message stating that a device file or loader is missing: 

      /dev/disk/by-uuid/03e69766-de00-446f-925c-7241841d493c

Any thohghts?  Am I trying to install Ubuntu on an incompatible box?

BTW: the 'Trial' mode on the install CD worked, I was able to run some apps, browse, etc.

Thanks,
Ray L.

---

### Post by Triden on 2009-06-05
Does your box have SCSI drives in it? 

 If so, I recently came across a similar error where the system was booting faster than the SCSI drives could spin up and be recognized.  The error message I got was that the root file system could not be found.  I had to add a boot command of rootdelay=45 to fix it.

---

