---
title: "Can't get started with Jack"
date: 2009-01-10
forum: Ubuntu Studio
---

### Post by acl123 on 2009-01-10
Hi,

I can't get any sound out of Jack. QSynth has provided me with the most useful error message: *"Failed to create the audio driver (jack)"*.

I have a usb soundcard (edirol ua-25) which is detected OK. I am trying to use the ALSA driver.

In Qjackctl I have setup the interface to "hw:1". I have tried checking and unchecking realtime and in Duplex and half-duplex modes.

I have installed UbuntuStudio and I think my system is relatively 'vanilla' at the moment, although I might have fiddled with one or two things.

Can anyone help me out?

---

### Post by kayosiii on 2009-01-11
Can you get QjackCTL to actually start jack? what happens when you press the start button?
If that fails try opening a terminal and typing 
"jackd -d alsa"

---

### Post by musicmatt on 2009-01-11
hey, I'm using a UA-30, and have the exact same problem.  I got it to work for a minute in a previous installation of studio (I also downgraded, and now I'm just running a standard installation.  this is actually kind of creepy).  even then, thought, it would xrun literally every 30 seconds.

the terminal thing seems to work, but what exactly is is doing, and will I have to repeat the action every time?

OK, I reinstalled studio, and I can start jack from Jackcontrol.  My roomate says it has to do with jack being a daemonized, though I'm still unclear about what exactly that means.

---

