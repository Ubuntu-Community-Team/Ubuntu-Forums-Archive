---
title: "Xen &amp; MythTV"
date: 2008-06-20
forum: Virtualisation
---

### Post by Contrarian on 2008-06-20
I instaled MythBuntu on an AMD 1700 chip and all seems to be working fine.  I then installed the xen server and now the video is horrific.  While the audio is still real time, i've gone from 30fps to about 1fps.  

Is this to be expected and should I just ditch xen and put it on a diferent box or are there areas I could look into tweaking.

---

### Post by hurenkam on 2008-06-25
Hi,

What exactly are you trying to do with your system (record/playback/both)? 

I'm currently running a Xen server based on an AMD 1200 Duron platform, which has a mythbackend running in a DomU. This is working fine for me, with 2 tuners recording in parallel. I am using a seperate pc as frontend.

If you are trying to use your box as a frontend you should probably look into your X settings & graphics acceleration. The nvidia kernel module for instance does not work 'out of the box' with xen (some patches can be found on the net though).
Probably you should also look at the preemptive scheduling options in your kernel configuration.

Regards,
Mark.

---

