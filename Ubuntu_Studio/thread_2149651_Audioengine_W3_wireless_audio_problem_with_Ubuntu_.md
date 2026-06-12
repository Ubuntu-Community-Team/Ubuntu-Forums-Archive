---
title: "Audioengine W3 wireless audio problem with Ubuntu Studio 12.04"
date: 2013-05-29
forum: Ubuntu Studio
---

### Post by eboats on 2013-05-29
I'm unable to get the Audioengine W3 wireless audio adapter to work with Ubuntu Studio 12.04 LTS (64 bit).  I've had no problem getting it to work with Ubuntu Desktop 12.10 and 11.4 so am not sure why I'm having problems with Ubuntu Studio.  

While I can see and select the Audioengine adapter in the Pulse mixer, the sound is still coming from my internal sound card rather than through the wireless adapter, even after rebooting with the Audioengine plugged in.  

When I do an  aplay -l , I see the Audioengine per below :

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: Cirrus Analog [Cirrus Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: W3 [Audioengine W3], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

