---
title: "easy raid setup"
date: 2007-09-01
forum: Server Platforms
---

### Post by jjh on 2007-09-01
after searching for days I can't find what I'm looking for. I have three hds in my server: one for the system and not so important data and two identical ones which i would like to make a raid 1 of.  I found [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
but I can't believe that's the only way!?

Isn't there a SIMPLE way to setup software raid in ubuntu server 7, where I can say take these two disks and make a raid out of it? I don't want to install linux on this raid...

jens

---

### Post by az on 2007-09-01
Use mdadm:

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by jjh on 2007-09-02
that's it! thank you!

---

### Post by LanDan on 2007-09-02
not sure if its any use,

but i once copied some howto's from and placed them on my wiki for my personal reference.

the thing is whether you want hardware RAID, Fake RAID or SOFT RAID,   i think everybody agrees that hardware RAID is the best option IF and only IF you have a REAL hardware controller instead of those halfway things you some times get, otherwise use the SOFT option

---

