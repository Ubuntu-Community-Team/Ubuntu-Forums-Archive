---
title: "Audacity records once, but not twice, &amp; other problems"
date: 2008-05-23
forum: Ubuntu Studio
---

### Post by alanwalterthomas on 2008-05-23
Noob's first post:
RE: Audacity
I installed a[FONT=Arial]udacity using ubuntu's [/FONT](Hardy Heron 8.04 LTS) add/remove. For some reason it installed the 1..3.4 beta instead of the latest stable version. Is that normal, & could that be the source of the following problem?
I have already seen a lot of posts regarding "Error while opening sound device..." & this is one of them, but a little different because for me audacity "kinda" works.
When I record sound the following options for recording under preferences are available:

oss: dev/dsp
oss: dev/dsp1
ALSA: VIA 8235: VIA 8235: (hw:0,0)
ALSA: VIA 8235: VIA 8235: (hw:0,1)
ALSA: VIA 82xx modem: VIA 82xx modem (hw:1,0)
ALSA: default

& the following respectively happen:

Records without error message, but the sound is scratchy/tinny
Records without error message, but records nothing (flatline)
No go: "Error while opening sound device. Please check the input device..."
""
""
Records without error message, and audio is much higher quality. (I want this one to work)

My main problem is that with the 1st & last options I can record, but only once. If I stop then click to record again I get "Error while opening...". I can pause and restart, and I can record again if I delete the previous recording.
Can anyone explain what's going on and what I can do to fix this? Let me know if you need more information about my system. I'll try to dig it up. I don't have this problem of continuing a recording when I run audacity in Windows on this same system.
Thanks a lot for any help, I appreciate it.

---

### Post by chosenbeans on 2008-05-23
I just got on the forums to also seek this answer. I have the same problem. It seems when I first open audacity then hit record I can record and it sounds perfect but when I am done or when I click stop and try and record another track, it tells me error please check input devices and sampling rate.

I have just found audacity to be a great program for recording my music although this problem is a pain. Thanks for all who can help.

---

### Post by skullmunky on 2008-05-24
Try downloading the source from CVS and recompiling it.  It's real easy to do and, for me, solved a whole bunch of problems that the 1.3.4 Beta had with the sound devices.

---

### Post by alanwalterthomas on 2008-05-25
Thanks skullmunky, so compiling from source on the system I intend to use it on should help audacity deal with any specific issues I have, is that right? Problem is, I'm a noob. What's CVS, and how do I compile something? I'm sure it's easy to do, but I'm clueless. I compiled a webcam driver step-by-step and it works with funny colours, but if I had audacity's source code and tried to do anything I'd probably butcher it. 
Hold my hand anyone? :)
Thanks,

ALAN


P.S.
Again, what's with synaptic downloading the beta and not something that I can make work? Is there any way I can choose?

---

### Post by CrazyCanuck on 2008-05-26
I just downloaded the same package as the OP, and it is of course the same, the newest beta version instead of the more-stable previous release.  I have not tried opening any wav's yet, but at least it opened up just fine for me.  I am also interested in learning how to compile, so I suppose a trip to the Forum Search Engine is in order for both the OP and myself.  Yay!

CC

---

### Post by alanwalterthomas on 2008-05-30
Sorta Solved:
I made it work like this:
Download version 1.3.3 (instead of the one you download from the repositories)
I have the alsa0oss package installed, but I not sure if that makes a difference or not
In Audacity under preferences choose ALSA: default for both playback & recording
Under system-preferences-sound set Sound Capture: ALSA

I wish I understood what was going on, but it worked.

Thanks,

---

