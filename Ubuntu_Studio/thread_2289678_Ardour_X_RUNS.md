---
title: "Ardour X RUNS"
date: 2015-08-06
forum: Ubuntu Studio
---

### Post by Ian DR Kirk on 2015-08-06
Hi I'm running US 15.04 fresh install on a intel i5 CPU with Harrison Mixbus 3 (fresh install). Jack is 256 frames, 48000 Hz, 3 Periods via firewire to a MOTO 8pre. linux-lowlatency (3.19.0.25.24) ... and I am in the user group. Big problem is that I still get xruns and Mixbus stalls for a moment. It's just the occasional xrun but it makes you feel a little nervous when recording. Can anyone give me some direction in how to solve this? I know the same problem has been posted before but I would have thought that after all this time the issue would have been resolved.

cheers

Ian

---

### Post by CrocoDuck on 2015-08-06
Hi Ian!

> **Ian DR Kirk said:**
>  ... and I am in the user group. 

Maybe you meant the audio group? Make sure you are in the audio group.

> **Ian DR Kirk said:**
> I would have thought that after all this time the issue would have been resolved.

the issue... Unfortunately it is not one and single one issue. The problem is that any system has a different likelihood to develop XRUNS, depending on hardware and OS configuration. For example, with my laptop (Compaq Presario CQ 61) it has always been a pain to get good performances because the messy USB hardware implementation. That is why I had to achieve a [pretty extreme configuration]("http://www.linuxmusicians.com/viewtopic.php?f=19&t=10837"). The page I linked should contain a lot of good references to point you to the direction of proper Linux pro-audio configuration. I especially recommend [this]("http://wiki.linuxaudio.org/wiki/system_configuration"), give a go to Quickscan and avoid the part about kernels at first. If after all the configuration you feel you need a real-time kernel maybe you are better to get one from [KXStudio]("http://kxstudio.net/"). Also, [this]("http://www.linuxmusicians.com/viewtopic.php?f=19&t=9666") could be interesting for you.

Hope it helps!

---

### Post by Ian DR Kirk on 2015-08-09
Thanks Croco Duck. I installed GIT ran a scan and am now dealing with issues one by one. It seems a significant problem though was set to "powersave". I've reconfigured to "performance" and am now testing. The other major issue seems to to be; "Real-Time Preemption... not found - not good" so I'm going to deal with that now.

Thanks again.....enjoy your coffee

Ian

---

