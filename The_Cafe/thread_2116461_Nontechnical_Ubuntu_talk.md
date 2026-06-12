---
title: "Nontechnical Ubuntu talk"
date: 2013-02-15
forum: The Cafe
---

### Post by userfriendly1992 on 2013-02-15
Just curious, how has Ubuntu 12.10 been faring? Last time I was getting Ubuntu it wasn't to stable.

What bugs and stuff like that has it had? How is it different compared to other Ubuntu? How are you all enjoying it?

And good evening my Ubuntu family! :D

---

### Post by 3rdalbum on 2013-02-15
> **userfriendly1992 said:**
> Just curious, how has Ubuntu 12.10 been faring? Last time I was getting Ubuntu it wasn't to stable.

What bugs and stuff like that has it had? How is it different compared to other Ubuntu? How are you all enjoying it?

And good evening my Ubuntu family! :D

You've only been around since January so you wouldn't know this, but every version of Ubuntu has had a vocal minority of people saying "It's the buggiest version ever!". Do a Google search or an Ubuntu Forums search for "Ubuntu 8.04 buggy", "Ubuntu 9.04 buggy", "Ubuntu 9.10 buggy" etc.

12.10, although I haven't used it much (can't afford the bandwidth and time to upgrade to it on my own computers!), doesn't seem to have any widespread bugs. I mean, 8.04 had a known-buggy Atheros wifi driver, 9.04 had shocking Intel graphics performance, and 9.10 was slow to boot pretty much everywhere compared to the sheer boot speed of 9.04.

I only have two 12.10 criticisms:

1. The Dash is semi-transparent and "glassy" when there is any degree of 3D support on the GPU. On graphics cards that only have unofficial open-source drivers (for instance, legacy ATI graphics cards that have been abandoned by ATI), there may be just enough 3D support to run semi-transparency, but not enough for the Dash to open in less than ten seconds.

When there is barely any 3D performance on a graphics card, Unity should fall back to no semi-transparency like it does when there's absolutely zero 3D support.

Oh sure, you can change it manually in dconf, but only if you know it exists.

2. The Additional Drivers has been hidden inside the Software Sources program. Who would look for drivers in a program that lets you set up your repositories? Not me. A lot of people have complained "Why did they get rid of the Additional Drivers in 12.10" and a lot of new users have simply not realised that there are proprietary drivers for their graphics cards, because the control for it has been hidden in an illogical place.

Bring it back to a separate menu item on the Dash, please.

Otherwise, 12.10 seems fine. Not enough for me to want to upgrade to it, but I wouldn't think twice about loading it onto a new computer.

---

### Post by mamamia88 on 2013-02-16
You'll usually find a bug list published for most open source projects.   The best way to find out whether or not there is a bug that might effect you is to browse the bug reports here [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

---

### Post by grahammechanical on 2013-02-16
I tested (daily use) 12.10 during its 25 week development period. What caused the biggest problems for me was buggy Nvidia video drivers. I stopped using Nvidia drivers for that reason.

I do test installs and I never allow the installation of third party software during the Installation of Ubuntu because it brings in proprietary video drivers and I see that as being a risk of not getting to a working desktop.

I often see posts on other sections of this forum where people have problems getting to a working desktop and I put most of these issues down to using a proprietary video driver.

And for the record, Ubuntu 12.10 is the only Ubuntu at present (not counting 13.04) that stands any chance of installing on a machine with secure boot enabled. Issues with installing alongside Windows 8 are more often down to problems caused by Microsoft's partitioning schemes or people not doing sufficient research on how to avoid issues before trying to install 12.10. Those issues have been around since Windows 7 came on the scene.

Regards.

---

### Post by deadflowr on 2013-02-16
> **grahammechanical said:**
> 
And for the record, Ubuntu 12.10 is the only Ubuntu at present (not counting 13.04) that stands any chance of installing on a machine with secure boot enabled. Issues with installing alongside Windows 8 are more often down to problems caused by Microsoft's partitioning schemes or people not doing sufficient research on how to avoid issues before trying to install 12.10. Those issues have been around since Windows 7 came on the scene.

Regards.

12.04.2 lts supports secure boot:
[http://fridge.ubuntu.com/2013/02/14/ubuntu-12-04-2-lts-released/]("http://fridge.ubuntu.com/2013/02/14/ubuntu-12-04-2-lts-released/")

That being said, I have no idea why people who don't know what their doing would ever want a dual-boot. I find it much easier to get a second hard drive and throw a distro on it. Go hogwild with it.

As for 12.10, it works, but I'm not one to recommend it. I'd rather recommend precise, or if newer is your thing raring.

---

### Post by PIE09gbLmgG6 on 2013-02-16
Had massive issues last year with 12.04...12.10 worked pretty good...it didnt break anything...lol...been running strong...

ego-

Ps. Trying to get my school district to make the switch...anyone know of a good place for stats on savings using ubuntu?

---

### Post by Peripheral Visionary on 2013-02-16
> **deadflowr said:**
> ... I have no idea why people who don't know what their doing would ever want a dual-boot. I find it much easier to get a second hard drive and throw a distro on it. Go hogwild with it.

Absolutely.  Dual-booting is high-risk for alot of new users.  Use an older computer or a different hard drive!

>  I'd rather recommend precise, or if newer is your thing raring.

I'll be sticking with LTS versions only until they reach end-of-life, for reasons of stability and because upgrading is hazardous for alot of people.  A fresh install of the next LTS when the old one reaches the end of it's support is always safest and least likely to mess up.

That's the non-tech users' way!

---

### Post by Linuxratty on 2013-02-16
> **Peripheral Visionary said:**
> 
I'll be sticking with LTS versions only until they reach end-of-life, for reasons of stability 

 Same here. For the most part,every version of Linux I've ever used (except Klikit) has been solid as a rock. Ubuntu is very stable for me.

---

### Post by deadflowr on 2013-02-16
> **Linuxratty said:**
> Same here. For the most part,every version of Linux I've ever used (except Klikit) has been solid as a rock. Ubuntu is very stable for me.

Definitely.

Sure I'll run newer versions here and there, but at the beginning of the day and end of the day, I'm an LTS user through and through.

Partly for its rock solidness, but mainly for my laziness in not wanting to upgrade so rapidly.
Three years without having to deal with edge of your seat nervousness was better than a year and a half, and now five years is even better.

---

### Post by mamamia88 on 2013-02-16
> **Peripheral Visionary said:**
> Absolutely.  Dual-booting is **high-risk** for alot of new users.  Use an older computer or a different hard drive!



I'll be sticking with LTS versions only until they reach end-of-life, for reasons of stability and because upgrading is hazardous for alot of people.  A fresh install of the next LTS when the old one reaches the end of it's support is always safest and least likely to mess up.

That's the non-tech users' way!

high risk?  maybe if you do manual partitioning and don't know what you are doing but if the Ubuntu installer detects windows it's as easy as it gets.   but yeah shrinking partitions always involves the potential of data loss.

---

### Post by Peripheral Visionary on 2013-02-16
Actually my partitions were set up already on this computer with Lucid.  When I installed Precise I left them the way they were.  I still have to "say so" manually when I install the next LTS, always from a LiveCD, never a 'net upgrade.

---

### Post by cariboo on 2013-02-16
> **egosophist said:**
> Ps. Trying to get my school district to make the switch...anyone know of a good place for stats on savings using ubuntu?

Have you contacted Canonical?

---

### Post by userfriendly1992 on 2013-02-16
I have really enjoyed Ubuntu 12.04. However, my graphics card perplexes me.. I am not sure if its the fact that its just a bad graphics card or if its not very compatible with Linux. I have an Intel Graphics Media Accelerator 3600. I can barely play Defcon, or 0 A.D. 

Anyone know anything about this?

---

### Post by userfriendly1992 on 2013-02-16
> **3rdalbum said:**
> You've only been around since January so you wouldn't know this, but every version of Ubuntu has had a vocal minority of people saying "It's the buggiest version ever!". Do a Google search or an Ubuntu Forums search for "Ubuntu 8.04 buggy", "Ubuntu 9.04 buggy", "Ubuntu 9.10 buggy" etc.

12.10, although I haven't used it much (can't afford the bandwidth and time to upgrade to it on my own computers!), doesn't seem to have any widespread bugs. I mean, 8.04 had a known-buggy Atheros wifi driver, 9.04 had shocking Intel graphics performance, and 9.10 was slow to boot pretty much everywhere compared to the sheer boot speed of 9.04.

I only have two 12.10 criticisms:

1. The Dash is semi-transparent and "glassy" when there is any degree of 3D support on the GPU. On graphics cards that only have unofficial open-source drivers (for instance, legacy ATI graphics cards that have been abandoned by ATI), there may be just enough 3D support to run semi-transparency, but not enough for the Dash to open in less than ten seconds.

When there is barely any 3D performance on a graphics card, Unity should fall back to no semi-transparency like it does when there's absolutely zero 3D support.

Oh sure, you can change it manually in dconf, but only if you know it exists.

2. The Additional Drivers has been hidden inside the Software Sources program. Who would look for drivers in a program that lets you set up your repositories? Not me. A lot of people have complained "Why did they get rid of the Additional Drivers in 12.10" and a lot of new users have simply not realised that there are proprietary drivers for their graphics cards, because the control for it has been hidden in an illogical place.

Bring it back to a separate menu item on the Dash, please.

Otherwise, 12.10 seems fine. Not enough for me to want to upgrade to it, but I wouldn't think twice about loading it onto a new computer.


Well, thats for this computer lol. I've actually ran Ubuntu, Lubuntu, Kubuntu, and some other distro that was made to look like windows xp but was linux. (Does anybody know the name of it is?) Anyways, this is just for my newest computer. :D I'm no extreme Ubuntu geek, but I'm not quite a newbie either. :)

---

### Post by 3rdalbum on 2013-02-17
> **userfriendly1992 said:**
> I have really enjoyed Ubuntu 12.04. However, my graphics card perplexes me.. I am not sure if its the fact that its just a bad graphics card or if its not very compatible with Linux. I have an Intel Graphics Media Accelerator 3600. I can barely play Defcon, or 0 A.D. 

Anyone know anything about this?

I'm sorry to let you know, this is a bad graphics chip with good Linux support. Not the other way around.

If you have a spare PCI-E slot you should be able to get a much better Nvidia card; even something like a GT620 would be far superior with only a little more electricity used.

---

