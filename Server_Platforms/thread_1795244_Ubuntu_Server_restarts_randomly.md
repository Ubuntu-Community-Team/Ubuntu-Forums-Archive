---
title: "Ubuntu Server restarts randomly"
date: 2011-07-02
forum: Server Platforms
---

### Post by Varnius on 2011-07-02
Hi,
I`m using Ubuntu Server 10.10. The system randomly restarts each day.
Here are the logs: []("http://paste2.org/p/1499300")[_http://paste2.org/p/1499309_]("http://paste2.org/p/1499309")
Everything seems normal except that UDP: short packet thingy but even Google didn`t help me to find what`s that.

By the way, I think reboots started after I configured this PC as a gateway between internet and my local network.

Any help would be appreciated. :)

---

### Post by papibe on 2011-07-03
If I were you, I would try to discard all hardware instability first. I would start with the memtest86 available either in your BIOS or in the live Ubuntu CD.

I'd run it for an hour or so.

Regards.

---

### Post by Gyokuro on 2011-07-04
Hi,

there are two things: what's up with your sda6 which already get noted and look at the second problem:


[LIST=1]
[*]Jul  2 13:14:00 hostxxx kernel: [    7.245088] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 524299


[*]Jul  2 13:18:41 hostxxx kernel: [  300.040054] Machine check events logged
[/LIST]
I would suggest that you check sda6 and watch the machine check events via the **mcelog **tool **(sudo apt-get install mcelog**) as the former poster have already noted you should really check you hardware.

---

