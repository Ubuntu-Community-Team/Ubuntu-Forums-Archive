---
title: "Weird Sound Problem (Koala Mini)"
date: 2008-07-18
forum: System76 Support
---

### Post by agisfox on 2008-07-18
I've started having a weird problem with the audio on my Koala Mini (most recent hardware, running Ubuntu 8.04 with -proposed).  I'm using the digital output to toslink.  It worked fine until the last couple of days, whereupon it's acted really weird.

**Working reliably**:
* Mplayer Digital passthrough (mplayer -ac hwdts, mplayer -ac hwac3) where applicable.
* VLC using ALSA set to the digital out using digital passthrough (ac3/dts) where applicable.
* Forced digital output via Alsa in mplayer only (mplayer -ao=alsa:device=iec958 for anything mplayer can handle).
* Digital output via aplay (aplay -D iec958 whatever.wav)

**Works only when adjusting channel volume (subwoofer/front/etc) or effects (Dolby PLII effects/etc) on the speaker unit**:
* Stuff that (I think) uses the gnome audio configuration (banshee, rhythmbox, the Gnome Sound Preferences test function), as long as Gnome Sound Preferences are set to ALC883 Digital.
* VLC using alsa set to the digital out playing anything other than ac3/dts passthrough.

Alsamixer / gnome-volume-control are appropriately set to use digital output (iec958 ). The only other thing with optical audio output I have around (a PS2) works fine with the speakers; between that and the success with mplayer and aplay, I don't think this is a problem with the speakers, at least not entirely. Still, beyond reinstalling all of gnome and/or ubuntu, I'm not sure where to go from here.

---

### Post by agisfox on 2008-07-27
Well, reinstalling ubuntu fixed the problem; sound works fine now.

I'm still not sure what was up here.

---

