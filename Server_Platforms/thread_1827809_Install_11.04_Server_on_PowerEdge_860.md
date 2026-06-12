---
title: "Install 11.04 Server on PowerEdge 860"
date: 2011-08-18
forum: Server Platforms
---

### Post by dwessell on 2011-08-18
Hi,

I've just installed 11.03 Server 64 on a Dell PowerEdge 860. Installation went fine, the only thing out of the ordinary that I saw was it did the install on sdb and not sda. I was prompted for reboot as expected, but on reboot I never see grub (installed to /sdb as the default). There's no screen output and the server just hangs.

There's a SAS1068 Raid Controller with two HD's attached to it. I've run Dell Hardware diagnostics and they all come back fine. Can anyone offer me any suggestions?

Thanks
David

---

### Post by Sanados on 2011-08-22
my first thought was ... how big is your /boot?

some (older) bios have real issues when addressing partitions that are big.
In terms of > 2GB on the really old computers.
Even newer ones tend to have problems with partition > 200GB

Easiet way to bypass this would be to create first partition on first harddrive with about 100MB and mount this partition as /boot.
Also second partition bout 8GB as /
(then just make sure you got enough space to mount into /var (for logging))

(my basic setup:

/boot 100MB (primary)
/ 8GB root (primary)
/20 GB /var (primary)
/data (rest - primary) (or logical partition and split as needed)


some nice infos to read up (in german though)
[http://www.bios-info.de/4p92x846/hdisk.htm](http://www.bios-info.de/4p92x846/hdisk.htm)

---

