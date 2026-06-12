---
title: "Grub2 won`t load"
date: 2015-07-06
forum: Ubuntu/Debian BASED
---

### Post by idris2 on 2015-07-06
Okay im new in ubuntu and here's my problem, im running dual boot between windows 10 and elementary os on acer aspire 4750. i just used it normally , no system change and i did not change everything. it just fine until suddenly when i tried to turn on my laptop , then the acer logo comes up, next the grub comes up, but it is only appearing 'grub loading', just that words, i waited so long but nothing happened.. i cant enter the bios menu via f2 and f12, so that's meant i can't plugin fdd to boot from. So what could i do to solve this?really need your help guys. Im using 256g sdd.

---

### Post by oldfred on 2015-07-06
Moved to Other OS since Elementary OS.

Did you turn off Windows fast startup which is its always on hibernation?
Did you turn off fast boot in UEFI?
Did you turn off Secure Boot in UEFI.

Acer require you to set a password (never lose that) to open more settings. And then you have to trust other installs.

 Screenshots of secure boot settings Asrock, Asus, HP, Acer
[https://neosmart.net/wiki/disabling-secure-boot/](https://neosmart.net/wiki/disabling-secure-boot/)
      
 Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)

 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

If still issues:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

