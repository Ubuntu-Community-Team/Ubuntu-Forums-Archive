---
title: "ALSA oddities and no sound after soundcard change in natty"
date: 2011-07-02
forum: Ubuntu Studio
---

### Post by Jay105 on 2011-07-02
[INDENT]                             Hi
 
I've just bought myself a E-MU 1820M audio interface for use in home  recording after seeing online that a number of people have managed to  get it working. The card replaces a Terratec DMX 6Fire (which i only  managed to get outs from, no in's). I have done everything and anything  suggested all on the forums and websites i can find and still no in's or  out's at all, and no lights on the dock functioning.
 
Having tried and failed on a number of things i decided to see if Alsamixer had picked it up, only to be shown a blank grey window  with nothing showing. I purged ALSA and started again (I have even done  a fresh install of natty in case it was anything else getting in the  way that i had done previously) but to no avail. I am using ALSA driver[]("http://www.linuxforums.org/forum/#")  1.0.24, which is the latest version, and according to the ALSA website,  the EMU support was addded in post-1.0.15, so all should be well.
 
Could it be ALSA 1.0.24? Could it be that Natty just doesn't get on with it?  
 
Any suggestions?                         [/INDENT]

---

### Post by Pablo_F on 2011-07-02
Hi, 

Please, run the alsa-info.sh script and give the result, so we can try to see the sources of the problem.

Cheers, Pablo

---

### Post by WalmartSniperLX on 2011-07-04
Grey window? Are you launching Alsamixer in the CLI? Do alsamixer in the terminal and it will tell you the hotkey to select devices in the top right. See if your device is there, and make sure you have it set for default. Sorry if I'm not in the ball park but that's what I would do first, and I personally tend to get better luck managing devices from the cli.

---

### Post by sgx on 2011-07-05
> **WalmartSniperLX said:**
> Grey window? Are you launching Alsamixer in the CLI? Do alsamixer in the terminal and it will tell you the hotkey to select devices in the top right. See if your device is there, and make sure you have it set for default. Sorry if I'm not in the ball park but that's what I would do first, and I personally tend to get better luck managing devices from the cli.

How did you come up with WalmartSniperLX for a nik?

---

