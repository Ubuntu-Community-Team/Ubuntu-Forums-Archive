---
title: "Connect multiple hard drives as one (as in WHS)"
date: 2011-02-24
forum: Server Platforms
---

### Post by joska_cz on 2011-02-24
Hi, I'm switching from Windows Home Server to Ubuntu Server edition. I'm pretty excited how easy it is, but I can't figure out how to connect multiple HDD in a bit specific way:

WHS has a nice user-friendly feature, which shows ALL non-system hard drives as one HDD, but eliminates the risk of software RAID 0, because it saves the entire file to one HDD, so if one of your hard drives breaks down, the files on others are still intact and can be easily extracted.
The main benefit is that when family members and other users copy their files to server, they don't have to think which HDD is for movies, backups, music etc. It's just one folder - easy and simple.

Is there some script of service that can make this work on Linux? I wan't to avoid SW or HW RAIDs, since they significantly reduce the total capacity and I don't really need mirrors.

--

*Uff, I hope that it's at least understandable, since my english is not so good as it should be.*

---

### Post by gobbledigook on 2011-02-24
hi :)

i connect my drives together using [mhddfs ]("http://www.google.co.uk/url?sa=t&source=web&cd=1&sqi=2&ved=0CBoQFjAA&url=http%3A%2F%2Fmanpages.ubuntu.com%2Fmanpages%2Flucid%2Fman1%2Fmhddfs.1.html&rct=j&q=mhddfs%20ubuntu%20help&ei=IGpmTZPiMIas8QPOx9XIDQ&usg=AFQjCNHSxo58Ftr8T7fB7e3J-SSPcEafQQ&cad=rja")which you add each mount point to it and t displays them all in one "folder". I am looking at moving over to [LVM]("http://www.google.co.uk/url?sa=t&source=web&cd=2&ved=0CC4QFjAB&url=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FSettingUpLVM-WithoutACleanInstall&rct=j&q=lvm%20ubuntu%20help&ei=C2hmTdmQDZOxhQfT_MmuDQ&usg=AFQjCNGXgSjanIsnZm7tKSBE2xgZxgbpZA&cad=rja") which you could also consider, i haven't yet cause i have TB of storage and from what i understand all drives need to be re-formatted.

---

### Post by joska_cz on 2011-02-24
Yeah, LVM seems nice and it definitely requires hard drive formating. I would be pesimist about LVM, since it doesn't make a difference between hard drives, so the risk of loosing data in failure is similar to RAID 0.

---

### Post by joska_cz on 2011-02-25
Thank you very much, mhddfs did the work.

---

