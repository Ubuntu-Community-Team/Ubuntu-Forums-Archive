---
title: "Raid1 restoring problem"
date: 2010-07-15
forum: Server Platforms
---

### Post by unar84 on 2010-07-15
Hi all! 
I have  a strange problem with Raid1 I can't solve.

This is the situation:
- I have installed Ubuntu 10.04 server on a raid1 mirror of 4 disks, 1 TB each one
- The server is a new machine with new hardware
- I complete disks format and raid1 setup during installation process and all goes well
- I have 2 raid partition: 1 for root(md1) and 1 for swap(md1)

- After 2 weeks Mr.X call me and said that the server won't start
- I noticed the server started in degraded mode and the fs is read-only
- watching the output of ```
cat /proc/mdstat
``` I have 2 disks labeled as failed [ UU__ ]
- I wait for the (auto)recovery of both disks. After some hours, the recover processes end and the label became [UUUU]
- After that, hoping all is ok, I reboot the machine but the server starts again in degraded mode and one disk is again in status '_'
- I wait until recovery finish (*[UUUU] ) but after the new reboot the situation won't change!

- could be a physical problem on the disk?
- I have tried to remove and re-add the suspected disks to md1 but after resync nothing change (through mdadm)
- have I to try something else?

To clarify I have attached 2 files:
- the first one is the output of the cat /proc/mdstat after the first full recovery
- the second one is the situation after reboot

Thank you in advance!
Bye,

ar

---

