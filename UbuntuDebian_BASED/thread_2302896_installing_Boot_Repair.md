---
title: "installing Boot Repair"
date: 2015-11-14
forum: Ubuntu/Debian BASED
---

### Post by korn16ftl3 on 2015-11-14
hello all i have a question i have been having odd issues in grub for example multiple selections at the boot up screen and i would like my default boot option to be windows 7 as it is my primary OS (i am dual booting kali a nd windows). i have played with boot repair before and really enjoy its simplicity to acheive a lot of what i am persuing i am also aware that kali linux is Debian based how ever i would like to install the boot repair package on my kali install for use how would i go about doing this? what commands should i use and things of that nature, do i need to add or edit the repo list in order to acheive this? thanks in advance for any help reguarding this situation.

---

### Post by grahammechanical on 2015-11-14
This is the official Boot Repair web site.

[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by korn16ftl3 on 2015-11-14
ok ill have a look and see what i can do with it thanks for pointing me in the right direction

---

### Post by oldos2er on 2015-11-14
Moved to Other OS, Ubuntu & Debian based.

Having multiple selections available at the grub menu isn't an "issue," it's normal. In default Ubuntu, you'd see at least two selections for each installed kernel, one normal and one recovery mode. There may also be different selections for systemd or upstart.

If you were using Ubuntu I'd suggest installing [grub-customizer]("https://launchpad.net/grub-customizer") to set your menu how you'd like it; I can't advise you on installing it on Kali. Why not check Kali's own forums? 
[https://forums.kali.org/](https://forums.kali.org/)

---

### Post by rocco6 on 2015-11-21
However, in order to take effect, Boot Repair must be launched like a Live Ubuntu version, from CD/DVD/USB.

---

