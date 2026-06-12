---
title: "keyboard sequencer"
date: 2013-06-22
forum: Ubuntu Studio
---

### Post by ajits on 2013-06-22
help me..which ubuntu software help me to midi keyboard sequencing.is it has roland guno Gi keyboard 16 midi track? is it possible to play audio track with midi track? can it do step recording?:)

---

### Post by Bucky Ball on 2013-06-22
*Thread moved to **Ubuntu Studio**.*

You'll probably have better luck here, even though this question is not directly to UStudio. ***Forum Feedback & Help*** is for threads specifically about the forums, not for technical help. 

Can you also add a little more detail. Is the keyboard USB? Have you plugged it in via USB and switched it on? What software are you using now? What research have you already done and what have you already tried? What Ubuntu release are you using? (If it is still 10.04 LTS it has reached end-of-life and is no longer supported.) ;)

If it is USB, plug it in, switch it on, open a terminal and run this:

```
lsusb
```

Is there anything there about the keyboard in the output? Post the output back here, please.

* Update: Yea, been looking at the keyboard here:

[http://www.rolandus.com/products/details/1126/specs/](http://www.rolandus.com/products/details/1126/specs/)

Unless you have an audio interface, plug the USB in, switch the keyboard on and immediately issue:

```
dmesg
```

... in a terminal. Does it say anything about having plugged in the device?

If you are not using USB but plugging the Juno into an audio interface via MIDI or using MIDI somehow, then you need to work out how to get the MIDI device you are plugged into talking nicely with Ubuntu rather than the keyboard.

Hopefully someone that has experience with all things Linux and pro-audio can find this thread now. ;)

---

### Post by jejeman on 2013-06-22
> **ajits said:**
> help me..which ubuntu software help me to midi keyboard sequencing.is it has roland guno Gi keyboard 16 midi track? is it possible to play audio track with midi track? can it do step recording?:)
Your questions does not make much sense.
Slow down, and explain what you need more elaborate.

---

