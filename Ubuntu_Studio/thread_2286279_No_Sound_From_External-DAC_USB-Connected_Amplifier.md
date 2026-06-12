---
title: "No Sound From External-DAC USB-Connected Amplifier"
date: 2015-07-11
forum: Ubuntu Studio
---

### Post by charlessmall18 on 2015-07-11
I am running the latest version of Ubuntu Studio. I have a Class D, USB-connected, external-DAC amplifier (connected to some really nice JBL passive speakers). When I play an MP3 in Audacious, sound comes out of my JBLs. When I start QjackCtl and any sound source, the audio output is present only at the line-out (headphone/powered-speaker) green 3.5 mm jack on the back of my PC. I have tried to read all the documentation and directions about sound in Ubuntu and, frankly, I am totally baffled by it. I have tried to implement what fixes I could find on line and all that did was mess up my OS badly that   I gave up and re-installed Ubuntu Studio from an image backup (courtesy of Clonezilla). It sure would be nice if the output from the synthesizers provided with Ubuntu Studio, et al, would come out of my JBLs instead of my cheesy $12 Logitech powered computer speakers. Can anyone tell me what to do to direct sound output to a USB-connected DAC? Ubuntu knows right where that DAC is so I am hoping that Jack or ASLA or Pulse Audio or the ghost in my machine or something will allow me to hook it up. Thank you. Chuck

---

### Post by jejeman on 2015-07-12
You need to set JACK to use USB card, not the internal one. See in
```
aplay -l
```what is the name of the USB card, and choose that in JACK settings.

---

