---
title: "Ubuntu 15.10 won't boot on NUC5PPYH"
date: 2015-11-01
forum: Server Platforms
---

### Post by kayp8217 on 2015-11-01
Hi everyone, recently I bought NUC5PPYH to play around with.  I tried to install Ubuntu 15.10 on it but the installer never loads completely.  After couple progress movements it just stops.

So I installed Ubuntu 15.10 server on the NUC successfully.  However on the very first boot since installation the machine won't boot completely.  It hags after these messages

> Started Apply Kernel Variables
Started udev coldplug all devices
Mounted POSIX message queue File System
Mounted Debug file system
...
Started udev Kernel Device Manager
...
Started Remount Root and Kernel File Systems
Starting Flush Journal to Persistent Storage...
Reached target Local File System (Pre).
Starting ensure /etc/mtab is a symlink to /proc/mounts...
Starting Load/Save Random Seed...
Started Flush Journal to Persistent Storage.
Started ensure /etc/mtab is a symlink to /proc/mounts.


And then nothing happens.  It just stops there.

I tried to search for problems with nuc5ppyh and ubuntu (or Linux in general) and there are very few matches.  I tried searching for the message "Starting Flush Journal to Persistent Storage AND ubuntu" and all references seemed to be about systemd.

At this point I am not sure if this because of a configuration problem, os problem or hardware problem.

I tried installing Ubuntu 14.04 desktop as well as server on the nuc but it won't boot either - for a different reason.  The installer, upon startup, would give error message like "linux image not found" or something similar.  I don't remember exactly sorry.

I must say that I was able to get Win 10 installed and up and running on this nuc just fine.

I would appreciate any help.  Thanks in advance.

Here are the specs: [http://www.intel.com/content/www/us/en/nuc/nuc-kit-nuc5ppyh.html](http://www.intel.com/content/www/us/en/nuc/nuc-kit-nuc5ppyh.html)

- Intel Pentium N3700 (2.4 GHz Quad Core, 6W TDP)
- 4gb RAM - DDR3L SODIMM
- 320 gb HDD
etc

---

### Post by lisati on 2015-11-01
Please do not start multiple threads for the same problem, it dilutes the community's ability to help.

Duplicate of [http://ubuntuforums.org/showthread.php?t=2301348](http://ubuntuforums.org/showthread.php?t=2301348) closed.

---

