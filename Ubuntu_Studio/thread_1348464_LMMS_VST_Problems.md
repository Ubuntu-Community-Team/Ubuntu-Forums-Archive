---
title: "LMMS VST Problems"
date: 2009-12-07
forum: Ubuntu Studio
---

### Post by rossco_50 on 2009-12-07
Hi,

I recently installed Unbuntu Studio Karmic and have been successfully using a number of windows VSTs (that I can't live without at the moment) under VSThost and the latest wine (ubuntu repository) and wineasio. However, I would prefer a more integrated solution.

I then saw that LMMS seems to normally have good integrated support for VSTs through the vestige plugin. I have installed LMMS-VST through synaptic. I set up the VST folder in LMMS and I am able to insert Vestige in a track. Audio output is set to Alsa and I have removed pulse audio.

All VSTs that I have tried to load crash the system. This includes those that were working with VSThost and some that are reported to work well with LMMS e.g. MDA Piano. I get a message saying "please wait loading plugin", but the system freezes.

Dave Philips reported similar but much less severe behaviour with a fairly recent version of LMMS in his linux journal review. Many others report fully functioning VSTs. Can anyone help? Is the LMMS package installed by default compiled for VST usage? I am really keen to get it going.

Thanks,

Ross

---

### Post by sgx on 2009-12-07
Hi, reaper and wineasio are the best combo for vsts, lmms I would try with
zynaddsubfx, rakarrack, hydrogen drum machine, and other linux native apps, but if there is any hint of buggy behaviour, just run them alone, they can be running along with wine in qjackctl, the whole lot recorded with timemachine.
Cheers

---

### Post by DerickX on 2009-12-07
What are the VST plugins you can't live without with?

For piano I recommend LinuxSampler with the maestro piano gig file. Or pianoteq.

For drums hydrogen 0.9.4, buy some quality samples with it

Did you try the latest zynaddsubfx for more sounds?

I don't use LMMS myself, but I think Qtractor is more valuable in the long run for you on Linux...

You can run VST for example with FST or dssi-vst


see also: [http://ubuntuforums.org/showthread.php?t=1348391](http://ubuntuforums.org/showthread.php?t=1348391)

---

### Post by rossco_50 on 2009-12-08
Thanks for the responses. However, my post was in the hope that I could get LMMS working the way it is reported to, rather than have to accept it doesn't work and look for alternatives - which seems to be the advice from your posts. 

Is LMMS-VST in the repositories broken or is it just me?

I have already tried qtractor, and again I really like the application, especially the integration of automatic tempo synced rubberband and jackctl. However, DSSI-VST does not seem to be installing easily on 9.10 and I have yet to be able to get vsts running within it. It may be the version of wine, so will try another later. The problems Im having with LMMS and Qtractor could well be related.

Thanks,

Ross

---

