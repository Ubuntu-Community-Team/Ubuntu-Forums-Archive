---
title: "Firewire 410 no longer showing in QjackCtl Audio tab"
date: 2015-01-06
forum: Ubuntu Studio
---

### Post by Bransby on 2015-01-06
Hi

I have an M-Audio Firewire 410 connected via a PCIe Firewire card. I'm running Ubuntu Studio 14.10, kernel 3.16.0-28-lowlatency. Yesterday QJackCtl was showing FW410 as an option when selecting ALSA as the driver, but I couldn't get the FW410 inputs and outputs to appear in the Connections window until I ran ffado-dbus-server - then everything started working perfectly. I could control all the outputs and inputs to the FW410 from the Ffado mixer, I was able to record via analogue input and route audio from Ardour through analogue outs, I also managed to get audio playback from Audacious.

Then I clicked on something in the Ffado mixer, I'm not sure what, and everything died. Now the Ffado mixer shows all the FW410 control but Jack refuses to recognise it on the Audio tab. It recognises it under the Midi tab, and always has done, but it does not appear as a routing option in the Audio tab. I'm not sure whether this is an issue with the order I'm starting things up in. I've tried various options, but I can't get Jack connections to show the FW410 audio ins and outs.

I've done a lot of searching about on this issue, but I'm aware that the snd-bebob support for the Firewire 410 is very recent so there isn't much out there that's relevant to my exact situation. What's frustrating is that for a brief, glorious moment everything was working fine, and i had a fully functioning Firewire 410 on Ubuntu which made me very happy. Then I dicked it up and I don't know how.

Any ideas?

Thanks

Bransby

---

### Post by Bransby on 2015-01-07
Quick update - thought it might be a pulseaudio conflict as pulseaudio was showing up in QjackCtl, so I killed pulseaudio and made sure it stayed killed as per instructions here [http://www.linuxplanet.com/linuxplanet/tutorials/7130/2](http://www.linuxplanet.com/linuxplanet/tutorials/7130/2) - which has ensured that pulse no longer shows up in QjackCtl, but still the only audio connections showing are the system on board ins and outs, not the Firewire 410. In QjakCtl I'm able to change the sample rate of the Firewire 410 which is then reflected in the Ffado mixer, so there clearly is some level of control from QjackCtl, but still no visible audio ins and outs from the FW410.

Thanks

Bransby

---

### Post by Bransby on 2015-01-08
Disabled the onboard sound in Bios, Firewire 410 shows as "System" audio in QjackCtl which is a bit off-putting as that's how the on board sound was labelled too, but nevertheless I now have control over my Firewire 410. Lots of clicking going on at the mo, so suspect some dicking about with IRQ and buffers is required but at least the little tinker is playing my tunes.

Hope this is of some help to someone in the future!

xx

---

