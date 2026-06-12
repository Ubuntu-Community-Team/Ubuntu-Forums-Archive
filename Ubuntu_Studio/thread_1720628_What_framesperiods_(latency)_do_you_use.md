---
title: "What frames/periods (latency) do you use ?"
date: 2011-04-03
forum: Ubuntu Studio
---

### Post by fedexnman on 2011-04-03
using qjackctrl , what latency do you use , situations : #1 when recording live instruments with ardour . #2 hydrogen hooked up to ardour. ive been using 64 in the frames/periods setting in qjackctrl without any x-runs recoding live instuments , but in situation #2 i get x-runs , i wonder if i should be using 1024 frames/period with hydrogen and ardour hooked together ?

---

### Post by ailo.at on 2011-04-03
Whenever you need low latency, like when you play an instrument and want to monitor yourself, a low frames/period is of course preferred. In other cases, you could even use 4096.

If you need to use Hydrogen + Ardour and play an instrument live at the same time, you might want to try 128, or even 256. I think 128 should be good enough on most modern systems.

---

### Post by AutoStatic on 2011-04-04
#1 when recording live instruments with ardour.
Even though I don't use Ardour I use a fairly high number of frames/period to lower the chance of running into xruns (512 or 1024). For overdubs I use a lower number of frames/period of course (64 or 128, also depends on the number of mics).

#2 hydrogen hooked up to ardour.
As low as possible. I'm using 64 frames/period but Hydrogen 0.9.5 rc1 doesn't always like that. It's not that I get xruns but Hydrogen does seem more crash prone at lower latencies. Not sure if 0.9.5 performs better, still have to test.

Best,

Jeremy

---

### Post by rusk911 on 2011-04-04
I use 128 samples & 44100 Hz. With 64 samples Jack won't start on my notebook..

---

### Post by fedexnman on 2011-04-04
i have a firewire  audio device  , ill probably try the 128 frame/periods rate . its nothing crippling, still making music..  but i did notice  the older hydrogen, the one in the ubuntustudio 9.10 repos seemed to do better  with xruns   .  thx guys this has been helpful . :guitar:

---

### Post by zettberlin on 2011-04-04
> **fedexnman said:**
> using qjackctrl , what latency do you use , situations : 

#1 when recording live instruments with ardour . 

128/2/48KHz on a quadcore-workstation with OpenSuse+ Jengelh-RT-Kernel and MAudio PCI-Card.

128/3/48KHz on a T60-Thinkpad with Fedora14+CCRMA-Kernel
256/3/48KHz on a T60-Thinkpad with UbuntuStudio 10.10
both with MAudio Mobile Pre USB


> **fedexnman said:**
> 
#2 hydrogen hooked up to ardour. ive been using 64 in the frames/periods setting in qjackctrl without any x-runs recoding live instuments , but in situation 
#2 i get x-runs , i wonder if i should be using 1024 frames/period with hydrogen and ardour hooked together ?


Even under heaviest conditions with Hydrogen, Guitarix and AMS hooked to Ardour recordings 12 Tracks at the same time I never need to exceed F/P to more than 512. Most of the time I can run everything with settings for around 10ms Latency.

---

### Post by fedexnman on 2011-04-04
i have to rt- kernels  ubuntu studio  10.04 to choose from , had better luck today with the older one !!!

---

### Post by AutoStatic on 2011-04-05
Which ones are you referring too? I'd suggest trying the [Tango Studio]("http://tangostudio.tuxfamily.org/en/kernel-rt") one, works very well for me on all my systems (netbook, notebook, desktop) while I had some issues with the 2.6.31-rt kernel from the repo's.

Best,

Jeremy

---

### Post by fedexnman on 2011-04-05
gonna have to add that tango studio repo to my lucid install sweeet !!

---

