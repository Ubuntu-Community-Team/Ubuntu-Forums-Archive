---
title: "Perc5/I Problems"
date: 2008-12-18
forum: Server Platforms
---

### Post by Snakekick on 2008-12-18
Hello, i use the perc5 raid Controller. For RAID monitoring i want to use megacli but this dont work.
my system is a amd64 sys
when i start megacli this error come:

Failed to get ControllerId List.
Failed to get CpController object.

i read in a forum that i need mfi driver (&#8220;MegaRAID Firmware Interface")
it is correct ? how get i this?
thanks

i use Ubuntu 8.10
ubuntu 8.04 have this "man page"

[http://manpages.ubuntu.com/manpages/intrepid/man4/mfi.html](http://manpages.ubuntu.com/manpages/intrepid/man4/mfi.html)
is this support remove in 8.10 ?

---

### Post by gtdaqua on 2008-12-19
Are you trying to monitor the hardware raid? If so, then you should not use megacli as that is intended for software raid arrays.

Use Dell OMSA to monitor the physical hardware including storage controller. Which PE model are you using?

---

### Post by Snakekick on 2008-12-19
i have solved the problem with megacli 
i use another version :
[ftp://fr2.rpmfind.net/linux/Mandriva/official/2008.1/x86_64//media/non-free/backports/megacli-2.00.11-1mdv2008.1.x86_64.rpm](ftp://fr2.rpmfind.net/linux/Mandriva/official/2008.1/x86_64//media/non-free/backports/megacli-2.00.11-1mdv2008.1.x86_64.rpm)

that work

---

