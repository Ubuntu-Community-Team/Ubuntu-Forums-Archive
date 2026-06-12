---
title: "Both Midikeyboards won't connect"
date: 2015-06-16
forum: Ubuntu Studio
---

### Post by bunkum on 2015-06-16
Hello,
I have set up a ubuntu studio 14.04 on which I am using renoise, pure data and sooper looper. Now there's been one nasty problem with it. I have an alesis io2 express connected to it which works fine. But when I connect a midi keyboard (I've tried two of them, an evolution MK 224 and a Fame Tweak 25) it recognizes the keyboard but won't connect it to any given program. I don't know why. I've read through numerous threads now which tackle similar problems but not exactly this one. None of the solutions helped (aka adding user to audio group, which was already done; checking qjackctl periods (set to 3)).
I would greatly appreciate any solutions 'cause I'm kind of helpless at the moment with this.
Cheers
Jens

---

### Post by jejeman on 2015-06-17
JACK (settings) does not have influence on MIDI devices. It is handled by ALSA.
Plug in USB keyboard. Give
```
lsusb
amidi -l
```
Do you use USB or MIDI?

---

