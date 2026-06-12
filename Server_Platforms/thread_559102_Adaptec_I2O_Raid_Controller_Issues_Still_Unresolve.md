---
title: "Adaptec I2O Raid Controller Issues Still Unresolved?"
date: 2007-09-24
forum: Server Platforms
---

### Post by hellomoto43 on 2007-09-24
I have searched these forums and elsewhere and found this "known issue" with Ubuntu.  Why hasn't this been resolved?

The issue is that after seeing the Adaptec I2O RAID device on installation, the installer does not properly set up the config and/or load up the right modules correctly to complete the install.  As a result the system hangs upon the first reboot with errors saying it cannot find the I2O device.

I have recently downloaded the latest versions of 6.06 and 7.04 Server and run into the same issue.  I have tried the suggestions of booting into a Live CD and editing the grub config and /etc/fstab files to no avail.

I was hoping someone out there has new information as to whether there is a fix in the works.

---

