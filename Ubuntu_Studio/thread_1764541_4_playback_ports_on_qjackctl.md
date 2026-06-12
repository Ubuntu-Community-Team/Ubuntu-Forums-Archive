---
title: "4 playback ports on qjackctl"
date: 2011-05-21
forum: Ubuntu Studio
---

### Post by Grone1985 on 2011-05-21
Hi everyone!

I have installed KXStudio over Ubuntu in my laptop and have been trying to get the best setup I can. One annoyance I have found is that qjackctl lists 4 playback ports on my computer. I think 1 and 2 are for the HDMI output because 3 and 4 go out through the speakers/headphone jack. What I would like you to help me with is to figure out if there is a way to get this order inverted so that 3 and 4 become 1 and 2 so I don't have to edit the connections whenever I create a new track on Ardour or open a new program. Thanks!

---

### Post by cchhrriiss121212 on 2011-05-22
Type aplay -l into a terminal to see what audio you have.

As a solution. you could either disable the HDMI channels (easy), or make the other outputs default (less easy). Which one would you like to do?

---

### Post by Grone1985 on 2011-05-22
Ok, so aplay -l gave me this:

```
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC269VB Analog [ALC269VB Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 1: NVidia [HDA NVidia], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: NVidia [HDA NVidia], dispositivo 7: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: NVidia [HDA NVidia], dispositivo 8: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: NVidia [HDA NVidia], dispositivo 9: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

And I think I would like to set the other outputs as default because I do use the HDMI every now and then. So how do I do that? Thanks!

---

### Post by cchhrriiss121212 on 2011-05-22
From that output we can see that your HDMI connection is a separate audio device, which means that they are not what you see in jack (which uses only one device at a time).

I think the easiest option would be to change your auto connect preferences in each program to use channels 3 & 4. Switching them around would require some in depth knowledge of ALSA configuration, which in my experience, is a time consuming process because what works for one card won't work for another. Take a look at this if you wish to proceed:
[http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc)

---

### Post by Grone1985 on 2011-05-22
Ok cool, I got some of the programs ready. But how could I do it for alsa to jack bridging?

---

