---
title: "New Kernel from 10.10 Upgrade Freezes xfs"
date: 2010-10-17
forum: Server Platforms
---

### Post by rickatnight11 on 2010-10-17
I recently upgraded my server running *10.04-server* to *10.10-server*.  Along with that upgrade I moved from the **2.6.32-24-server** kernel to **2.6.35-22-server**.  Now my xfs partition across my RAID-5 array locks the system up when trying to mount it.

It took a while of trial and error to weed it down to the kernel, but I commented out the xfs partition from fstab to troubleshoot.  I finally figured out that when I load up Ubuntu with the older kernel, I can mount xfs immediately.  With the newer kernel the system locks up, but in a strange way.  The system won't respond to keyboard input, but the services running on the server still work.  My webserver still runs, and I can establish new SSH sessions, but upon logging in there is no keyboard response.

Is there a known issue between **2.6.35-22-server** and xfs, or is there some way that I can troubleshoot this?

Here's the configuration of my array:

_/dev/md0_ (RAID-0)
1.) sdb1 (1TB)
2.) sdc1 (1TB)

_/dev/md1_ (RAID-5)
1.) /dev/md0 (2 x 1TB)
2.) /dev/sdd1 (2TB)
3.) /dev/sde1 (2TB)
4.) /dev/sdf1 (2TB)

---

