---
title: "Slackware 12.....what happened?!"
date: 2007-07-18
forum: Slackware and derivatives
---

### Post by marsmissionaries on 2007-07-18
As much as i loved slackware 10, and 11, i just can't get over the fact that slackware 12...is just not living up to the slackware name. Normally slackware just works for me, so i thought "lets give slack 12 a try".

Not only was i upset that wpa support was absent by default (i tried miserably to fix that...i was not successful) but everytime i inserted a CD it gave me permission errors.


I never thought i would ever say this but, I like ubuntu more.

Has anybody else experienced any similar problems?

---

### Post by bonzodog on 2007-07-20
if you were used to slack 10 and 11, then you *should* be able to fix these minor things.

The CD thing is merely a case of changing mounting permissions in /etc/fstab. (hint -- try amending the words 'users' to the end of the CD/DVD mount line)

Slackware has **never** been for people who want everything to Just Work.

WPA is a little harder, but there are tutorials for using ndiswrapper with the card, or patching the kernel and configuring the system using iwconfig.

WPA does not even work out of the box with Zenwalk, normally classed as Slackware-for-beginners.

---

### Post by marsmissionaries on 2007-07-21
The point here is not that i could have fixed the problems, the point is, i shouldn't have had too. 

If slackware is ever going to compete with the more modern linux distributions it has the realise that there are things that should just work. Yes, WPA isn't something i would expect to just work on any operating system, however you can not advertise the new way of handling devices when it won't work out of the box.

I should not have had to do as much as I did.

And yes I do know that slackware has never been for people who want everything to just work, however everything before 12 has ALWAYS just worked, infact the point of simplicity is to maintain stability and it's ability to just work, this is why the 2.6 kernel didn't get used until slack 12.

---

### Post by fistfullofroses on 2007-07-28
Slackware was never meant to compete with other distributions. It is there as a Linux for very particular people. It is meant to be as Unix like as possible (and success was found considering that after a few minor tweaks I was able to install netbsd packages without a problem) using the Linux kernel. Slackware does not change much from distro to distro. Generally Patrick just updates all of the packages, and occasionally adds or removes a package. Other than that things have to be reworked when massive changes to the kernel are made. If you want things to just work, out of the box, stay with Ubuntu distro or similar. If you want a non-Unix Unix... choose Slackware.

---

### Post by Vague on 2007-07-28
Heh.  This kind of made me chuckle.  I mean, I can understand that frustration when things don't work, and everything "just worked" before, but. . . it's Slackware.

---

### Post by Bachstelze on 2007-07-29
Only thing on the down side for Slack 12 to me is that checkinstall no longer works due to a bug in the coreutils. Besides that, it's all good.

---

### Post by Motoxrdude on 2007-07-29
Wow dude, you can't have expectations when its **free**. I hear windows can get wpa working without a huge fuss, try that ;)

---

### Post by stmiller on 2007-07-30
> **marsmissionaries said:**
> 
Not only was i upset that wpa support was absent by default... 



Heh. It's Slackware. Everything is absent by default. You make it work the way you want it to. Slackware is a good no-fuss distro. It's one of the original Linux distros, so glad it's still around.

---

