---
title: "usb mic with jack"
date: 2011-03-11
forum: Ubuntu Studio
---

### Post by Affrikka on 2011-03-11
Hey everyone,

two things:

1) I have three USB mics, when plugged in they work fine under my normal sound stuffs, like the generic sound recorder, but Jack doesn't seem to recognize them (right now I'm just trying to get 1 working)
I want to use them in Ardour ultimately. How do I make Jack recognize them?

2) One I get them working, is it possible for them to all be plugged into Jack and all run with Ardour?


Thanks!


Mathieux

---

### Post by Affrikka on 2011-03-11
UPDATE: I have the usb mic working with both JACK and ardour now, yay!
I have a new problem, however, my speakers don't seem to work with jack. That is, I don't hear playback through them. On the setup I don't see anywhere for output devices that have to do with my speakers.

---

### Post by sgx on 2011-03-12
Hi, ardour output should be listed in the System capture on the left side of the qjackctl audio panel, and should be connected to the System playback on the right side. If this is already done, you may need a mixer volume turned on. alsamixergui can be installed, it is pretty
good at finding anything with an output. Some mixers are for pulseaudio, and not for jackd.
Cheers

---

### Post by Affrikka on 2011-03-12
everything is turned up, my speakers just don't show up for anything in jack

---

### Post by Pablo_F on 2011-03-12
Hi,

Please, show the terminal output of:

arecord -l && aplay -l

Cheers, Pablo

---

### Post by Affrikka on 2011-03-13
```
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 3: default [Blue Icicle ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 4: default_1 [Blue Icicle ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Pablo_F on 2011-03-13
Hi, 

You need to specify input device and output device separately:

Input device: 

hw:default

Output device:

hw:Intel

Cheers, Pablo

---

### Post by Affrikka on 2011-03-13
Hi,

I have the input as hw:3 which is my Blue Icicle, and my output I have tried every one and nothing has worked.

---

### Post by Affrikka on 2011-03-15
Bring
Up
My
Posts

---

### Post by sgx on 2011-03-16
> **Affrikka said:**
> Bring
Up
My
Posts
Hi, assuming your speakers have standard cables with any needed adapters, they plug into the line-out of your chosen soundcard, and that line-out, in qjackctl,  is on the right side of the audio tab, labeled 'System', with a little +  to the left, click that +  and 
you'll see playback_1 and playback_2 are your stereo line-outs on your soundcard.
I would set up a constant sound source for your mic, to test connections with alsamixergui, so you can see and or hear when a
proper connection is established.
Cheers

---

### Post by Affrikka on 2011-03-16
Hi,
I don't know if we're using different versions of jack, but there are no tabs labeled 'audio' or anything about what you're talking about anywhere in jack from what I can see. My speakers are indeed working when jack isn't running, I just don't understand why jack can't use the speakers when it is in fact running.

---

### Post by sgx on 2011-03-18
Hi, qjackctl is the gui for jackd. It is called Jack Connect in some menus. Here is are pages with screengrabs:

[http://qjackctl.sourceforge.net/qjackctl-ss1.html](http://qjackctl.sourceforge.net/qjackctl-ss1.html)

[http://www.64studio.com/quickstart_jack](http://www.64studio.com/quickstart_jack)

There may be an Alsa tab on the right, sadly these sceens only show audio and midi tabs.

Cheers

---

