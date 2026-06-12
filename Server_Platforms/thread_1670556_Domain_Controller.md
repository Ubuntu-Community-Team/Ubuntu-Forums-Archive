---
title: "Domain Controller"
date: 2011-01-19
forum: Server Platforms
---

### Post by motermouth15 on 2011-01-19
I just decided that I no longer wanted to use Windows Server 2008 because of my wide variety of machines, however, i'm still a noob. I currently have webmin installed on my ubuntu server, however, i'm wondering what the easiest way to make it a domain controller would be (preferably so i could manage it through webmin). I did do some google searches however none of them really seemed to have gone through webmin. 

If this question gets asked a lot i'm sorry, i'm still completely new at the whole linux server idea.

Thanks!!
-Nate

---

### Post by dreadblack on 2011-01-19
You can use OpenLDAP + Samba as your Domain Controller under Ubuntu Server. Here's a thread [http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760) it says 7.10 but I've tested it under 8.04 without problem... Remember to remove the AppArmor first. :D

---

