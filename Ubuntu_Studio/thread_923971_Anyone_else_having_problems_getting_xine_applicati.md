---
title: "Anyone else having problems getting xine applications to use pulseaudio's jack sink?"
date: 2008-09-19
forum: Ubuntu Studio
---

### Post by motin on 2008-09-19
In the beginning of August I had the sound from desktop applications including xine-based ones routed via pulseaudio through jack thanks to pulseaudio-module-jack and it was working great!

At some point or another thereafter this has stopped working! paplay can still output through the jack sink, but xine applications such as xine-ui and Amarok just won't play along any longer, complaining that the "device is busy" or similar. 

I just re-installed the system (leaving nothing but /home) using the latest Intrepid alpha and the problem persists...

I have heard that other's are experiencing problems with xine as well - anyone found a solution to this? Smells like some sort of regression in the xine packages...

Time for a bug report against xine you think? Since pulseaudio-module-jack is taken from debian, I'd guess that we'd need to report it against debian's or xine's bugtracker.

---

### Post by markbuntu on 2008-09-19
Well, I just checked and I am not having this problem. I have Amarok set up to use the xine engine pulseaudio output and the stream shows up just fine in PA Volume control and plays through the jack sink without any problem. My i386 system is fully updated from proposed. I have not tested this on my amd64 but will when I run it again.

I am not really sure that leaving your /home is a good idea when changing distros. There are a lot of setup default files in there. I have not moved to Intrepid yet, I am waiting for the ATI and Radeon drivers to be fixed.

---

### Post by leepesjee on 2008-09-19
No problem here also. I can play xine both directly through jack or through pulse-audio and the throug jack.

Have you set the audio driver in xine?

In Settings -> Setup (set experience level to at least "Advanced") -> Audio -> driver. May be worth a try.

---

### Post by motin on 2008-09-22
> **markbuntu said:**
> Well, I just checked and I am not having this problem. I have Amarok set up to use the xine engine pulseaudio output and the stream shows up just fine in PA Volume control and plays through the jack sink without any problem. My i386 system is fully updated from proposed. I have not tested this on my amd64 but will when I run it again.

I am not really sure that leaving your /home is a good idea when changing distros. There are a lot of setup default files in there. I have not moved to Intrepid yet, I am waiting for the ATI and Radeon drivers to be fixed.

Ok so it can work with a fully updated system - good to know! Keeping /home allowed me to reinstall and upgrade to Intrepid in less than 20min instead of having to configure everything again so it is a win, but you are right - maybe this is due to a user-related configuration issue. I have now moved my .asoundrc and .xine settings folders to a backup location and will now see if it works better...

> **leepesjee said:**
> No problem here also. I can play xine both directly through jack or through pulse-audio and the throug jack.

Have you set the audio driver in xine?

In Settings -> Setup (set experience level to at least "Advanced") -> Audio -> driver. May be worth a try.

Yeah I tried that, but it doesn't help unfortunately. :(

There seems to be a bug report about an identical issue: [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/176332](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/176332) , however that bug should already have been fixed - but apparently it's not...

Thanks for the feedback guys!

---

### Post by motin on 2008-10-06
> **Mark76 said:**
> since this isn't my thread I'll refrain from marking it solved

Happy your issue is solved. However, it is never polite to hijack threads like you did. Chances are that people skimming through this thread will mistake it for being solved, and then move on...

---

### Post by Stochastic on 2008-10-06
> **motin said:**
> Happy your issue is solved. However, it is never polite to hijack threads like you did. Chances are that people skimming through this thread will mistake it for being solved, and then move on...

Hijacker has been moved to his/her own thread in Mulimedia & Video forum.

P.S. my xine jack sink is working fine too, but I can't offer any advice on how to get yours solved.

---

### Post by motin on 2008-10-07
> **Stochastic said:**
> Hijacker has been moved to his/her own thread in Mulimedia & Video forum.

Thanks man!

> **Stochastic said:**
> P.S. my xine jack sink is working fine too, but I can't offer any advice on how to get yours solved.

Yeah my xine jack sink works acceptable (there is audio), except for the stuttering and delays... However, does your PulseAudio's JACK sink work fine? That's the sink that has stopped working for me...

---

### Post by markbuntu on 2008-10-07
I just got some long delayed updates to both xine and amarok and my jack-pulse sink is still working with the amarok xine plugin. You are not using Pulse 0.9.11 or 0.9.12 by any chance are you?
Intrepid comes with one of those I believe. I am still on hardy an pulse 0.9.10 and I probably will be for a while.

---

### Post by kayosiii on 2009-10-17
libxine->pulse->jack is just asking for pain.
If it were me I would cut out the middle-man

---

### Post by Stochastic on 2009-10-17
> **kayosiii said:**
> libxine->pulse->jack is just asking for pain.
If it were me I would cut out the middle-man

Yes, to clarify my earlier statement (though this thread is quite old now), I had xine hooked directly into Jack.  To do this I needed to recompile xine with the jack-dev libraries installed.  Why go through pulse if you don't need to?

Hopefully soon Jack will get back into Main repository and sound servers like xine and pulse will ship with the jack bridge compiled in by default.

---

### Post by kayosiii on 2009-10-17
> **Stochastic said:**
> Yes, to clarify my earlier statement (though this thread is quite old now), I had xine hooked directly into Jack.  To do this I needed to recompile xine with the jack-dev libraries installed.  Why go through pulse if you don't need to?

Hopefully soon Jack will get back into Main repository and sound servers like xine and pulse will ship with the jack bridge compiled in by default.

Yeah I hoping that happens too I am sick of recompiling everything for jack support every time I upgrade.

---

