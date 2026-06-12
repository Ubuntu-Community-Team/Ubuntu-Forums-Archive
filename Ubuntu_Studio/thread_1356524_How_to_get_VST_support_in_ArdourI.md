---
title: "How to get VST support in Ardour?I"
date: 2009-12-16
forum: Ubuntu Studio
---

### Post by JohneG on 2009-12-16
I am not very technical with Linux. I am very much a user end person. I have read up a bit about compiling Ardour with VST support but it's going over my head. Is there any easy way to do this or could someone break it down for me so it's easier to understand? Is it a big job? Any help appreciated. Thank you

---

### Post by sgx on 2009-12-16
> **JohneG said:**
> I am not very technical with Linux. I am very much a user end person. I have read up a bit about compiling Ardour with VST support but it's going over my head. Is there any easy way to do this or could someone break it down for me so it's easier to understand? Is it a big job? Any help appreciated. Thank you
Don't bother, as the support, when it arrives, will be too limited for serious audio production. The author is not creating a vst host.

...but, Reaper using WINE, with wineasio is a good way to go. Reaper allows you to load multiple vst instruments, fx, and audio files, and is fine for basic multi-track recording in linux.

Also, for single vsts, the fst command can use WINE/wineasio to open a plugin, but you need plugins that have their own preset browsers if you go that route.

LMMS is getting close to usability, and no doubt will work sometimes for some plugins, but they are not a sales-funded commercial business like Reaper, so progress is slow in comparison. 

Plugins requiring a dongle, pace, ilok, or complex challenge-response schemes won't work.

Native Instruments, Zebra, AlgoMusic, EZDrummer/Addictive Drums/Drumcore, Wusikstation, and most free or small-developer plugins will work, so really, the sky is the limit! You can mix/route the Reaper output with
most native linux apps, so I use Hydrogen drum machine and rakarrack multi-fx along with Reaper hosted plugins, and record it all at once using timemachine, then you can load it in audacity or ardour or jamin for more tweaks/conversions etc

Cheers

---

