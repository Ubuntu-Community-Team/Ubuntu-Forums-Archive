---
title: "Dell PowerEdge 1750 SCSI Drives wont install"
date: 2011-04-30
forum: Server Platforms
---

### Post by Elochai on 2011-04-30
I looked though the forums and found one or two post on PowerEdges but didn't find an anwser to this problem I'm having. So I hope someone here can help me :).
 
I'm new to Dell PowerEdges. I got a good deal on a 1750 so I took it. It has 2 SCSI hard drives. Both are Maxtor 36GB ATLAS15K2_36SCA drives. When I go to install the server and I get to detect disk. It tells me that it's unable to find the disk drivers. I tried everyone on the list and I looked up Maxtor Drivers at Dell.
 
I feel as if I'm getting nowhere with this. So I think it time I step back and see if someone with more experience can help me get this thing running.
 
I been waiting for this to show up for a bit now and now that I got it and the gf is working, I'd was hoping to play around with it.
 
Thanks for your time and I do hope you can help me.

---

### Post by elico on 2011-04-30
the problem is the SCSI drivers so i found this:
[http://www.zaphu.com/2009/06/17/install-ubuntu-on-a-hp-xw9300-workstation-with-ultra320-scsi-hard-drives-ubuntu-tip/](http://www.zaphu.com/2009/06/17/install-ubuntu-on-a-hp-xw9300-workstation-with-ultra320-scsi-hard-drives-ubuntu-tip/)
saying to install with acpi=off switch.
if you do want to understant it more you can take a live cd of ubuntu and try to see what will happen when it runs.

another way is to get a Gentoo Minimal CD and boot the machine using it.
the gentoo Minimal CD has built-in many drivers and you can use on the cd the command:
```
 fdisk -l
```to see if it's recognizing the hardware such as "adaptec scsi ultra 320"(can be other name)
if it is then you can check using:
```
lspci 
```command what the device identified as and to find the module you need to make it work later.

---

### Post by Elochai on 2011-05-01
I was able to figure out the problem from Dell forums.

Thanks for your help tho.

The problem was within BIOS. It was with me not understanding configuration of RAID and SCSI. from some other post I read here on poweredges, it looks like some others may have the same issue. So I will link to my topic over at Dell.

[http://en.community.dell.com/support-forums/servers/f/906/t/19376552.aspx](http://en.community.dell.com/support-forums/servers/f/906/t/19376552.aspx)

---

### Post by harvledger on 2011-06-10
[SIZE=4]Using Ubuntu for a month now on the desktop and loving it!  
I too got a good deal on a poweredge 1750 and am wondering which version to install. I dl'd one , but it shows 'AMD' and the 1750 (which hasn't arrived yet) has a pair of xeons. With very little intimate experience since the 6809e I'd be grateful for all the direction I can get including recommended reading.
Thanx  Harv 
[/SIZE]

---

