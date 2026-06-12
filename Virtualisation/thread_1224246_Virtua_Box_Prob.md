---
title: "Virtua Box Prob"
date: 2009-07-27
forum: Virtualisation
---

### Post by m4tic on 2009-07-27
ok i had virtuabox instaed on Ubuntu Jaunty for about two weeks, had debian, winxp, mandriva installed on their own partitions. Well just three days ago somethin weird happend, virtuabox keeps aborting wen trying to boot up all OS, so i deleted before trying to get hep. Has anyone had this probem before because i wanna keep virtualising and maybe try preventing or be able to solve this issue may it occur again.

---

### Post by aesis05401 on 2009-07-27
I have not had this issue, but I can give you a tip that will help prevent data loss in the future.  

VirtualBox harddrives are known as .vdi files - and they are actually not that hard to work with manually.  All the documentation is online to cut an image out of a .vdi file or to mount an existing image as a .vdi file.  

So this means that even if something goes horribly wrong with VirtualBox, you should be able to succesfully rescue the .vdi drives.  Provided the files are readable you can rip the installed image out of the .vdi to mount it another way.

One tool that used to be around was just called vditool.  If you can't find an up to date automated tool then search docs on how to remove the VirtualBox specific parts of the .vdi from the command line.

---

### Post by rannable on 2009-07-28
i had this on my dell e5500, i put it down to a hardware glitch but could be wrong but anyway i switched to 64bit ubuntu from 32bit and now it works perfectly...

---

