---
title: "Dumb Questions"
date: 2008-08-21
forum: Ubuntu Studio
---

### Post by TeeBird on 2008-08-21
Dude, I just got a Dell desktop with hardy.  Got a wireless stick and have no problems running stuff, etc.  My history:  winders at work and Mac at home.  (Long time solid geometric modeling software developer; old timey BSD Unix and even assembly language guy).

Just starting to play with JACK, ALSA mixer, Audacity.  Don't have studio yet.  I checked out Hydrogen; looks awesome.  I have Ardour but haven't used it yet.

Do you think the Intel HD ICH9 soundcard will be ok for the time being?  Do you think I should just go ahead and install studio or is their any point to setting it up to dual boot ubuntu/ubuntu studio?

My highest priority goal is to sequence and record (I play guitar, bass and build vacuum tube amps) music with high sound quality, though I may also wish to try to piece together and/or develop some mechanical engineering design tools at some point for a long term research project.  Side stuff I like to do includes still photo processing. website design, and of course email and browser.  No gaming.

Thanks for any comments you may have.

---

### Post by TeeBird on 2008-08-22
Bemp.

Shouldn't have called it Dumb Questions.  :)

---

### Post by caljohnsmith on 2008-08-22
If you all ready have Ubuntu installed, you can install Ubuntu Studio "on top of" Ubuntu by doing:
```
sudo apt-get install ubuntustudio-desktop
```
I believe that will install most everything you need, but there may be a few ubuntustudio-* packages not included which you can install manually too. But bottom line is you don't need a separate partition for Ubuntu Studio in addition to Ubuntu. You can have your cake and eat it too. :)

---

### Post by thorgal on 2008-08-22
Intel HDA ? not really friendly with jackd. Get something proper (a PCI interface like an RME HDSP or M-Audio Delta) and make sure it is fully supported. I have the RME HDSP PCI card with the RME Multiface II external IO box -> great stuff!! but pricy ... 
you can get the intel HDA to work reasonably OK with jackd but it's not really worth if you plan to produce high quality music.

---

### Post by TeeBird on 2008-08-22
Thanks.  So the studio kernel is just as solid as vanilla ubuntu?  Or good enough?

On the card, I was figuring I would need a better PCI card in the long run anyway...thanks for confirming that.

---

### Post by caljohnsmith on 2008-08-22
The studio kernel is just a patched version of the generic kernel to include "realtime" support. It is not a drastic overhaul of the kernel, so for most people it is just as reliable as the generic kernel. 

In case you want just a little more info on what the extra functionality the "realtime" kernel gives the user, you might want to read my post in this thread:
[http://ubuntuforums.org/showthread.php?t=896721&page=2](http://ubuntuforums.org/showthread.php?t=896721&page=2)

---

### Post by thorgal on 2008-08-22
about ubuntu I cannot say, I am using my own custom system based on debian sid. I tried ubuntu studio about a year ago but it was not stable enough and there were a few things I disliked (but nothing to do with realtime operation).

if you want to give priority to audio, then you need the RT kernel and set up your security accordingly. Installing ubuntu studio should have all this set up by default. One thing I remember : the RT patch made the suspend/resume operation unstable for me. That was some tim ago and it seemed OK last time I tried expect for one thing : it screws up something in the RME Multiface II. The only remedy : shutdown AND power off the PC, then booting up again should re-flash the firmware correctly.

If you want to use the intel HDA, you will have to set the periods per buffer to 3 in the jackd setting (qjackctl setup window).

What is the graphics chip ? I have the i965. The Xorg driver will enable hardware acceleration (3D and 2D). I disabled all that stuff, I detected some instabilities. IIRC, the intel graphics chips use PCI access for acceleration ( I know, they are integrated chips). But I did notice an improvement in the audio flow (no xruns, etc). The price to pay is a sometimes sluggish quick scrolling (firefox, etc) but my PC is a DAW so I don't fool around with it, I process audio only. I have my laptop for fancy but not important things.

---

### Post by TeeBird on 2008-08-22
Suspend/hibernate don't work anyway so that's no loss.

I got some ATI graphics card; it was the mid-level option.  I'm not planning to run any 3D mechanical CAD programs (I do that at work) so I didn't worry about that too much.  Hopefully any graphics computation load won't affect sound processing.  I'll deal with that later if so.

I'll read the linked thread, thanks CJS.

Edit:  read.  Yeah, that's what I understood it to be.  Your final comment is a little worrisome because I know Dell added a proprietary driver for the ATI card.  I guess I will find out...

---

