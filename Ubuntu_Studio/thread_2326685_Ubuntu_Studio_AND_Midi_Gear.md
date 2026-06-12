---
title: "Ubuntu Studio AND Midi Gear"
date: 2016-06-03
forum: Ubuntu Studio
---

### Post by mbender on 2016-06-03
Anybody out there had success with midi keyboards and recording interfaces, please post makes and models.

Also, post unsuccessful interface attempts with gear names.

Thx!

---

### Post by marseille2 on 2016-06-04
Take a look at the forum for [linuxmusicians.com]("https://linuxmusicians.com/"). They have some of the best threads going about gear... Also see the [ALSA Sound Card Matrix]("http://www.alsa-project.org/main/index.php/Matrix:Main") to check out known compatibility for interfaces.

---

### Post by yoshii on 2016-06-04
USB audio interfaces and USB MIDI keyboards that are "USB Class Compliant" should work in Linux (and in MacOS and Windows) without issues.  
Their class compliance means that they were designed to fit and match the USB standards for working with operating systems without needing to manually install drivers.  

I have the Alesis M1Active 320 USB audio interface/monitors and it works.  It shows up in software as something like "USB AUDIO CODEC", just like it's manual says it should.  
Also, I have the M-Audio Oxygen 49 MKIV USB MIDI keyboard and it works too.  It shows up in software as "Oxygen 49".  
Also, I have the Alesis Q25 USB MIDI keyboard and it works and shows up in software as "Q25".  The Alesis Q-series is USB Class Compliant, but many of their other series gear isn't and thus probably doesn't work.  It took a lot of effort to find out about M-Audio gear by downloading a lot of PDF files, but a lot of M-Audio USB MIDI keyboards are USB Class Compliant also.  In terms of actual physical preference, I find the Alesis gear to be of higher quality and reliability.  

If you have a desktop computer with the old standard PCI card slot(s), then the M-Audio Delta Audiophile 2496 24-bit audio interface might work.  
I used to have that and from what I remember, it's compatible as "ICE ENVY" or something like; it doesn't show up in software as Delta Audiophile.  But because the internal hardware of it is actually known by a different name, that's the name that Linux sees and it's configurable in ALSA.  But it's been a long time since I had that and I haven't tested it in Ubuntu.  I did test it in Puppy Linux though, and I was able to get monophonic audio.  Back then I didn't know much about Linux though.  If I remember correctly, I was able to get stereophonic audio in WattOS but I had to edit some configuration files.  These days it's probably easier to get stuff to work.

---

