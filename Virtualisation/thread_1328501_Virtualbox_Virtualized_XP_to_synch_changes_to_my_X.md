---
title: "Virtualbox Virtualized XP to synch changes to my XP partition"
date: 2009-11-16
forum: Virtualisation
---

### Post by Markkreuzz on 2009-11-16
**Is there a way for Virtualbox's Virtualized XP to sych changes to my XP partition??? :(**



Hello. I have been searching this forum for virtualization stuff and somehow managed to get my XP HD install virtualized using this guide [**[COLOR="Sienna"]_here_[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=769883"). 

Ok everything is up and running, I installed MS office and some updates on my virtualized XP. All was good until i decided to boot into my XP install natively....
 and lo and behold no Office 2007!!! :shock:... not even Service Pack 3 was installed :shock:.

So now i'm kinda wondering if there is anyway to synchronize the changes i have made on my Virtual XP down to my Native XP install... 
Or do i have to change some settings in Vbox like read/write to my XP partition... Any kind of help or info would be appreciated. :cry:

BTW im running Hardy Heron 8.04 and virtualbox 3.0.10 r54097

---

### Post by Markkreuzz on 2009-11-18
:KS BUMBP :KS !!!!!

**PROBLEM SOLVED!!!**

I was tinkering around virtualbox and found out the reason it doesn't write to the partition is because i took a snapshot, when snapshots are taken it creates a differential disks (which kinda works like diff backups). The solution was to revert all the snapshot then discard the remaining 1. That made virtualbox update my windows partition. :P... Also while going about in this forum i found a great info about snapshots **_[COLOR="DarkOrange"][HERE]("http://ubuntuforums.org/showthread.php?t=689982")[/COLOR]_**. So be careful when messing around and deleting snapshots because you might lose hours of work :shock:. 

Also another tip I've picked up somewhere was to disable the **IO-APIC**(warning::disabling it wrongly might bork your virtual image! Go [COLOR="DarkOrange"]**[_HERE_]("http://forum.virtualbox.org/viewtopic.php?f=2&t=21480&start=0")**[/COLOR] for the howto) option which greatly improved my virtualbox performance.... \\:D/

---

