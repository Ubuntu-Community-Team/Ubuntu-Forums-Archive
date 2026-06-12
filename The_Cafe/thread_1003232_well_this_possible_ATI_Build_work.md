---
title: "well this possible ATI Build work?"
date: 2008-12-05
forum: The Cafe
---

### Post by medievalman86 on 2008-12-05
intended OS: Ubuntu 8.10 prefered

Motherboard:[ECS A780GM-A AM2+/AM2 AMD 780G HDMI ATX AMD Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813135075")

Video Card:
1) [SAPPHIRE 100236L Radeon HD 3650 512MB 128-bit GDDR2 PCI Express 2.0 x16]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814102726")

2)[MSI R4850-T2D512 Radeon HD 4850 512MB 256-bit GDDR3 PCI Express 2.0 x16]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814127359")

3) [HIS Hightech H485F512P Radeon HD 4850 512MB 256-bit GDDR3 PCI Express 2.0 x16]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814161235")

-----------
previous experience with an old visiontek x1300, and reading about others experience tells me that ATI card are as a whole very problematic, require code after code, reboot, uninstall, reboot, install, etc

basically, Im looking for an ATI "plug and play" build that well quickly enable full desktop effects and such without any real hastle beyond a reboot after installing the driver.

I guess another basic question would be

Does Ati "Just work" now?

---

### Post by igknighted on 2008-12-05
Do you do gaming?  If you don't, the intel graphics work completely out of the box and will be way more powerful than you need.  Those higher-end ATI cards are a waste of energy if you aren't gaming.

---

### Post by medievalman86 on 2008-12-05
> **igknighted said:**
> Do you do gaming?  If you don't, the intel graphics work completely out of the box and will be way more powerful than you need.  Those higher-end ATI cards are a waste of energy if you aren't gaming.

I well be doing some gaming- as much as wine or cedaga or crossover well allow. World of warcraft and such games like that are my thing though....

but I well be getting a bluray player in the semi soon future.. this is for a entertainment first, gaming second machine.

---

### Post by igknighted on 2008-12-05
> **medievalman86 said:**
> I well be doing some gaming- as much as wine or cedaga or crossover well allow. World of warcraft and such games like that are my thing though....

but I well be getting a bluray player in the semi soon future.. this is for a entertainment first, gaming second machine.

I would consider a mobo with the intel g45 (x4500hd) graphics chip.  Works great OOTB with intel's open source drivers and can game just fine for basic stuff like WoW (ie... not Crysis).  You can always add a discrete card later if need be, but that intel chip will do HD movies like bluray just fine (I have it in my laptop w/ hdmi and bluray @ 1080p).  In the mean time you will save money, energy, and support open source by supporting a company that develops all their graphics drivers open source.

EDIT: Linux really struggles playing bluray at the moment (cannot watch new movies, watching old ones requires a lot of work), so I would consider waiting on that.

---

### Post by arrancaru on 2008-12-05
ATI's fglrx driver sucks, compared to nvidia's. Actually, if you don't care for desktop effects you can disable them and play videos, games and opengl apps without flickering.

---

### Post by medievalman86 on 2008-12-05
cool, did not know that. okay, everything else aside.- would that build take and run linux with effects like i refrenced in the op?

---

### Post by medievalman86 on 2008-12-05
> **arrancaru said:**
> ATI's fglrx driver sucks, compared to nvidia's. Actually, if you don't care for desktop effects you can disable them and play videos, games and opengl apps without flickering.


im really after the desktop effects.. could you elaborate on your assesment of fglrx? for someone who doesnt know to look for "sucky driver" would it suffice, work with the effects?

---

### Post by binbash on 2008-12-06
dude it is hard to get a decent fps with ati drivers WITH LATEsT wow expansion.Ready to dual boot.You can play videos without flickering while compiz is on, but you cant use applications which uses 3d.

It is easy to install ati drivers.but as i stated above if you are a hardcore wow player (like me before), do a dual boot or try your luck with nvidia drivers.It was not good to see the game crashed at a black temple raid or 3v1 pvp.

---

### Post by medievalman86 on 2008-12-06
> **binbash said:**
> dude it is hard to get a decent fps with ati drivers WITH LATEsT wow expansion.Ready to dual boot.You can play videos without flickering while compiz is on, but you cant use applications which uses 3d.

It is easy to install ati drivers.but as i stated above if you are a hardcore wow player (like me before), do a dual boot or try your luck with nvidia drivers.It was not good to see the game crashed at a black temple raid or 3v1 pvp.

makes sense.

---

### Post by mips on 2008-12-06
> **igknighted said:**
>   You can always add a discrete card later if need be, but that intel chip will do HD movies like bluray just fine (I have it in my laptop w/ hdmi and bluray @ 1080p).  In the mean time you will save money, energy, and support open source by supporting a company that develops all their graphics drivers open source.


Does the Intel gfx chip take the load of the CPU by doing the decoding? nVidia's [VDPAU]("http://en.wikipedia.org/wiki/VDPAU") allows the gpu to do the decoding which takes a big load of the cpu.

I have Intel gfx on my laptop and it's good for daily use, I also have it on my desktop but found it lacking in performance so updated to nVidia discreet card.

---

