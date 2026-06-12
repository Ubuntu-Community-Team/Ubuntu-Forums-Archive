---
title: "Ubuntu on old desktops"
date: 2006-10-22
forum: The Cafe
---

### Post by Gargamella on 2006-10-22
i have an old desktop originally windows98 (64 MB ram Pentium Celeron 400 MHz)

so it is preistoric but because off i need it to use in wifi i had to bring it in Winxp for drivers incompatibility.

It's slow ... slow............................
slow.............................................
.................................................slow

but usefull to browse the internet and to download/upload

i would like to install a linux ( ubuntu if possible ) in it... but if the hardware is old i have to use an old linux release? or it is quite the same and it will detect its possibility?

---

### Post by Albi on 2006-10-22
Give it around 128mb more of ram and you should be able to install xubuntu on it

However, that's really slow, and the best option would be to do a server install and fluxbox:
[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)
or IceWM
[https://help.ubuntu.com/community/IceWM?highlight=%28IceWM%29](https://help.ubuntu.com/community/IceWM?highlight=%28IceWM%29)

See this:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by anaconda on 2006-10-22
You might want to try some light linux distributions.
puppy linux
and
DamnSmallLinux (DSL)

are among the lightest. I like DSL more, but puppy is much easier for new users.

Even if you install a heavier os, you might want to have a light one for surfing the web etc..

---

### Post by Gargamella on 2006-10-22
thank you for linking

i know it is slow...but you know that i am using XP on it...
so should i install the last version of xubuntu? (this i had not understand)

---

### Post by Albi on 2006-10-22
> **Gargamella said:**
> thank you for linking

i know it is slow...but you know that i am using XP on it...
so should i install the last version of xubuntu? (this i had not understand)

Xubuntu might STILL be too slow for you

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Is the best guide to follow

And usually, the newer versions of linux won't mean it doesn't detect your hardware good, but if you want an older one, Damn Small Linux uses the 2.4 kernel and it's much lighter.

---

### Post by Gargamella on 2006-10-22
from [www.xubuntu.org](www.xubuntu.org)

Recommended Minimum Requirements

To run the Desktop CD at least 128 megabytes of RAM is required. To use the installed system at least 64 megabytes of RAM is required but 128 is recommended. At least 1.4 gigabytes of disk space is required. 

the very important thing is the wireless pci card, a Vivanco one
which i added this year.

so i have to find if it is compatible...may i would try it with the live cd.

might be a good idea?

---

### Post by Albi on 2006-10-22
yes, that's a good idea, however, the live cd will be VERY slow on that computer.  i had one with double that (800mhz/128mb ram) and it took over a minute to start up firefox, but you should definitely do it before installing

---

### Post by Gargamella on 2006-10-22
so let it be ;D but i need to test the wireless if it does not work i will not pass to linux with that pc

---

### Post by IYY on 2006-10-22
It's all about the window manager/DE. IceWM, Fluxbox and even XFCE are good choices.

---

### Post by PatrickMay16 on 2006-10-22
Fackin' back through time at 300,000 years per minute. 

I suggest that you add a bit more RAM if possible, like someone else said. Then, do an Ubuntu server install and use apt-get to install x-window-system-core, icewm or another light window manager, and whatever applications you'd like to use. Also you could try turning off font anti-aliasing and turning off unneeded services (sysv-rc-conf, which is in the repositories, is great for this).

---

### Post by bionnaki on 2006-10-22
I dont recommend xubuntu. your computer will run very slow.

you need either a ubuntu server install + a minimal desktop environment like icewm or openbox or fluxbox. or you need to just use DSL.

---

### Post by Gargamella on 2006-10-22
trust me,i am not searching for the fastest but i need the sure hardware compatibility and i can test by xubuntu live cd.

so take it easy ;D

however thank you everyone for the ideas

---

### Post by lapsey on 2006-10-22
What's the point of compatible hardware that takes an age to do anything?



I have a very nice icewm setup running on 128 Mb / 300Mhz.

I just install server (not LAMP) and then put ```
sudo apt-get -y install x-window-system-core icewm menu xterm gtk2-engines-ubuntulooks tangerine-icon-theme
```

This will give you icewm-session to run plus the ubuntu icon theme & ubuntu style widgets (I also like to use this with the 'IceBuntu' icewm theme) :cool:

Everything else can be installed later. 

and it barely uses any of the memory or cpu. You couldn't use firefox with that little memory, though.

---

### Post by Gargamella on 2006-10-23
there is no problem:
i didn't know if to use an old or a new release,because it isn't all old hardware (there's a wifi card pci too)

so i will try xubuntu live cd. 

that's all ;D

---

### Post by mips on 2006-10-23
Gargamella has obviously made up his mind and wants Xubuntu.

If he wants to run Xubuntu and have a slow system then so be it, it his his choice. You have provided Gargamella with good advice on light WMs and adding a bit of ram so you have done your part.

You can lead a horse to water, but you can't make him drink...

---

