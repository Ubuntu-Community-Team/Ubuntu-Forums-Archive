---
title: "Updated Ubuntu Server and not its not booting"
date: 2018-04-18
forum: Server Platforms
---

### Post by satish8 on 2018-04-18
[COLOR=#000000]I updated the server which was running ubuntu 12.10. However, now I am unable to start the server keeps throwing error select boot media and press any other key. This machine as configured on RAID 1 TB + 1 TB = 2 TB. [/COLOR]

[COLOR=#000000]Below is the boot repair log that boot-repair tool provides.[/COLOR]

[http://paste.ubuntu.com/p/9HYphj2KWb/](http://paste.ubuntu.com/p/9HYphj2KWb/)

---

### Post by TheFu on 2018-04-19
12.10 support ended over a year ago, so no updates have happened in over a year. I'd be surprised if the machine wasn't totally pwned by this point.  Move to 16.04 or wait a few weeks and move to 18.04.

BTW, using RAID0 on spinning disks is very dangerous.

---

### Post by satish8 on 2018-04-19
I agree that the machine still made it so far. However, this machine was setup a very long time ago and unattended due to application running on it. However, is there a way I can get it booted and recover the data and then move on with upgrade. Will that be possible. Appreciate your help.

---

### Post by TheFu on 2018-04-20
Boot from a live-install (flash or CD or DVD) and backup any settings and data, a clone of partitions would be smart in addition, then wipe the system, load the base OS, restore the application settings and data, then load the programs - updated versions would be recommended since libc has changed since 2012.

---

