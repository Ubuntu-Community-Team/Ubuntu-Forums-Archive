---
title: "Yakkety vs Xenial"
date: 2016-07-08
forum: Ubuntu Development Version
---

### Post by QDR06VV9 on 2016-07-08
How many testers have noticed a big improvement with Yakkety over Xenial.
This is my view:
1.Speed big improvement
2.form and function..big improvement
3.Lags and other oddities..Gone 
Just curious if you see as big of an improvement as I have.:popcorn:
Specs and Sources I am using:
```
$ inxi -Sr
System:    Host: me-M61SME-S2 Kernel: 4.4.0-28-lowlatency x86_64 (64 bit)
           Desktop: MATE 1.14.1  Distro: Ubuntu 16.10
Repos:     Active apt sources in file: /etc/apt/sources.list
           deb http://us.archive.ubuntu.com/ubuntu/ yakkety main restricted
           deb http://us.archive.ubuntu.com/ubuntu/ yakkety-updates main restricted
           deb http://us.archive.ubuntu.com/ubuntu/ yakkety universe
           deb http://us.archive.ubuntu.com/ubuntu/ yakkety-updates universe
           deb http://us.archive.ubuntu.com/ubuntu/ yakkety multiverse
           deb http://us.archive.ubuntu.com/ubuntu/ yakkety-updates multiverse
           deb http://us.archive.ubuntu.com/ubuntu/ yakkety-backports main restricted universe multiverse
           deb http://security.ubuntu.com/ubuntu yakkety-security main restricted
           deb http://security.ubuntu.com/ubuntu yakkety-security universe
           deb http://security.ubuntu.com/ubuntu yakkety-security multiverse
           deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
           Active apt sources in file: /etc/apt/sources.list.d/flexiondotorg-ubuntu-telegram-yakkety.list
           deb http://ppa.launchpad.net/flexiondotorg/telegram/ubuntu yakkety main
           deb-src http://ppa.launchpad.net/flexiondotorg/telegram/ubuntu yakkety main
           Active apt sources in file: /etc/apt/sources.list.d/flexiondotorg-ubuntu-youtube-dl-gui-yakkety.list
           deb http://ppa.launchpad.net/flexiondotorg/youtube-dl-gui/ubuntu yakkety main
           deb-src http://ppa.launchpad.net/flexiondotorg/youtube-dl-gui/ubuntu yakkety main
           Active apt sources in file: /etc/apt/sources.list.d/graphics-drivers-ubuntu-ppa-yakkety.list
           deb http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu yakkety main
           Active apt sources in file: /etc/apt/sources.list.d/noobslab-ubuntu-themes-yakkety.list
           deb http://ppa.launchpad.net/noobslab/themes/ubuntu yakkety main
           Active apt sources in file: /etc/apt/sources.list.d/vertex-theme.list
           deb http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_16.04/ /


```

---

### Post by ventrical on 2016-07-08
I don't have a yakkety MATE desktop yet but it is very performance friendly on ubuntu-desktop and unity8.

Regards..

---

### Post by PJs Ronin on 2016-07-08
I've been saving a 'system-analyze' test to a log file since Vivid... when I remember, is not auto, as some folks on here were lauding fast boot times and my system seemed to be a dog.   My yakkety partition is simply a cloned xenial partition with a dist-upgrade.   Today's results:
```
Sat 09 Jul 2016 10:06:26 AWST xenial Startup finished in 6.304s (kernel) + 2.199s (userspace) = 8.503s
Sat 09 Jul 2016 11:30:02 AWST yakkety Startup finished in 6.565s (kernel) + 2.401s (userspace) = 8.967s
``` So for me, yakkety is not yet pushing boundaries.   I've also noted that since Trusty each dist-upgrade has been the height of boredom with only a few minor glitches.   Then again, I don't push the envelope like others do.

---

### Post by rrnbtter on 2016-07-09
Greetings,
It borders on greatness! I using Yakkety on a 2007 L305 Toshiba Laptop. Performance is top notch. I am also running Xenial on a 2009 10" Toshiba Netbook which has a SSD installed and RAM maxed at 2gig. This is also performing better than when new. I'm already keeping up with Unity 8 on this Laptop and am hoping for enough "click" to not need a touch screen replacement. Overall, an enjoyable time to be a Linux user. Even on old junk.

---

### Post by ventrical on 2016-07-09
> **rrnbtter said:**
> Greetings,
It borders on greatness! I using Yakkety on a 2007 L305 Toshiba Laptop. Performance is top notch. I am also running Xenial on a 2009 10" Toshiba Netbook which has a SSD installed and RAM maxed at 2gig. This is also performing better than when new. I'm already keeping up with Unity 8 on this Laptop and am hoping for enough "click" to not need a touch screen replacement. Overall, an enjoyable time to be a Linux user. Even on old junk.

I just did an upgrade using the auto upgrader notification. from wily to xenial (ubuntu-desktop). There have always been issues previously. This time it looks like they got it right.  Xenial running much faster on old machine than wily did. Great work !



Regards..

---

### Post by sudodus on 2016-07-09
Lubuntu Yakkety is no longer affected by some long lasting bugs, that are affecting Xenial, so yes, I agree that Yakkety is a big improvement. But there is still a long ride until il will be released in October. Let us hope that new versions of the kernel and several upstream packages will work well together :-)

---

### Post by sudodus on 2016-07-09
> **ventrical said:**
> I just did an upgrade using the auto upgrader notification. from wily to xenial (ubuntu-desktop). There have always been issues previously. This time it looks like they got it right.  Xenial running much faster on old machine than wily did. Great work !



Regards..

That's great news :-)

I also hope that several bugs will be squashed or worked around in the first point release 16.04.1 LTS. I think this is important particularly for Lubuntu.

---

### Post by ventrical on 2016-07-09
> **sudodus said:**
> That's great news :-)

I also hope that several bugs will be squashed or worked around in the first point release 16.04.1 LTS. I think this is important particularly for Lubuntu.

That's why I did the upgrade :)
Regards..

---

### Post by ventrical on 2016-07-09
Ok.. and now a wily ubutnu-gnome to a xenial ubuntu-gnome using automated upgrade manager.

@runrickus

Don't want to hijack your thread. Don't want to hijack the other thread. Don't want to start a new thread  because of dupes.   so I'm just leaving this stuff here because I'm on a roll and you can move it later.

Thanks..

Regards..

---

### Post by mc4man on 2016-07-09
> **PJs Ronin said:**
> I've been saving a 'system-analyze' test to a log file since Vivid... when I remember, is not auto, as some folks on here were lauding fast boot times and my system seemed to be a dog.   My yakkety partition is simply a cloned xenial partition with a dist-upgrade.   Today's results:
```
Sat 09 Jul 2016 10:06:26 AWST xenial Startup finished in 6.304s (kernel) + 2.199s (userspace) = 8.503s
Sat 09 Jul 2016 11:30:02 AWST yakkety Startup finished in 6.565s (kernel) + 2.401s (userspace) = 8.967s
``` So for me, yakkety is not yet pushing boundaries.   I've also noted that since Trusty each dist-upgrade has been the height of boredom with only a few minor glitches.   Then again, I don't push the envelope like others do.
Not sure that start up times reflect 'performance' but in that regard & overall don't see 16.10 being any better or worse than 16.04 (fresh installs of both.
Start up here is fast, actual time from power up to usable dsktop is a bit quicker than reported. (- More like about 4.5 sec

> $ systemd-analyze
Startup finished in 1.697s (firmware) + 2.267s (loader) + 1.941s (kernel) + 1.316s (userspace) = 7.222s

A plot shows firmware & loader as 'negative' times, don't quite get that. kernel is at 0.0 s  in the plot..
(- to try 
systemd-analyze plot > 1.svg

Both 16.10 & 16.04 get these occasional 90 sec time outs on restarts for some stop job or another, think I'll set the timeout to 10 sec as nothing is happening during the 90 secs so having nothing happen for 10 secs can't be any worse.

---

### Post by fjgaude on 2016-07-09
Pray tell, mc4man, how do you change timeout to 10sec?

Thanks,

frank

---

### Post by QDR06VV9 on 2016-07-09
> **ventrical said:**
> Ok.. and now a wily ubutnu-gnome to a xenial ubuntu-gnome using automated upgrade manager.

@runrickus

Don't want to hijack your thread. Don't want to hijack the other thread. Don't want to start a new thread  because of dupes.   so I'm just leaving this stuff here because I'm on a roll and you can move it later.

Thanks..

Regards..
No worries Vent that was the purpose of this Thread:D
It was growing stagnant here.
But this proving to be a better user experience at least for me. So I am getting ready for the first point release of Xenial.
Kind Regards and thanks for the reply's to all.

---

### Post by mc4man on 2016-07-09
> **fjgaude said:**
> Pray tell, mc4man, how do you change timeout to 10sec?

Thanks,

frank
I did it months ago on the install I just removed & forgot to get or look at the file. It can be adjusted here - 
/etc/systemd/system.conf

I believe the line would be this one,at least for some instances of stop jobs 'hanging'  - 
#DefaultTimeoutStopSec=90s

What I forget was whether it needed to be uncommented, I'll assume it does so am setting to this here & will wait for the next shutdown/restart hang & see if it goes 10 or 90 sec
DefaultTimeoutStopSec=10s

References - 
[https://www.freedesktop.org/software/systemd/man/systemd-system.conf.html](https://www.freedesktop.org/software/systemd/man/systemd-system.conf.html)

---

### Post by fjgaude on 2016-07-09
Okay, just changed it to 10sec. Will see what happens in a couple of reboots.

Thanks!

---

### Post by fjgaude on 2016-07-09
It shut down in less than 2sec. So it might be working. Over time we'll see.

---

