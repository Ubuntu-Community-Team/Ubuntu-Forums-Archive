---
title: "three monitors"
date: 2010-01-18
forum: System76 Support
---

### Post by johnmata on 2010-01-18
hello,

i have a System76 model RAT-V2.  I have been running two monitors for a long while.  I have now tried to add a third monitor, in doing so I installed a second video card.  upon boot up the third monitor does not power up.  moreover, in the "display preferences" i can only see the two original monitors listed.

any help is greatly appreciated.

cheers,
john

---

### Post by thomasaaron on 2010-01-19
What kind of graphics card did you add? Does it have auxiliary power connectors on it? (Most beefier cards do.)

If it's an nVidia card, did you try going to nvidia_settings to see if the new card is detected? Display Preferences probably aren't adequate (depending on the version of Ubuntu you are running, which is?). How's that for a hosed sentence structure?

(Another consideration is that the RatV2 didn't have a very beefy power supply in it. What are the power requirements of the card you got?)

---

### Post by johnmata on 2010-01-19
hi,

the video card is a nvidia geforce 8400gs 512mb pci card.  i don't recall seeing an auxiliary power supply on it.

cheers,
john

---

### Post by slamhound on 2010-01-19
With 9.04, I had to run sudo nvidia-xconfig -a to get multiple gpus configured (I think the -a flag tells it to check all gpus).  There were a couple weird things that needed to be taken care of before this would work, but eventually it did.  Searching "nvidia-xconfig -a" on this forum and then looking at posts having to do with multiple gpus should detail the steps. I also set this up with 9.10 and I think that I had to do this step as well (though I can't remember for sure). 

Note that having two GPUs does cause some problems.  For instance, you either have to choose to have separate x-screens if you want compiz (which means no dragging across all three monitors; though can do 2 and 1 with twinview), or you have to enable xinerama, which allows for dragging windows across all three, but prevents you from using compiz.  I don't think there is any solution to this yet.

---

