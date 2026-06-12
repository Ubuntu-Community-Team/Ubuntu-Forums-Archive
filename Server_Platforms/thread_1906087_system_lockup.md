---
title: "system lockup"
date: 2012-01-08
forum: Server Platforms
---

### Post by speed32219 on 2012-01-08
Maverick 10.10, I have a 4 GB root partition and I use about 2.3 GB.  I attached a 4 TB (2 2TB) external USB storage device to test for a backup solution using rsync.  The new device was generating multiple errors and the errors were being written to the syslog and dmesg logs as they should.

But, it filled the logs (df -h showed no space left on root), hence the system would not boot. I went into the logs and there were many syslog/dmesg that ended in gz, compressed)  syslog1/dmesg1.gz, syslog2/dmesg2.gz, etc. until no more space.

Are these logs suppose to be removed after a reboot?  Does a script need to be applied to clean the old logs?

---

### Post by arrrghhh on 2012-01-08
No, the logs do not get removed automatically, ever, as far as I know.  Typically compressed text files don't take up much space, and sysadmins can go thru and clean them up if it really gets bad.

I'd say you have some rm'ing to do.

Also, just strikes me odd that you're on 10.10.  Most server admins run on LTS releases, that way you only have to upgrade every 2 years.  You should really look at getting off that platform ASAP, because you're either a) in for a fresh install or b) lots of upgrades.

---

### Post by kevinthecomputerguy on 2012-01-08
I'm not sure how to do it command line, but if you have Webmin installed you can click on "Log File Rotation" and bump up the level at which they are overwritten.

Arrrghhh brings up a good point, and my suggestion above is only masking a bigger problem. But i too run really small root partitions, and do benefit from a tighter log file rotation.

*note, i do read every one of them, if your not that dedicated, don't change it :- )

-Kev

---

