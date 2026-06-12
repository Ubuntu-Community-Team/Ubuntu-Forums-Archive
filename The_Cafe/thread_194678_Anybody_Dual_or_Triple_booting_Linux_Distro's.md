---
title: "Anybody Dual or Triple booting Linux Distro's"
date: 2006-06-11
forum: The Cafe
---

### Post by richbarna on 2006-06-11
I know that most people on this forum are or have at some point dual-booted with Xp.

I have had a few probs with the MBR/GRUB recognizing two Linux distro's and was just wondering what you would recommend as a second or third distro, and also if there is an easier solution to the MBR/GRUB problem ?

---

### Post by John.Michael.Kane on 2006-06-11
I'm about to try gentoo live install. if that works then i will be dual booting gentoo/ubuntu for a while.

---

### Post by richbarna on 2006-06-11
Any Bootloader issues with that ?
I tried Dapper/ Dapper and each time only the newest install is shown.
I don't see why it doesn't get found like with XP.

---

### Post by John.Michael.Kane on 2006-06-11
richbarna i will post back after i have done. i have also run ubuntu6.06 side by side with xp, with no grub issues. so can't really speak on those kinds of problems.

---

### Post by xXx 0wn3d xXx on 2006-06-11
[QUOTE=richbarna]I know that most people on this forum are or have at some point dual-booted with Xp.

I have had a few probs with the MBR/GRUB recognizing two Linux distro's and was just wondering what you would recommend as a second or third distro, and also if there is an easier solution to the MBR/GRUB problem ?[/QUOTE]
I would recommend Gentoo, Archlinux, and Debian. As for the MBR problems, try re-installing grub. [ Here is the tutorial. ](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by aysiu on 2006-06-11
I usually just copied over the relevant entry from one distro's Grub to the other distro's Grub menu.lst (the one that was installed on the MBR).

---

### Post by richbarna on 2006-06-11
[QUOTE=xXx 0wn3d xXx]I would recommend Gentoo, Archlinux, and Debian. As for the MBR problems, try re-installing grub. [ Here is the tutorial. ](http://doc.gwos.org/index.php/Restore_Grub)[/QUOTE]
Thanks for the how to, I suppose that when I mount all partitions and THEN install GRUB they are automaticall added ?

Going to Distrowatch for a read-up on Gentoo and Archlinux,
Thanks for the tips :)

---

### Post by benplaut on 2006-06-11
ubuntu, arch, and gentoo

---

### Post by spier on 2006-06-11
I have currently  Dapper, Breezy, winxp and vaio`s recovery partitions on grub. I noticed (just another beginner thought) that everything between the following menu.lst tags

### BEGIN AUTOMAGIC KERNELS LIST
### END DEBIAN AUTOMAGIC KERNELS LIST 

will be overwritten by new installations or kernel updates. Thus, I moved out of them the boots I`m interested to preserve.

---

### Post by richbarna on 2006-06-11
[QUOTE=aysiu]I usually just copied over the relevant entry from one distro's Grub to the other distro's Grub menu.lst (the one that was installed on the MBR).[/QUOTE]
Aah Aysiu, I have spent the best part of tonight not only reading psychocats.net but sending everybody and his mother there.
I couldn't PM you, and was waiting.
Any chance of an Ubuntu/Ubuntu dual boot guide on your splendid website? ;)

Yeah, Ive been reading about copying over to the menu.lst, most involve using a floppy drive/disk which I don't have.

Could I install second Dapper, boot, mount the partition and gksudo nautilus to the file then manually edit the menu.lst ?

I,m kind of looking for a copy paste method here ;)

Also, thanks for the "pure xfce" guide, working sweet on a 64Mb laptop !!

---

### Post by WildTangent on 2006-06-11
I triple-boot, but not with other Linux distros. I've got Ubuntu Dapper, Windows XP, and Windows Vista right now.

-Wild

---

### Post by richbarna on 2006-06-11
Had a look at Gentoo and Archlinux, think i'll give Gentoo a go, Arch doesn't really jump out at me if you know what I mean.

I know a lot of peolpe try the Live cd's but I'm not really all that keen on them myself.
For some sad geeky reason I really do enjoy installing OS's (whther they work ok or not) :)

---

### Post by RAV TUX on 2006-06-11
[quote=richbarna]Had a look at Gentoo and Archlinux, think i'll give Gentoo a go, Arch doesn't really jump out at me if you know what I mean.

I know a lot of peolpe try the Live cd's but I'm not really all that keen on them myself.
For some sad geeky reason I really do enjoy installing OS's (whther they work ok or not) :)[/quote] 
try "dyne:bolic 2.0" this distro is damn sweet!
[http://www.dynebolic.org/index.php?show=available]("http://www.dynebolic.org/index.php?show=available")
  

I plan to triple boot:

XPsp2/dyne:bolic/Gentoo

---

### Post by MetalMusicAddict on 2006-06-11
I have XP, Ubuntu and Xubuntu installed. I did Xubuntu because I wanted to play games but still use Compiz.

Xubuntu+Games=:D

---

### Post by Lucho on 2006-06-11
I´m running this: 32-bit Debian Etch, and 64-bit Breezy. In addition,
I´ve got 32-bit dapper installed just to give a bit of a shakedown. I´ll
say this: 32-bit Etch and 64-bit Breezy are formidable combo. 
      It´s just my opinion, but my experience with Dapper is that it´s 
just not quite ready -yet- but it is still pretty sweet.
      Here´s how I handle Grub and the multi-boot: I boot out of Etch.
When I install a new distro to test, I don´t install a boot loader. I just
edit the one in Etch. So, my bootloader never changes, and I can do
whatever  I want in the other partitions; I know I´ll still be able to boot
the system

---

### Post by richbarna on 2006-06-12
[QUOTE=yozef]try "dyne:bolic 2.0" this distro is damn sweet!
[http://www.dynebolic.org/index.php?show=available]("http://www.dynebolic.org/index.php?show=available")
  

I plan to triple boot:

XPsp2/dyne:bolic/Gentoo[/QUOTE]

Dynebolic coming down now, looks like it's got a lot of features. It's amazing how many different distro's there are.

Lucho: Thanks for the GRUB tip, I think I've got a pretty good idea of how to multi boot with Linux now.

And thanks everyone else for the distro suggestions :)

---

### Post by RAV TUX on 2006-06-12
[quote=richbarna]Dynebolic coming down now, looks like it's got a lot of features. It's amazing how many different distro's there are.

Lucho: Thanks for the GRUB tip, I think I've got a pretty good idea of how to multi boot with Linux now.

And thanks everyone else for the distro suggestions :)[/quote] 


I'm downloading **StartCom MultiMedia Edition 5-ML-5.0.5 (Kessem)**
[http://www.startcom.org/]("http://www.startcom.org/")
[http://www.startcom.org/index.php?lang=en&app=15](http://www.startcom.org/index.php?lang=en&app=15)

---

### Post by benplaut on 2006-06-12
[QUOTE=yozef]try "dyne:bolic 2.0" this distro is damn sweet!
[http://www.dynebolic.org/index.php?show=available]("http://www.dynebolic.org/index.php?show=available")
[/QUOTE]


what's so amazing about it (what is it?). I've heard the name, so there must be something :rolleyes:

---

### Post by richbarna on 2006-06-12
[QUOTE=benplaut]what's so amazing about it (what is it?). I've heard the name, so there must be something :rolleyes:[/QUOTE]

Runs on 64Mb RAM :) (got to keep those old PC's running)

---

### Post by richbarna on 2006-06-12
[QUOTE=yozef]

I plan to triple boot:

XPsp2/dyne:bolic/Gentoo[/QUOTE]

Hey !? Where's Dapper in that equasion ?
I think somebody has forgotten something :rolleyes:

---

### Post by RAV TUX on 2006-06-12
[quote=richbarna]Hey !? Where's Dapper in that equasion ?
I think somebody has forgotten something :rolleyes:[/quote] 
I use Dapper on my other computer exclusively. I haven't been able to get Dapper to work on my EM64T computer.

see the thread here:
[http://www.ubuntuforums.org/showthread.php?t=190189]("http://www.ubuntuforums.org/showthread.php?t=190189")

---

### Post by richbarna on 2006-06-12
[QUOTE=yozef]I use Dapper on my other computer exclusively. I haven't been able to get Dapper to work on EM64T.

so the thread here:
[http://www.ubuntuforums.org/showthread.php?t=190189](http://www.ubuntuforums.org/showthread.php?t=190189)[/QUOTE]

Maybe Edgy will deal with that ?
I'm thinking of a computer upgrade soon, so I hope so.

---

### Post by kievking on 2006-06-12
Dapper/Gnome
Fedora4/KDE
Breezy/Gnome on USB HD
XP
Second Grub menu

I've been lucky - flawless booting for months

---

### Post by RAV TUX on 2006-06-12
[quote=richbarna]Maybe Edgy will deal with that ?
I'm thinking of a computer upgrade soon, so I hope so.[/quote]

I certainly hope so Ubuntu is my distro of choice even if it doesn't load on my new Computer. So I am looking forward to Ubuntu Edgy Eft and I will probably give Debian Etch a try also.

---

