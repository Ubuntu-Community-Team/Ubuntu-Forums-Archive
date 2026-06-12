---
title: "Netfinity 5000"
date: 2009-03-24
forum: Server Platforms
---

### Post by Dormage on 2009-03-24
U guys must hear this a lot but i'll say it anyway!
My knowledge of this topic is not expressable in numbers cause they don't go that low :D
So im a newb but im rady to learn :)

The problem appeared when i was trying to install Ubuntu server (latest version available) on my Netfinity 5000 server. The old comp is pritty banged up but still working. It's supposed to have 4 SCSI disk's but i think 1 of them is dead :)
However when booting Ubuntu i select the language and kayboard layout and after that i get an error asking me to manualy chouse the modul of the CD-ROM.
It simply wount let me pass that so i tryed manualy even if i had no idea what im doing.
I got the screen asking me to enter the modul in some sort of chatbox that was filled with dev\cdrom. As far as i know ubuntu has its CD-ROM's at dev\cdrom so i let it stay but it wount let me pass.
The comp is curently running server 2003 and it kinda works fine but nevertheless i feel i should inform you that righit be4 booting the comp an arror pops out saying SCSI bios not installed!
I read a few forum threads saying that mighit mean the SCSI  controller dosent recodnize the discs but then how does Windows server 2003 start o.O?
I mighit have left some inportant info unsaid so please if u'd require anything just ask and i'll do my best.
For those that will try to help me, 
I thank you in advance!:D

---

### Post by cariboo on 2009-03-24
There is a well know bug, that Ubuntu server won't install from a scsi cdrom drive. If the computer has IDE ports, just hook up an ide cdrom drive to install, then reconnect your scsi drive after your done.

Jim

---

