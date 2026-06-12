---
title: "Root Access Worked When Accessing Ubuntu on a Different Hard Drive Partition"
date: 2013-06-10
forum: Security
---

### Post by mouse- on 2013-06-10
This may be one of the most ridiculous questions asked, but here's what happend:
So I, because I sometimes have too much free time, have 3 partitions on my hard drive, each with it's own operating system.  One is Windows, one is Ubuntu 12.10, and one is an older release of Ubuntu, for messing around and quite often breaking things.  So I was booted into the older release of Ubuntu and logged in as root and wanted to see if I could edit a configuration file for Ubuntu 12.10 which requires root access.  I could.  I then rebooted into 12.10 and tried to access the same file in the older release of Ubuntu, which also worked.  The passwords for both root accounts are the same.  Can someone explain to me why this worked, and if this indicates a security vulnerability I should be aware of?  I have been trying to figure it out and my head keeps running in circles, so any help would be appreciated.

---

### Post by deadflowr on 2013-06-10
Because you're running as root, albeit through sudo.

root is the owner of the files, regardless of system.

---

### Post by mouse- on 2013-06-10
Thanks!

---

