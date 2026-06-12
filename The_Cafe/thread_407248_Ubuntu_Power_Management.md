---
title: "Ubuntu Power Management"
date: 2007-04-11
forum: The Cafe
---

### Post by GoHabsGo on 2007-04-11
I'm running Feisty beta, and Ubuntu is getting really impressive. Kudos to everybody in the community !!!! 

Honestly, the only thing that is keeping me away from using Ubuntu as my first OS is its power management. I'm on a HP TC440 Tablet PC and in Windows Vista, I get 2 hours in a half with power saving mode while in Ubuntu I get 1 hour 25 mins. Any development surrounding the gnome power management ? Are KDE or XFCE versions will give my  battery a longer charge  ?

Thanx.

---

### Post by hardyn on 2007-04-11
what video card?

only the binary ATI driver to my knowlege will underclock the video on battery, im not even sure that the intel driver does.  same can be said about the wireless cards, there is a script posed, but there are problems withing gnome that don't allow this script to work that well.

turing off the wireless on my notebook gives me 1:20min more than with it on!

that and suspend are issues that need to addressed in a dire sence of the word!

good luck.

---

### Post by PatrickMay16 on 2007-04-12
Try setting the screen brightness to a lower level. That will use less battery.

---

### Post by GoHabsGo on 2007-04-12
Thanx for your tips guys, but I wanted to know why using the same settings, the windows power manager is more efficient.

---

### Post by Polygon on 2007-04-12
windows power management is better for your laptop mostly beacuse the people who designed/made your laptop most likely used windows and optimized it / have support for windows power management 

and i know in edgy there were some significant improvements in power management, im sure the same thing will go for fiesty too once its released.

---

### Post by palmerthegeek on 2007-04-12
GoHabsGo...
I must say it's awesome to read this thread. I find it interesting how my dual-boot laptop performs relating to power management when I'm not in MSWinXP.

Have a great day!

---

### Post by prizrak on 2007-04-13
> **hardyn said:**
> what video card?

only the binary ATI driver to my knowlege will underclock the video on battery, im not even sure that the intel driver does.  same can be said about the wireless cards, there is a script posed, but there are problems withing gnome that don't allow this script to work that well.

turing off the wireless on my notebook gives me 1:20min more than with it on!

that and suspend are issues that need to addressed in a dire sence of the word!

good luck.

Intel GPU's don't support scaling at all as far as I know, unless it's 100% automatic and hidden even in Windows. At the same time they are not powerful enough to significantly drain the battery. 

> Thanx for your tips guys, but I wanted to know why using the same settings, the windows power manager is more efficient.
The most widespread cause is the video card. On Windows both nVidia and ATI allow for the video card to run slower on battery. On Linux the binary driver for ATI will allow for it but it has to be set manually and is not nearly as good. nVidia doesn't allow for underclocking at all. Also HP laptops have ACPI that is heavily in Windows favor it seems. I'm using an Acer Tablet that has an nVidia card and I only get 10 minutes less power in Ubuntu than I do in XP. I tested it on wired ethernet on both and Feisty had Beryl running. Wireless might yield different results because in Windows there are a bunch of options for the wireless card that deal with battery saving.

---

### Post by penno on 2007-04-27
Ah ok.It's a video driver thing. Dang, was hoping that the new "[tickless]("http://www.linux-watch.com/news/NS5286251174.html") [kernel]("http://lwn.net/Articles/223185/")" improvement in 2.6.21 might help with the big difference in power usage in ubuntu (vs windows). And I guess it will help, but sounds like it won't help *much*?

---

