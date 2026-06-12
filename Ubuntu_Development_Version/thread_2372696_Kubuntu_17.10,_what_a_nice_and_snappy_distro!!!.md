---
title: "Kubuntu 17.10, what a nice and snappy distro!!!"
date: 2017-09-28
forum: Ubuntu Development Version
---

### Post by Chanath on 2017-09-28
Decided to download Kubuntu 17.10 daily. Played with other derivatives, why not Kubuntu? What a nice surprise! 
Have a look at the screenshot below. Ram use on idle. 347.7 MiB! 
(Or 365MB.)

A fully fledged desktop. And, a snappy one.
KDE has gone much much further in development.:)

---

### Post by Chanath on 2017-09-28
Had been using Kubuntu for work last  6 hours. Had no problem. *Most interesting is the idle usage, 0.35MB.* Not even Xubuntu came near that! A fully fledged DE with so little idle ram usage!

Dolphin is a very nice file manager, maybe the best GUI one out there. Only you are not allowed to open it as root. Well, I can use MC for that -- the best file manager I ever known. I always have MC installed in every install.  

There had been lot of talk about Kubuntu being faster in many comments in Ubuntu related websites. I didn't believe how snappy Kubuntu is, until yesterday. And, I'm glad I installed it.

---

### Post by vasa1 on 2017-09-28
> **Chanath said:**
> ...
Dolphin is a very nice file manager, maybe the best GUI one out there. Only you are not allowed to open it as root. ...
You maybe interested in a post over at the Kubuntu forums indicating that there'll be some sort of provision made to address that issue: [https://www.kubuntuforums.net/showthread.php/72427-kdesudo-not-working?p=405199&viewfull=1#post405199](https://www.kubuntuforums.net/showthread.php/72427-kdesudo-not-working?p=405199&viewfull=1#post405199)

---

### Post by SeijiSensei on 2017-09-28
I can open dolphin as root from the terminal in 14.04 which uses KDE4.  Have the developers removed that ability in KDE5?

---

### Post by mc4man on 2017-09-28
> **SeijiSensei said:**
> I can open dolphin as root from the terminal in 14.04 which uses KDE4.  Have the developers removed that ability in KDE5?
[https://cgit.kde.org/dolphin.git/commit/?id=0bdd8e0b0516555c6233fdc7901e9b417cf89791](https://cgit.kde.org/dolphin.git/commit/?id=0bdd8e0b0516555c6233fdc7901e9b417cf89791)

---

### Post by Chanath on 2017-09-28
I shouldn't have commented on "Dolphin not opening as root." *It does not matter.* [B]What matters is that while idling, it takes only 0.35 GB ram! 
[/B]Gnome takes 1.1 GiB and Unity only 1.0 GiB.
This is KDE 5...and, it is snappy!

---

### Post by Chanath on 2017-10-01
Well, installed Kubuntu daily of 1st October in a UEFI laptop.
Just can't believe what I see; Kubuntu uses *only *380 MB in idle mode. Without System Monitor, it might be even less.
Its less than even what Lubuntu or Xubuntu. Nothing much to say about Gnome, which takes 1.1GB!!!

Kubuntu being fully fledged distro, without the need of any extensions, tweak tools etc, idling at just 380 MB is amazing!

---

### Post by Scott Deagan on 2017-10-09
I switched to Kubuntu after Canonical announced it was ditching Unity, and am really glad I did! I'm not really a distro-hopper, so will probably stick with Kubuntu for the foreseeable future. I tried Gnome, and just didn't like it (found it quite awful, if I'm to be honest).

Kubuntu, FOR THE WIN! ->

[https://www.youtube.com/watch?v=TGnzJ7SH2u0](https://www.youtube.com/watch?v=TGnzJ7SH2u0)

[https://www.youtube.com/watch?v=64Nmvf-d-2c](https://www.youtube.com/watch?v=64Nmvf-d-2c)

[https://www.youtube.com/watch?v=4vjQiZAKZW8&t=17s](https://www.youtube.com/watch?v=4vjQiZAKZW8&t=17s)

Really looking forward to 17.10 final :)

---

### Post by VMC on 2017-10-10
> **Chanath said:**
> Well, installed Kubuntu daily of 1st October in a UEFI laptop.
Just can't believe what I see; Kubuntu uses *only *380 MB in idle mode. Without System Monitor, it might be even less.
Its less than even what Lubuntu or Xubuntu. Nothing much to say about Gnome, which takes 1.1GB!!!

Kubuntu being fully fledged distro, without the need of any extensions, tweak tools etc, idling at just 380 MB is amazing!

That's not what I'm seeing on my system:
```
===**xubuntu**===$ grep -iE 'MemTotal:|MemFree:'  /proc/meminfo
MemTotal:        3788344 kB
MemFree:         [COLOR=#008000]**2709496**[/COLOR] kB
==
$ free -m
              total        used        free      shared  buff/cache   available
Mem:           3699         [COLOR=#008000]**312**[/COLOR]        2645          15         741        3121
Swap:          1999           0        1999
==
$ vmstat -s|grep -E 'total memory|used memory'
      3788344 K total memory
       324072 K used memory
==
Htop reports:
Mem [COLOR=#008000]**346M**[/COLOR]/3.61G


===**kubuntu**===
$ free -m
              total        used        free      shared  buff/cache   available
Mem:           3696         [COLOR=#008000]**597**[/COLOR]        2602           5         496        2881
Swap:          1999           0        1999
==
vmstat:
 
    3785248 K total memory
       [COLOR=#008000]**611280**[/COLOR] K used memory
==
top reports:
used memory [COLOR=#008000]**658588**[/COLOR]
```

In distant past, I was able to use kubuntu with nouveau. Not anymore. I need to install nvidia-legacy for it to even boot to the desktop. Also Plasma takes a long time to finish.

---

