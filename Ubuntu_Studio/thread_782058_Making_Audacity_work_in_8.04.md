---
title: "Making Audacity work in 8.04"
date: 2008-05-04
forum: Ubuntu Studio
---

### Post by skullmunky on 2008-05-04
Short answer: recompile from CVS.  

Like a lot of folks, I did a fresh install of 8.04 and suddenly found that Audacity didn't work and would errors about being unable to open a sound device, etc., when I tried to play any sounds.  Also, it gets really slow and sometimes becomes totally unresponsive.  If you run audacity from the terminal you get tons of frantic errors about AlsaOpen failing.  That's the command to open the sound device to try and play something failing; it thrashes around helplessly in frustration and kind of freezes up.

The solution I've used for years still works:

```

aoss audacity

```

which makes audacity run using OSS, in an ALSA wrapper. 

In previous versions, this was important because OSS, ye Olde Sound System, does not allow more than one program to access the sound hardware.  So, if anything else is trying to make sounds, like desktop sounds, RhythmBox, something in your web browser, etc., it can't do anything.

ALSA lets you play sound in more than one program at once.  

Up until pretty recently, Audacity only supported OSS, hence the aoss wrapper workaround.

As of 05/04/2008 the version of Audacity in the repositories is 1.3.4.  This version has support for ALSA and also JACK, which is a really cool thing when it works.  

But 1.3.4 seems to have some oddities with its Jack communication; for instance, it tries to start Jack even if you just want ALSA, and in any case just doesn't play any sound no matter what you do.

Some other threads suggest making sure the sampling rate is set to 48k instead of 41, and the same in Jack Control, but that didn't work for me.  What did work, though was just downloading the source from audacity.sourceforge.net and recompiling it.  

that's NOT the "1.3.4 Beta" download, you have to open a terminal and use cvs to download version 1.3.5.  just compile and install it - for me that solved everything.  Running audacity alone lets me use the ALSA devices properly; if I have Jack started, I can tell Audacity to use Jack, and all the mixing and filtering things work great.

---

### Post by stinger30au on 2008-05-04
thanks for the tip, have not experienced the error  myself though

---

