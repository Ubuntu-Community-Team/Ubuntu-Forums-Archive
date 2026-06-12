---
title: "Jack does not show multiple capture devices"
date: 2013-08-09
forum: Ubuntu Studio
---

### Post by ShawnCP on 2013-08-09
Hi All,

I cannot get jack (in QJackctl) to show all (both) capture devices.

First of all, please accept my apologies if this is not the right forum.  This problem is actually on Ubuntu 12.04 not Ubuntu Studio.  I have been trolling the web for hours and am just not coming up with anything.

So, specifically, I expect in QJackCtl to see: Capture_1, Capture_2, Capture_3, Capture_4, but am only seeing Capture_1, and Capture 2, which (check me :) ) are the left and right channels for one capture device.  (Card 0 in the listing below.)  

On my particular board/chipset, I have two capture devices which can be individually assigned from Front Mic, Rear Mic, and Line.  Sound is playing just fine and I can record from either capture device in Audacity if I select from Alsa sources instead of jack sources.

Info:

```

uname -a
Linux ... 3.2.0-48-generic #74-Ubuntu SMP Thu Jun 6 19:43:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

```
arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: VT2020 Analog [VT2020 Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: U0x46d0x8cb [USB Device 0x46d:0x8cb], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Does anyone know what I need to do to get both capture devices working in Jack?  Or can point me to the relevant docs so I can RTFM?

Thank you.

-Shawn

---

### Post by jejeman on 2013-08-09
Yes, JACK works only with one card at the time. Or, it can work with two but only one can be assigned for either input or output. Can't input/output from two cards at the same time.

---

### Post by zequence on 2013-08-09
It is possible to use multiple devices, but that doesn't work by default. You can read more about that here [http://jackaudio.org/multiple_devices](http://jackaudio.org/multiple_devices).

---

### Post by ShawnCP on 2013-08-09
Thanks everyone.

To clarify, I do not need to use multiple cards.  I need to use both capture devices for the first card (Card 0).

---

### Post by jejeman on 2013-08-09
Well devices are card0, card1 etc. 
If you think on Mic, Line in, that are inputs. You can record from only one at the time (usually cards have only 2 input channels). Playback (monitoring) from both in the same time is supported, but I think that is done on the hardware level.
Idea - try to record playback, with some custom ALSA setting.

---

