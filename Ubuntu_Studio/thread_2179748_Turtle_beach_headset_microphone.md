---
title: "Turtle beach headset microphone"
date: 2013-10-09
forum: Ubuntu Studio
---

### Post by Tristan_Williams on 2013-10-09
I have a Turtle Beach px21 headset. As far as i know everything is connected properly between the headset and my computer. I am trying to use the mic on the headset in Ardour.

I opened QjackCtl and the mic does not show up there, nor does it show up in PulseAudio.

The headphone part of the headset works perfectly fine, its just that the mic doesn't work. 

The mic is connected via USB.

---

### Post by jejeman on 2013-10-11
Connect everything and give
```
lsusb
arecord -l
```

---

