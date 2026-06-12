---
title: "Audacity Records but Won't play"
date: 2008-09-10
forum: Ubuntu Studio
---

### Post by hookzilla on 2008-09-10
My Ubuntu Hardy installation is pretty much straight off the cd, plus all the available updates. I'm running Hardy on an older machine with an onboard audio system and a pci SB Audigy.   I use the Audigy because the line in on the O/B audio is blown. I loaded Audacity from the repository.  RythmBox plays well.  Audacity records well (though the input volume and balance controls have never worked) and used to play well. But now it won't play.  Audacity will not play on any of the several devices shown in the drop down list.  I did remove and reinstall Audacity, but that didn't change anything. I think (but am not sure) this started shortly after I tried an audio converter, which worked initially and then quit leading me to remove it.  I also did try Jack some time ago, but quickly removed it. I'm not sure where to start on this one.  Any suggestions will be a big help.

---

### Post by patchin_house on 2008-09-11
I think we all got a bad build this time around... has there been any news of progress
to fix the sound driver issue? If Audacity works well on other platforms, then there's no reason for us penguistas to be stuck like this.

Philip David
2008.09.11

---

### Post by paulmerchant on 2008-09-11
Three suggestions:

1. You might be able to get Audacity to work better by launching it with pasuspender (or anything else that helps force the sound output to something Audacity recognizes). From a terminal, type: pasuspender audacity. (Your mileage may vary.)

2. You can build a newer version of Audacity. The Audacity in the repos doesn't work well at all with Hardy. Yes, it's sad.

3. You can try another application. I gave up on Audacity in Hardy and started to use ReZound. It's actually quite good. If fact, until Hardy broke Audacity, I didn't even know that ReZound existed.

---

### Post by eye208 on 2008-09-12
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

---

### Post by shane2peru on 2008-09-19
> **paulmerchant said:**
> Three suggestions:

1. You might be able to get Audacity to work better by launching it with pasuspender (or anything else that helps force the sound output to something Audacity recognizes). From a terminal, type: pasuspender audacity. (Your mileage may vary.)

2. You can build a newer version of Audacity. The Audacity in the repos doesn't work well at all with Hardy. Yes, it's sad.

3. You can try another application. I gave up on Audacity in Hardy and started to use ReZound. It's actually quite good. If fact, until Hardy broke Audacity, I didn't even know that ReZound existed.

Thank you for this info!  I installed ReZound, and must say, I'm impressed.  Why is ardour soo complex and not user friendly???  Ahh, it gets on my nerves.  At any rate I'm really disappointed that Audacity is broken in Hardy!!! (Especially being a LTS version).  And doesn't look like it is going to be fixed.  I can't record through the mic with audacity. :(

Shane

**EDIT:**  Well, I guess I spoke too soon!  I tried the rezound, and it worked initially, but after trying to 'really' use it, it kept crashing on me.  :(   Oh well!  I was able to compile audacity, and it seems to work now that I have it compiled on my computer.

---

### Post by paulmerchant on 2008-09-20
Yeah, ReZound is still a fairly early beta and not nearly as mature as Audacity.

---

### Post by shane2peru on 2008-09-20
Looks as though it is going to have good potential though.  Audacity is my favorite, too bad they stuck us with a non-working version on a standard install.  That is the kind of things that drive me crazy.  Still better than windows though, at least I don't pay for these headaches. :)

Shane

---

### Post by eye208 on 2008-09-20
> **shane2peru said:**
> Audacity is my favorite, too bad they stuck us with a non-working version on a standard install.  That is the kind of things that drive me crazy.
Don't blame Audacity. PulseAudio is the part that's "broken" (i.e. not yet ready for prime time). If you suspend or remove it, Audacity will work just fine.

---

### Post by shane2peru on 2008-09-20
> **eye208 said:**
> Don't blame Audacity. PulseAudio is the part that's "broken" (i.e. not yet ready for prime time). If you suspend or remove it, Audacity will work just fine.

Do you have a link to suspending or removing PulseAudio?  I don't like to just go ripping default installed stuff off my computer.  I love guides, because I can re-run those steps backwards if I really mess something up. :)

Shane

---

### Post by eye208 on 2008-09-20
See post #4 in this thread.

---

### Post by arthursucks on 2008-09-20
For Audacity, I've been using Jack Audio.  It's a pain in the ***, but once Jack is running, Audacity runs so damn smooth.

---

### Post by shane2peru on 2008-09-22
> **eye208 said:**
> See post #4 in this thread.

Mine really is the opposite of his problem.  I got it straightened out now though.  Thanks.

Shane

---

