---
title: "m-audio conectiv usb - no input with alsa, jack"
date: 2009-01-06
forum: Ubuntu Studio
---

### Post by oida on 2009-01-06
Hi, I'm using an M-Audio Conectiv USB interface.
Playback worked out of the box with both Ubuntu 8.04.1 and Ubuntu Studio 8.10

However, I can not record. I tried Audacity, Ardour and PureData with both ALSA and JACK. All it gives me is a low volume noise at 25dB (PureData) or -45dB (Ardour)

```
$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Conectiv [Conectiv], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Conectiv [Conectiv], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I think, the problem might be, that a mixer control for the input(s) would need to be unmuted or raised in level. I can unfortunately not control any mixer settings:

```

$ alsamixer -D hw:1
No mixer elems found

$

```

I'm stuck now.
Anyone got a clue how I might get this to work? ANY help is highly appreciated.
I know some people got it working properly with other Linux distributions, notably Fedora Core. I don't know how, unfortunately.

---

### Post by kamlapati on 2009-01-07
That device is not mentioned on the ALSA support page. Does it perhaps go by another name?

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-MAudio](http://www.alsa-project.org/main/index.php/Matrix:Vendor-MAudio)


BTW, I had similar problems with my M-Audio Fast Track PRO (same symptoms).

---

### Post by oida on 2009-01-07
Did you solve your input problems with the fast track pro?
There are some suggestions here: [http://ubuntuforums.org/showthread.php?t=769822](http://ubuntuforums.org/showthread.php?t=769822)

The Fast Track Pro is an usb audio class compliant device.
The Conectiv seems to be a DFU device which needs a firmware download before every connection.

I found the madfuload tool which seems to be inactive since three years though and only supports Audiophile, MobilePre, Sonica, Transit and Ozone.

[http://usb-midi-fw.sourceforge.net/](http://usb-midi-fw.sourceforge.net/)

I also could not find any ma****.bin file in my Windows/system32 directory after installation, only madfu.sys, so I'm not sure, if it's really a simple DFU device. For me, that doesn't fit together with the fact that audio output works.

---

### Post by kamlapati on 2009-01-07
No, I kind of gave up and decided to get a Delta 66, which has a long track record of working!

However, I am going to come back to it since I need something for my laptop as well. Thank you so much for pointing out that post. I will try that stuff as soon as I get the time.

---

