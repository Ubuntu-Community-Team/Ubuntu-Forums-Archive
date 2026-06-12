---
title: "Bluetooth headphones with Ardour and alsa_out"
date: 2015-05-17
forum: Ubuntu Studio
---

### Post by Slatevine on 2015-05-17
Im running Ubuntu 14.04 with a modified kernel, but not full Ubuntu Studio - but I think here is where Im most likley to get the right help.

I have Ardour running with a Zoom G7 via usb. I also run alsa_out and have got playback through both the PC speakers and the Zoom. 

Im trying to go more step more and get playback via a set of bluetooth headphones. 

At the time of these tests, the headphones are connected, working and able to output sound. 

aplay -l gives me this:

```
**** List of PLAYBACK Hardware Devices ****

aplay -l

card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC668 Analog [ALC668 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

So using alsa_out, I can get simultaneous output to my PC speakers like this:

```
alsa_out -d hw:1
```

But there is no bluetooth device listed in aplay for me to connect to?

So how could I alsa_out to my bluetooth headphones ?

---

### Post by Slatevine on 2015-05-27
Is anyone able to help out? Someone must have done this, surely? Or does no-one have families that demand guitar practise through headphones!!

Or perhaps there's a better forum I should try? Im open to suggestions . . .

---

### Post by jejeman on 2015-05-27
Use traditional headphones.
See this forum [http://linuxmusicians.com/](http://linuxmusicians.com/) it is more "crowded".

---

### Post by Slatevine on 2015-06-03
Thanks for the links, Ill give them a try.

I had thought 'bout traditional headphones! But I'm likely to smash my guitar with frustration next time the lead wraps around everything!

---

