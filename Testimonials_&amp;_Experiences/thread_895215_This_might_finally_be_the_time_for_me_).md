---
title: "This might finally be the time for me :)"
date: 2008-08-20
forum: Testimonials &amp; Experiences
---

### Post by rob1101 on 2008-08-20
I have been playing with linux for years now but I have never been to completely switch over. Mainly due to hardware and games. I always comeback and try my hand at linux every once in a while. 

    So far I have tried Ubuntu, Debian, Fedora, Arch,  and probably a few others I can't remember right now multiple times on different systems. Anyway I think I can finally live windows free on this Thinkpad T61p. I got so fed up with vista, and thought I would give Ubuntu another shot before I install XP.

    I installed and everything works out of the box, except for suspend, Hybrinate(not a suprise), an LED for wireless LAN(no biggie really), and the Active Hard drive protection. Though I got suspend to work perfectly with very minimal tweaking, and I hear that the active hard drive protection can be tweaked to get working as well. 

   So to put things quite simply I think this might finally be my time to fully switch over. I really do like linux a lot more than windows in just about every way.

---

### Post by kspncr on 2008-08-20
Glad to hear everything's working out for you.

---

### Post by NWAdawg on 2008-08-20
Glad to hear it! I just recently made to step myself. good luck and have fun.

---

### Post by Teamgeist on 2008-08-20
Godd to hear (almost) everything works fine for you on your machine.
For the LED try installing the linux-backports-modules-hardy-generic Pakage.
You can do so by putting ```
sudo apt-get install linux-backports-modules-hardy-generic
``` in a terminal or install it through the Synaptic Package Manager.

Have fun with Ubuntu.

---

### Post by FJGamer on 2008-08-20
I would install XP first and then use Ubuntu as a boot option. Ubuntu is great, but I have too much in XP to scrap it.

---

### Post by Sef on 2008-08-20
> 
Code:

sudo apt-get install linux-backports-modules-hardy-generic



Backports can introduce instability or other problems in a stable system.

---

### Post by rob1101 on 2008-08-20
> **Sef said:**
> Backports can introduce instability or other problems in a stable system.

Yea that's what I was thinking, its not a big deal anyway to be honest I don't think I have ever seen it in xp or vista. And its just an LED I think I would know pretty quick if the WLAN stopped working :P So it is kind of a trivial feature, thanks though :)

---

### Post by Ewingo401 on 2008-08-20
It took me awhile to finally make the switch too.  I started out with Ubuntu 7.04 and used that for a few months and went back to Windows.  After a particularly bad trojan infection I decided to give Ubuntu another shot...it was on 7.10 at the time, I was pleasantly surprised to find things working out much easier.  After spending a long time with 7.10 with no problems and making a very easy transition to 8.04 with even better results, I think I'm now a lifer. :)

---

### Post by wolfen69 on 2008-08-20
great news. spread the word!

---

### Post by Teamgeist on 2008-08-20
> **Sef said:**
> Backports can introduce instability or other problems in a stable system.

Actually your right, but this time you're not. ;-)

This package has been around since hardy was released.
In there is stuff that's been backported by ubuntu devs from newer kernels. Meaning it has features that were not in the ubuntu kernel version but were important enough that the devs wanted them in. Instead of patching the kernel (again) this package was created. So if something breaks it can easily be removed.
It does introduce (among other stuff) support for the wifi LED of the Dell XPS m1330.

This is not like the backports repository that will be updated frequently. It is a static package just like anything else in main. Only reason for this to be updated would be security fixes.

Anyway. it is still your descision to install it. :D

---

