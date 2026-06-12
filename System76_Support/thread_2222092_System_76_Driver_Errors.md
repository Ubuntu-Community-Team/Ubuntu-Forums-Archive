---
title: "System 76 Driver Errors"
date: 2014-05-05
forum: System76 Support
---

### Post by blanik on 2014-05-05
I reinstalled Ubuntu 14.04 on my Galago Ultrapro today in order to customise the partitioning schema.  After installation, I added the PPA for the System7 Drivers, and then installed the System76 Drivers.

When I click on the System76 Drivers icon in System Settings, I get the Password Authentication Dialog Box, and after entering the password, nothing further appears to happen - except that the dialog box disappears.  

A check of dmesg shows that the following error is occurring:

[13786.934815] system76-driver[17833]: segfault at 0 ip 00007fb0f0154657 sp 00007ffff7cc4738 error 4 in libgtk-3.so.0.1000.8[7fb0f003f000+4ff000]

The only configuration change on this Ubuntu install that is potentially non-standard is that the / and /home partitions are both btrfs.  Otherwise, it is a vanila install of Ubuntu 14.04.

Any ideas what's going on, or how to fix this error?

Thanks,

Roy

---

