---
title: "how to manage an old serveraid adapter"
date: 2011-01-10
forum: Server Platforms
---

### Post by m.ardito on 2011-01-10
Hi, i am trying to recycle an old IBM server equipped with a hw raid device:
serveraid-4x, which lspci reports as:

$lspci -nn | grep -i raid
02:0a.0 RAID bus controller [0104]: IBM serveraid controller [1014:01bd]

$lspci -nn | grep -i scsi
02:05.0 SCSI storage controller [0100]: Adaptec AIC-7892p U160/m [9005:008f] (rev 02)

i can boot from 10.04 livecd and browse the logical disk, but can't find any way to manage this controller, e.g, to seta an email alert in case of phisical volumes damage, etc.

it came with windows 2000 server and had IBM serveraid manager installed; now  i want to switch to a linux (any), but can't find any way to even detect this controller.

on adaptec site i can't find anything about this controller (maybe too old)
i've also looked here [http://hwraid.le-vert.net/](http://hwraid.le-vert.net/)
but they only list Adaptec AACRaid series which i think does not aply to my controller. 
i tried anyway to install arcconf through apt-get but it finds no devices.


on ibm site i just found this
[http://www-947.ibm.com/support/entry/portal/docdisplay?brand=5000008&lndocid=MIGR-61707](http://www-947.ibm.com/support/entry/portal/docdisplay?brand=5000008&lndocid=MIGR-61707)
which should install the ibm manager on supported OSes:
 
[LIST]
[*]Microsoft Windows 2000
[*]Microsoft Windows 2003
[*]Microsoft Windows 2008
[*]Microsoft Windows XP
[*]Red Hat Enterprise Linux 3
[*]Red Hat Enterprise Linux 4
[*]SUSE Linux Enterprise Server 9
[*]SUSE Linux Enterprise Server 10
[*]Novell NetWare 6.5
[*]VMware ESX Server 3.0
[*]VMware ESX Server 3.5
[*]Sun Solaris 10
[*]SCO UnixWare 7.1.3
[*]SCO UnixWare 7.1.4
[*]SCO OpenServer 5.0.6a
[*]SCO OpenServer 5.0.7
[*]SCO OpenServer 6.0
[/LIST]
so, no ubuntu here... but RHEL 4... maybe it will work on CENTOS 4?

is there any chance, to your knowledge?

thanks, marco

---

### Post by disabledaccount on 2011-01-10
Maybe this not the best solution, but You can try to switch off raid mode and use mdadm instead (if it will be able to see particular harddisks).
For Raid1 and 10 it won't make big difference as this is very old hardware.

---

### Post by m.ardito on 2011-01-10
..thanks, that is another solution... :-)

Marco

---

### Post by PrivateSNAFU on 2011-01-10
What about using alien to convert the redhat rpm to a deb then install that.  Might work.

Good Luck:P

---

