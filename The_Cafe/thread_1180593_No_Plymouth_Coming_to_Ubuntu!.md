---
title: "No Plymouth Coming to Ubuntu!"
date: 2009-06-07
forum: The Cafe
---

### Post by Sashin on 2009-06-07
Source:
[http://www.phoronix.com/scan.php?page=news_item&px=NzI5NQ](http://www.phoronix.com/scan.php?page=news_item&px=NzI5NQ)

The planned boot time for Karmic +1 will be under 10 seconds. Meaning that by the time plymouth would have had time to load it would have already reached the GDM.

Despite the upset, the increased speed certainly does make things worthwhile. But now there is an important issue that needs to be address.

**Someone with the adequate knowledge needs to make a smooth jaunty usplash theme.**

Please, if someone here is savvy enough take this theme:

[http://gnome-look.org/content/show.php?content=93386](http://gnome-look.org/content/show.php?content=93386)

And convert it so that it uses the jaunty bootloader and it runs on Jaunty.

PLEASE!

---

### Post by SunnyRabbiera on 2009-06-07
Feh Plymouth doesnt work for me anyway so it dont bother me (certain video cards and systems are not supported by Plymouth.)

---

### Post by Sashin on 2009-06-07
Still, the idea of a flicker free startup would still be nice. Hopefully someone makes an Ubuntu Usplash smooth for Jaunty.

---

### Post by DeadSuperHero on 2009-06-07
Well, time to take that cyanide pill I was saving. Goodnight everyone!

---

### Post by Sashin on 2009-06-07
But there's still hope, we just need someone to make a jaunty usplash smooth and we'll be able to have a flicker free startup.

---

### Post by jonathanysp on 2009-06-07
yea plymouth does look nice but how long do you actually spend on the boot screen each day? 30 seconds? I guess they could make it optional or smth and also make it easier to change usplash screens. and please someone make a smooth jaunty usplash screen!

---

### Post by kpkeerthi on 2009-06-07
Jaunty's 15 seconds GRUB -> GDM is good enough. 

They should rather focus on reducing the GDM -> Desktop load time (~25 seconds for me!) than saving an extra 5 seconds on GRUB -> GDM.

---

### Post by gnomeuser on 2009-06-07
And people STILL labor under this inane notion that plymouth is just about beautiful graphics. It's also enabling Kernel Modesetting which greatly improves X startup time which is why Moblin uses a version Plymouth to get their 5 sec boot.

We need something like plymouth to hit a 10sec goal, since they are rejecting plymouth knowing this it is starting smell badly of not invented here syndrome. In which case I imagine it won't be long till we are presented with the KMS enabled usplash, in essense a pointless duplication of work.

---

### Post by Giant Speck on 2009-06-07
I had to look up what Plymouth was.

*REALLY?*  A boot splash program?  #-o

---

### Post by ghindo on 2009-06-07
It's kernel modesetting (KMS) which gives a flicker-free boot, not Plymouth specifically.  Karmic Koala will have KMS enabled, so there *should* be a flicker-free boot.

---

### Post by 3rdalbum on 2009-06-07
> **kpkeerthi said:**
> They should rather focus on reducing the GDM -> Desktop load time (~25 seconds for me!) than saving an extra 5 seconds on GRUB -> GDM.

+45 (that's the total amount of time it takes for Gnome to start on my computers! One of them has an SSD for gof's sake!)

---

### Post by Mazza558 on 2009-06-07
> **kpkeerthi said:**
> Jaunty's 15 seconds GRUB -> GDM is good enough. 

They should rather focus on reducing the GDM -> Desktop load time (~25 seconds for me!) than saving an extra 5 seconds on GRUB -> GDM.

Absolutely. Especially if people use a lot of panel widgets, GNOME does take ages to load, compared to KDE4.

---

### Post by Sashin on 2009-06-07
Hopefully that'll be solved with gnome 3, and that gnome shell will be a completely optional thing or it'll be improved upon infinitely.

Compiz already does alot of that fancy stuff with a plugin called expo.

---

