---
title: "Quickshot Midi Composer Not Working."
date: 2009-02-28
forum: Ubuntu Studio
---

### Post by Chris^%$£&quot;! on 2009-02-28
Hello all,

Have been reading around in the forums to no avail, so please dont direct me to more reading please. Got to the pulling hair stage, needing some help, so here goes:

Have a ASUS P4C800-E Deluxe MB, onboard sound and MIDI port 
(MIDI port enabled in bios as 200/330, IRQ 10, the onboard sound is disabled but the midi port enabled, able to configure separately, although have tried both ways on and off sound, dosnt work either way!)

Audigy 2 ZS Value card working ok, hearing sound ok from playing shoutcast and other downloaded media, also virtual midi keyboard works OK, and can play and hear notes on PC keyboard and with mouse.

Have upgraded Ubuntu to Ubuntu studio, tried using jack control to connect everything up and run Rosegarden and play quickshot keyboard, but dosnt work.

Nothing showing in the midi tab in jack control???

Taken a snap of what I have in Jack, havnt got a clue of what to connect to what although have tried all sorts of possibilities including everything connected to everything! Managed to connect the virtual keyboard ok though and that works.

I was getting an error from rosegarden on startup:
System timer resolution is too low, before and after upgrading to the studio edition of Ubuntu.

Just want to use the MIDI Quickshot keyboard to play into Rosegarden and compose, but feel I have come to a brick wall, I am new to Ubuntu, am I missing something really obvious, the fact that there is nothing in the midi section in Jack is worrying.

Any help advice much appreciated.

---

### Post by thorgal on 2009-02-28
maybe you can get some inspiration from this thread. It's not exactly an answer to your questions :

[http://ubuntuforums.org/showthread.php?t=1068913](http://ubuntuforums.org/showthread.php?t=1068913)


As to the timer resolution, it's a kernel thing. You will need the RT kernel (package linux-rt) but if you are using ubuntu 8.10, there are issues with RT kernel 2.6.27-xxx and MIDI ...

---

### Post by Chris^%$£&quot;! on 2009-03-01
Hello,
Thank you for responding, have it working now!

The problem was that the onboard midi port wouldn't work at all, so I pulled my soundcard (audigy 2ZS) and had a look at it carefully.

On the card is a blank area where there should be a midi pinout arrangement, the holes just soldered up, no way of connecting anything.

I decided to solder 15 little wires into the soundcard to simulate a pinout header, poked the wires into the appropreate holes on the internal midi, lead and hey presto! worked a treat.

---

### Post by thorgal on 2009-03-01
so it was a hardware issue! well spotted :)

---

