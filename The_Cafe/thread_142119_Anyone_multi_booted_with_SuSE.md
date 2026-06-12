---
title: "Anyone multi booted with SuSE?"
date: 2006-03-09
forum: The Cafe
---

### Post by Swiss on 2006-03-09
Anyone multi booted with SuSE? I want to MultiBoot XP, Ubuntu, and SuSE. I am already DualBooting XP & UB, I just want to know if SuSE has a good partitioner, and if anyone here has done this already.... :)

---

### Post by Lux Perpetua on 2006-03-09
You just described my computer. :) The SuSE installer has a good partitioner. If you want to do anything fancy, though, then you'll have to go the "expert" route, which is very usable. You just might have to click around before you find exactly what you need. 

However, if you plan to share a /boot partition, then back up your /boot/grub/menu.lst before installing SuSE; you might (or might not) need it later to get your other OSes back on the map. (I needed it, but then I have a fairly complex setup.) (SuSE should make a backup, but of course, you should have your own.)

---

### Post by ComplexNumber on 2006-03-09
[quote=Swiss]Anyone multi booted with SuSE? I want to MultiBoot XP, Ubuntu, and SuSE. I am already DualBooting XP & UB, I just want to know if SuSE has a good partitioner, and if anyone here has done this already.... :)[/quote] yes, i tri-boot involving suse. in the past, i have tri-booted bwteen XP, ubuntu, and suse. suse has a good partitioner and has lots of good tools for fixing corrupting MBR's and installations etc.

> 
However, if you plan to share a /boot partition, then back up your /boot/grub/menu.lst before installing SuSE; you might (or might not) need it later to get your other OSes back on the map. (I needed it, but then I have a fairly complex setup.) (SuSE should make a backup, but of course, you should have your own.) thats not at all necessary, if i've understood you correctly. i have installed fedora after suse (note that fedora did not recognise suse. only XP and fedora) and i got suse to 'reconfigure' the booting list correctly so that it recognised XP, fedora, and suse and included all OS's in the boot list. it did this successfully.

---

### Post by darkmatter on 2006-03-09
SuSE is excellent at partitoning, auto-detecting other os's

Plus it has a prettier grub ;)

---

### Post by Lux Perpetua on 2006-03-09
> **ComplexNumber] thats not at all necessary, if i've understood you correctly. i have installed fedora after suse (note that fedora did not recognise suse. only XP and fedora) and i got suse to 'reconfigure' the booting list correctly so that it recognised XP, fedora, and suse and included all OS's in the boot list. it did this successfully.[/QUOTE]Depending on the boot setup, it may or may not be necessary. I have Ubuntu and Suse sharing a physical partition with LVM, and as far as I can see, SuSE was unable to figure out the Ubuntu part correctly. (I'll retract my statement if you point out how to get SuSE to reconfigure this by itself. Maybe I just didn't see it said:**
> 
Plus it has a prettier grub ;)I didn't like it, personally, but don't worry, you can go back to the plain Grub menu just by commenting out a couple lines in your /boot/grub/menu.lst. Anyway, yeah, it would probably be considered "prettier." :-)

---

### Post by YourSurrogateGod on 2006-03-09
Yeh, the partitioner was pretty damn good. I've booted XP and Suse before, but never with Ubuntu in the mix. I like the idea of having disks for some software, which helps to cut down on the amount of bandwith wasted.

Not to get up in your business Swiss and tell you what to do, but why are you trying to install Suse? From my experience it was a rather annoying distro (I had 9.0.) I've installed KDE on Ubuntu and that worked swimmingly (with the exception of one or two little annoying bugs.) Just curious...

---

### Post by Rev. Nathan on 2006-03-10
[QUOTE=darkmatter]Plus it has a prettier grub ;)[/QUOTE]
In either case, you can download new grub themes, which almost all look prettier than the ones I've seen (gentoo, ubuntu, debain... which suprisingly has a diffrent grub than ubuntu).

---

### Post by Jucato on 2006-03-10
Um... this is kinda off-topic. I'm interested in trying out SuSE, too. I was wondering if there's a live CD out there. Also, are you guys talking about the Eval SuSE or openSuSE? Lastly, Do I really have to download all the CD ISO's? I have a DSL connection and I don't mind downloading stuff that I would need later, but I don't want to download multiple CD images. Thanks!

---

### Post by aysiu on 2006-03-10
This may be just a SuSE Personal 9.1 thing, but SuSE's installer wouldn't let me install it to any partition but the *last* one. Weird. Other distros would let me install to any partition I wanted.

---

### Post by Swiss on 2006-03-10
> Not to get up in your business Swiss and tell you what to do, but why are you trying to install Suse?

Oh, I took a look at it (10.0) and thought it looked nice, I want a Gnome Distro (Ubuntu) and KDE (SuSE 10.0 or Kubuntu) SuSE got good reviews so I thought "hey why not!" 


Can anyone recommend a better KDE distro?

---

### Post by TrailerTrash on 2006-03-10
[QUOTE=Swiss]Oh, I took a look at it (10.0) and thought it looked nice, I want a Gnome Distro (Ubuntu) and KDE (SuSE 10.0 or Kubuntu) SuSE got good reviews so I thought "hey why not!" 


Can anyone recommend a better KDE distro?[/QUOTE]


The best other KDE distro ive ever used (and ive used many distros) is PCLinuxOS. Its greeat! :mrgreen: 

[www.pclinuxos.com](www.pclinuxos.com)

---

### Post by Lord Illidan on 2006-03-10
Imho, SUSE was the best KDE distro I installed. Kubuntu beat it when it came to installing programs and such, because it had apt-get. If YAST didn't suck so much, I might still be using SUSE. Though, then the forums pale in comparison to these, and I couldn't install KDE 3.5 due to dependency hell.

Also, it is bloated. And while it is quite fast normally, YAST is **unbelievably** slow.

---

### Post by Swiss on 2006-03-10
> The best other KDE distro I've ever used (and I've used many distros) is PCLinuxOS. Its greeat! 


I tried it, but it messed up my XP and Ubuntu install...

---

