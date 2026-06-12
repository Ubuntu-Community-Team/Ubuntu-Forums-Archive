---
title: "Choosing the right Audio Interface for Ardour"
date: 2014-12-29
forum: Ubuntu Studio
---

### Post by Rob_Shepley on 2014-12-29
Hey guys,

I'm putting together a PC with the intention of doing some multi track recording for a band that I'm in. I've used Ubuntu and Debian for many years, but for this I'm probably going to go with Ubuntu Studio for this.  I've used Ardour for recording in the past, recording only from the line-in from my onboard soundcard.

This PC will have a AMD Athlon 4600x2 CPU in it. Hopefully this won't be too dated for this application.  It has a PCI Firewire card installed, as well as a bunch of USB2.0 ports available.

I'm most experienced with Ardour, but am willing to use a different DAW if you guys recommend it.

Anyway, looking for suggestions on what audio interface to use for multitrack recording.  I'd like to keep this as inexpensive as possible, but need to record at least 6 tracks at once (more tracks if I can).  I've found that when working with other peripherals, some manufacturers seem to have much better Ubuntu support than others.  (For example,. Brother seems to have great Ubuntu support for their printers, so I typically buy Brother when I need a printer).   Anyway, is there a certain brand that works best when it comes to multi track audio interfaces?   I've looked at the ALSA compatibility list, and there's just too much on there to go through every single brand, so I was hoping somebody could suggest what the most Ubuntu friendly brand is?

---

### Post by bhilmers2 on 2014-12-29
Hi [COLOR=#000000]Rob_Shepley[/COLOR]. Ardour is the best choice for recording a band. I'm also a fan of a DAW named [EnergyXT]("http://www.energy-xt.com/"), but it costs money and has little development or support. Speaking of support, the Ubuntu Studio forum is not the ideal place for audio questions. Try [LinuxMusicians.com]("http://www.linuxmusicians.com/viewtopic.php?f=6&t=13093") and get better answers. The site is very active.

The good news about audio interfaces is that major manufactures do a decent job of making thier devices class-compliant and even generic kernel drivers are usually enough to use them, though you might need a special package if the device has peculiar features. I've had good luck with M-Audio products using the *midisport-firmware* package, but then again this is Linux, so "results may vary." ;)

---

