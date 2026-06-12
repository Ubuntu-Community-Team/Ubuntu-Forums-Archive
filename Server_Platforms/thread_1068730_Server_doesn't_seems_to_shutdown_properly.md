---
title: "Server doesn't seems to shutdown properly"
date: 2009-02-13
forum: Server Platforms
---

### Post by ibob on 2009-02-13
Hi guys,

I have a ubuntu server 8.10. Most things work really well however when I try to shut it down ( i.e using "shutdown now" ) it doesn't behave as normal.

It stops all the services ( mysql, nfs, rsync etc etc ) but then drops into a blue Recovery Menu. The options are:

 resume
 clean
 dpkg
 fsck
 root

However, it would be really great if the machine switched off at this point.

It is a completely standard installation - however it has software raid on some data drives installed using mdadm.  I have checked the bios settings and APIC is working correctly.

Any thoughts or ideas to try would be gratefully received,
Thanks,

James

---

### Post by cdenley on 2009-02-13
```

man shutdown

```

```

shutdown -h now

```

---

### Post by ibob on 2009-02-13
Ah... a rocky mistake! I really should read the manual.
Thanks for your help,

James

---

