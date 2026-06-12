---
title: "WinSVR 03 software RAID5 migrate to Ubuntu Server 9.04"
date: 2009-05-30
forum: Server Platforms
---

### Post by ubunRyan518824 on 2009-05-30
Hi, I am a new user of Linux and have to say that I have never enjoyed using my computer more than I do now. Thank You Ubuntu Creators and Users. Now since I am loving linux on my desktop so much, I want to get it on my server. 

Ok now to my question. I am currently running Windows Server 2003 and have been for a few years. With that server I have a "software raid5" with 3, 320GB drives, formated in NTFS. 

Qu1: Will Ubuntu SVR9.04 use a Windows SVR03 "software" raid setup or will will it detect them as single drives?

Qu2: Should I keep it in NTFS or format to something different and restore data to it?

---

### Post by Vegan on 2009-05-30
I do not particular like software RAID as there are enough problems with hardware ones already.

Low cost RAID cards are you best bet and a 4 channel SATA card is << $100.

Using a card means the OS cannot break the RAID when it fails.

As for a file system, Linux works safest with EXT3 file system.

My suggestion is if you want to dump the Windows server, Ubuntu server can be used. SAMBA can make Linux shares visible to Windows clients.

SAMBA is what I use on my machine to allow me to use Windows web development tools.

---

### Post by ubunRyan518824 on 2009-05-30
That is the plan, get ride of microsoft all together. I will take your advice and go with the EXT3 format. I will just back up the raid5 and rebuild with in ubuntu server. I am not sure if i can do a raid with the onboard sata controllers on my motherboard. Been a while since i bought it, but buyin a 4 port sata raid controller that i trust, like promise or something just cant do that right now, but want one!! Well thanks for the insite. I am just sick  of MS ******** and want to get all my pc in the house running on ubuntu!!....

---

### Post by Vegan on 2009-05-30
I strongly advice buying a low cost SATA card. It will make your life 10x easier.

---

