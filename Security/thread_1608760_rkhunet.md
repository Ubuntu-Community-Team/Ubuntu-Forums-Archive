---
title: "rkhunet"
date: 2010-10-29
forum: Security
---

### Post by spillage2 on 2010-10-29
Hi All,

I have just run rkhunter and had this warning:

[18:02:57] Warning: Suspicious file types found in /dev:
[18:02:57]          /dev/shm/pulse-shm-1178251524: data
[18:02:57]          /dev/shm/pulse-shm-127737491: data
[18:02:57]          /dev/shm/pulse-shm-1066142079: data
[18:02:57]          /dev/shm/pulse-shm-1619952623: data

I cannot open then in gedit as unable to detect the chartacter encoding. 

How concerned should I be. I dont want to jump in and delete them and end up messing up my o/s.

Cheers,

Spill.

---

### Post by Rubi1200 on 2010-10-29
Warnings are just that; warnings. It means you need to do some research and find out if this is a threat or not.

In this case, I can put your mind at ease and tell you that this is quite normal.

pulse: 
> PulseAudio, previously known as Polypaudio, is a sound server for POSIX and
WIN32 systems. It is a drop in replacement for the ESD sound server with
much better latency, mixing/re-sampling quality and overall architecture.

Please also read this:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

and this:
[http://ubuntuforums.org/showpost.php?p=9265649&postcount=8](http://ubuntuforums.org/showpost.php?p=9265649&postcount=8)

especially this part:
> Warnings are exactly that, warnings and not necessarily problems. You  should not either panic or ignore them, you should investigate to see if  they are "normal" for your system.

> Google search any warnings or alerts.

---

