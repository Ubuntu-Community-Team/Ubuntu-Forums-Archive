---
title: "Error mounting partitions on second hard disk after Xen installation"
date: 2007-04-11
forum: Server Platforms
---

### Post by voipfc on 2007-04-11
After installing Xen 3.0.3 on a Ubuntu 6.06 system trying to mount partitions on the second hard disk fails.

> [admin@server ~] mount /dev/sdb1 /backup1
mount: /dev/sdb1 already mounted or /backup1 busy

When I reboot with the non Xen kernel everything is fine.

After googling around it seems that some lvm or dm issues may be the cause.


Is there some way to diagnose it further? Are some kernel modules or daemons that are known to cause this type of problem?

After checking the howto I used at [http://www.howtoforge.com/forums/showthread.php?t=5229](http://www.howtoforge.com/forums/showthread.php?t=5229) it appears that the issue is related to some kernel module called EVMS.
How is EVMS disabled?

---

### Post by voipfc on 2007-04-12
No help?

---

