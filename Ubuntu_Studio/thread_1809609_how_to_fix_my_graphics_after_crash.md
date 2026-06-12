---
title: "how to fix my graphics after crash"
date: 2011-07-21
forum: Ubuntu Studio
---

### Post by stephenstop on 2011-07-21
i have ubuntu studio 10.04 and my graphics crashed,i have a dual boot with windows xp with half memory and half memory in ubuntu studio.i am a newbie and need help please

---

### Post by stephenstop on 2011-07-21
and now when i run jack and record the cpu goes up to almost 100 percent,it was working great just last night,danggggggggggggggggggggggit!!!!!!!!!!!!!

---

### Post by jejeman on 2011-07-22
You should give more inforamtion about your PC, and what exactly happend.
What do you mean by "my graphics crashed"?

---

### Post by stephenstop on 2011-07-22
ok i just got a comp[uter(toshiba)(few weeks ago)and it had a dual boot with windows xp and ubuntu studio.everything was working good(i use jack to record into ardour and I use Hydrogen for the drums)There was an error about graphics x crash or something and it gave me a few options i picked restart and when it restarted the neato screen savers were not working and jack was not working normal anymore.
The only other thing I can think of is an update that went thru the same day(update manager)but I dont know really.
One dude named <henstein> had me apt get a rt kernel so when i reboot there are like 3 or 4 ubuntu and windows xp

????I really really need help

---

### Post by sgx on 2011-07-22
prepare to reinstall, but check for a file

/etc/X11/xorg.conf.old  (might be a slightly different path)

rename the file without the .old, and rename the current one xorg.bad
then reboot. If the update changed it, this should revert. You can
post them here, you may need a live cd to edit/copy them.

Cheers

---

### Post by stephenstop on 2011-07-22
oh im confused how do i do that?is a live cd putting ubuntu on a disc?sorry

---

### Post by zealibib slaughter on 2011-07-22
grab an iso image of ubuntu studio from their website and burn it with an iso burner in windows, you will need a dvd for studio. Then you can use the disk to start a live session of ubuntu, meaning the os loads from the dvd instead of the hard disk.

---

### Post by stephenstop on 2011-07-22
why?what will that do?

---

### Post by stephenstop on 2011-07-22
ok i found the file how do i rename it its xorg.conf.failsafe so i make it what?

---

### Post by stephenstop on 2011-07-23
So i renamed the file and i rebooted but i am having problems with jack that i didnt used to,and when I turn on guitarix it eats my cpu but i just got this comp. and it has ba duo centrino cp,is that normal?

---

### Post by sgx on 2011-07-23
> **stephenstop said:**
> So i renamed the file and i rebooted but i am having problems with jack that i didnt used to,and when I turn on guitarix it eats my cpu but i just got this comp. and it has ba duo centrino cp,is that normal?

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

at this wiki, these, and the other topics will help with jackd setup:

How to use the QjackCtl connections window

How to configure Jack in Ubuntu Studio

cpu scaling may be 'conserving' the power you need to use, read about
adjusting it here:

[http://ubuntuguide.net/change-and-monitor-cpu-frequency-scaling-in-ubuntu-11-04-with-indicator-cpufreq](http://ubuntuguide.net/change-and-monitor-cpu-frequency-scaling-in-ubuntu-11-04-with-indicator-cpufreq)

(never give up, we all are learning as we go!:D  )
Cheers

---

