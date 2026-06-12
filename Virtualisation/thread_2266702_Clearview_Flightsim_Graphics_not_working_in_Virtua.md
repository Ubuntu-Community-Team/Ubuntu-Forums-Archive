---
title: "Clearview Flightsim Graphics not working in Virtualbox running Win 7"
date: 2015-02-24
forum: Virtualisation
---

### Post by PopsTheSailor on 2015-02-24
I'm running Ubuntu 14.04 as my main OS. I have Virtualbox installed with Windows 7. I'm trying to get a flight simulator to work but all I get when I run the app is a black screen. The menu bar does appear. The flightsim is called Clearview the SE version. It's version "ClearviewSE RC Flight Simulator version 5.50". I don't know much about how graphics work in virtualbox but I did find a setting and set my video memory to 128MB which is the highest setting that is allowed. That didn't fix it. 

Anyone have any ideas about what might be causing this? ClearviewSE does run fine natively if I boot into Windows.

---

### Post by TheFu on 2015-02-27
[http://rcflightsim.com/help.html](http://rcflightsim.com/help.html) has a few ideas.  I suspect the virtualbox video driver isn't close enough to a real GPU for this program.
[http://ubuntuforums.org/showthread.php?t=2198726](http://ubuntuforums.org/showthread.php?t=2198726) is from people running it under WINE. With a fast enough CPU, that should be workable - there are 2 recent reports - one said garbage and the other claimed platinum support which basically means everything works exactly like it should.  The Platinum report didn't provide any winetricks or other comments - might be worth contacting him directly?

The report:```

What works
Everything worked nearly flawlessly for me. Installs and runs with no issues.

What does not
Had once a graphics glitch after a crash, but recovered by pushing the spacebar to reset the sim. Otherwise no issues.

What was not tested
nothing
```

Running under wine should be significantly faster than under vbox.

---

### Post by PopsTheSailor on 2015-02-28
Thanks. It is working now in Wine. Unfortunately, I have no idea why which bites because that means this won't help anyone else. I just started it up and it works in Wine. Thanks for the help.

---

### Post by TheFu on 2015-02-28
> **PopsTheSailor said:**
> Thanks. It is working now in Wine. Unfortunately, I have no idea why which bites because that means this won't help anyone else. I just started it up and it works in Wine. Thanks for the help.

I've had working programs under WINE stop working after a newer WINE release. Definitely capture the WINE version, installed winetricks and keep the WINEPREFIX outside the default, so it doesn't accidentally get clobbered.

Things that magically start working worry me.

---

