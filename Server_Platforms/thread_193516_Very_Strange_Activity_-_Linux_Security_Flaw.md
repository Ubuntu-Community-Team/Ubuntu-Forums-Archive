---
title: "Very Strange Activity - Linux Security Flaw??"
date: 2006-06-10
forum: Server Platforms
---

### Post by T-Minus1 on 2006-06-10
Hi All...

Two days ago i did a search for "Eizo TFT" under google and clicked on a link hosted by Aurorasystems.se (i think). I was logged on as the primary user, ie with root priviledges, and was using Dapper. I attempted to click on the picture of the monitor but also noticed my hard disk was very busy. Several popups appeared, which i attampted to cancel (popup blocker was on). I eventually managed to cancel all the images, tried to logout only my menus had ALL disappeared!!. I did a hard shutdown, tried to reboot and whilst attempting to load device drivers, service etc, i noticed alot of "Failed" results. Basically, system files had been deleted i suspect. I have since tried to reinstall, but a failure results on each occasion. Is this a possible boot sector virus?? I WOULD NOT recommend going on this site, but i was unsure of how to notify security teams/individuals to check this situation and confirm...any explanations??

---

### Post by fmo on 2006-06-10
I think that what you need is a proper fsck of you file system you might have damaged some files.

Try this, it's going to reboot you PC and a FSCK is going to be doing upon reboot
```
sudo shutdown -r -F now
```

Next time you have this kind of problem, shutting down the X interface with CTRL+ATL+BACKSPACE should do the trick without risking damage on your filesystem.

---

### Post by LordHunter317 on 2006-06-10
[QUOTE=T-Minus1]Two days ago i did a search for "Eizo TFT" under google and clicked on a link hosted by Aurorasystems.se (i think). I was logged on as the primary user, ie with root priviledges,[/quote]No, that's not what hte primary user has.

> and was using Dapper. I attempted to click on the picture of the monitor but also noticed my hard disk was very busy. Several popups appeared, which i attampted to cancel (popup blocker was on). I eventually managed to cancel all the images, tried to logout only my menus had ALL disappeared!!. I did a hard shutdown, tried to reboot and whilst attempting to load device drivers, service etc, i noticed alot of "Failed" results. Basically, system files had been deleted i suspect.No, I don't believe that is the case in the least.  Without detailed logs, there is no way to tell.

>  I have since tried to reinstall, but a failure results on each occasion. Is this a possible boot sector virus??Assuredly not, if it's affecting the reinstaller.

I suspect bad hardware, probably a HDD.

---

