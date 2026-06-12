---
title: "[SOLVED] 8.1: Network loads with live CD not with server CD"
date: 2008-11-05
forum: Server Platforms
---

### Post by Astro6312 on 2008-11-05
I booted my server with the live 8.1 64bit CD, everthing went ok. Network loaded ok without a problem.

I boot with the server 8.1 CD 64bit and no network is detected.

I don't understand why it would work with the live cd and not the server cd.

I can always load manually with those [drivers]("http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/13663/eng/igb-1.3.8.6.tar.gz&agr=&ProductID=2874&DwnldId=13663&strOSs=&OSFullName=&lang=eng"), but not sure I want to go there.

Any hints will be appreciated.

---

### Post by Astro6312 on 2008-11-05
I have tried with the 32 bit version and same problem.  No nextwork card detected.

LSPCI shows the two intel nic OK.

:confused::confused:

---

### Post by Astro6312 on 2008-11-05
Ok here's some more information while booted with the live CD. This is when the network loads ok.

lspci | grep -i network
> 08:00.0 Ethernet controller: Intel Corporation 82575EB Gigabit Network Connection (rev 02)
08:00.1 Ethernet controller: Intel Corporation 82575EB Gigabit Network Connection (rev 02)

lsmod | grep igb
> igb                    94212  0

uname -a
> Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64 GNU/Linux

lsb_release -rd
> Description:	Ubuntu 8.10
Release:	8.10


When I boot from the server cd and go to the repair system.  I cannot find the igb drivers.  I see ixgb drivers but not igb in /lib/modules/<KERNEL VERSION>/kernel/drivers/net/igb/

If I do insmod of the ixgb drivers, I have no error message.

Any clues what is going on here?

---

### Post by Astro6312 on 2008-11-05
So, I manually loaded the drivers that I downloaded from intel web site and it worked fine.

Not sure if I need to load those drivers if I change the kernel with an update?

I think the igb intel drivers where simply missing from the server CDs since they are in the desktop CD of ubuntu 8.1

Should this be entered as a bug.

---

