---
title: "jack was working and then for no reason now gets 100s of xruns!"
date: 2009-12-27
forum: Ubuntu Studio
---

### Post by partofthething on 2009-12-27
This is so weird. I just bought a M-Audio Axiom 49 MIDI controller and had it all hooked up and working nicely with JACK, the rt kernel, Rosegarden, hydrogen, zynaddsubfx... the whole nine yards. I had decent latency and things were going well. This is on an online-upgraded version of Karmic Koala.

Then, after doing other stuff like fiddling with mapnik (totally unrelated) and suspending/resuming a few times over a few days, I rebooted. 

Now, when I fire up the jack server, I start getting HUNDREDS of xruns within seconds "XRUN callback (66) skipped" every second until jack crashes with the msg: "jackd watchdog: timeout - killing jackd"

I googled and searched and all that, reading that MIDI keyboards can sometimes take the place of the primary audio device (mine is an HDA intel on a Dell 1505E laptop) so I made sure the alsa-base.conf stuff was right. After going through everything a few times, I decided I must've messed up somewhere and went ahead and installed a fresh Ubuntu Studio on a spare hard drive I had sitting around (I swapped drives, so same computer). I fired up JACK and guess what! Hundreds of XRUNS! I couldn't believe it. So is this a hardware issue? did my sound card die (it still works fine in pulseaudio, etc.)? What's going on?!?

The only really weird thing I noticed in my BIOS was that "Audio controller" shows my modem and "modem" is my audio controller. WT..? That's not configurable though. 

Am I out of luck? would a USB sound card work? What happened? 

Thanks. 
-Nick

---

### Post by ajgreeny on 2009-12-27
If you have installed a proprietary driver for your software(?) modem, assuming you have one from your BIOS comment, disable it and try the audio again.  There seems to often be a problem with the sound system and modem using the same chips and not allowing both to work.

If you really need the modem, I don't know how to deal with the problem.

---

### Post by partofthething on 2009-12-27
Well, first of all, I didn't even realize I had a modem. Additionally, I see no mention of it anywhere in Ubuntu. I assume I'd have to install a driver for it to see it. Anyway, I'd definitely disable it in bios if I could but it's not an option. 

A further update, I got a Creative SB X-Fi 1090 USB off craigslist today and it totally works out of the box with JACK (hit the little arrow, choose hw:1), so I'm at least making music again:P. OK sound, at least.  I'm still confused as to what happened.

I should also mention that at some point my laptop overheated or something to the point of warping plastic near the battery... yeah. That was a while ago and everything's been working. This is why I'm not ruling out weird hardware problems. If anyone has other ideas, let me know. 

-Nick

---

### Post by bluesscream on 2010-01-01
what about a bios update?

an other thing:
/etc/security/limits 
are  @audio rtprio 99
@audio nice -19
set properly?

ubustu updates resetted this for me repeatedly

---

### Post by sojournerC on 2010-01-04
verify that you are using a 2 period buffer and try increasing the buffer amount in jack setup. Latency will increase, but you might find the xruns gone

---

