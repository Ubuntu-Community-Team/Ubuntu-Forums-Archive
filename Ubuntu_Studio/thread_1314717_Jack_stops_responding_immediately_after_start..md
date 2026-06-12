---
title: "Jack stops responding immediately after start."
date: 2009-11-04
forum: Ubuntu Studio
---

### Post by Muffinabus on 2009-11-04
I am trying out SuperCollider and installed SC, the plugins, and Jack.  When attempting to start the Jack server, I get the following in the messages window:
```
16:26:07.172 JACK was started with PID=9738.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
16:26:09.314 Server configuration saved to "/home/brad/.jackdrc".
16:26:09.315 Statistics reset.
16:26:09.368 Client activated.
16:26:09.370 JACK connection change.
16:26:09.380 JACK connection graph change.
16:26:09.402 XRUN callback (1).
16:26:11.373 XRUN callback (46 skipped).
16:26:13.874 XRUN callback (59 skipped).
16.26:16.525 XRUN callback (61 skipped).
jackdwatchdog: timeout - killing jackd
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
```

Any suggestions on what I should do?

I am entirely new at sound development and everything, so I do not know what to look for or how to troubleshoot.

I guess it should be noted I'm on Karmic, have a Soundblaster Audigy soundcard and am running on a P4@2.8Ghz.  I also have a USB headset plugged in and I hear it might have problems with multiple sound devices, but I have removed it and tried it again and get similar results that ends with the program crashing or hanging.

---

### Post by AutoStatic on 2009-11-05
Try other settings like force 16-bit or a sample rate of 48000. JACK now chokes on too many xruns.

---

### Post by rada on 2009-11-15
> **Muffinabus said:**
> I am trying out SuperCollider and installed SC, the plugins, and Jack.  ....

I guess it should be noted I'm on Karmic....

Sorry to hijack thread, but how did you install SC? I don't find any karmic packages in ppas or Ubuntu Studio list, although I'm running regular karmic 64 bit.

---

### Post by sgx on 2009-11-15
this how-to from 2007 at least mentions dependancies, and the process, so   you might be able to install the deps via synaptic, and then follow the tutorial for the SC itself. Cheers

[http://www.yeeking.net/index.php?location=Quick%2064%20bit%20Debian%20Supercollider%20install%20howto](http://www.yeeking.net/index.php?location=Quick%2064%20bit%20Debian%20Supercollider%20install%20howto)

---

### Post by sgx on 2009-11-16
@ the OP, Hi, if you are not a linux expert, or knowledgeable programmer, I highly recommend studying sound design with zynaddsubfx instead, as you can use the sounds you find appealing, enter the editing pages, and begin experimenting and taking notes. Things like resonance, cutoff and gain, among others, can abruptly launch damaging sound levels, so take appropriate cautions, move knobs in small increments, with system volume low,
note the 'panic' button, its there for good reason! There are many editing pages, multi-fx chains to utilize, and a few hundred usable often wonderful sounds to begin with. First you must start jackd

jackd -d alsa -r 44100    is a good command for now, then launch qjackctl, open the connections button, and of the 3 tabbed interface that appears, connect zyn to to system on the left tab, annd a midi keyboard if you have one, in the right-most tab. There is a Virtual Keyboard button on the zyn gui
(initials only, not spelled out).
You can of course try the SC, to see if it appears in qjackctl, and go from there if it does! cheers :)

---

