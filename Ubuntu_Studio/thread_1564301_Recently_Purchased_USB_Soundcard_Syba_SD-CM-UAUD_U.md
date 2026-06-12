---
title: "Recently Purchased USB Soundcard: Syba SD-CM-UAUD USB"
date: 2010-08-30
forum: Ubuntu Studio
---

### Post by Peter7K on 2010-08-30
Recently purchased this: [http://www.amazon.com/Syba-SD-CM-UAUD-Adapter-C-Media-Chipset/dp/B001MSS6CS/ref=sr_1_3?ie=UTF8&s=electronics&qid=1283180816&sr=8-3]("http://www.amazon.com/Syba-SD-CM-UAUD-Adapter-C-Media-Chipset/dp/B001MSS6CS/ref=sr_1_3?ie=UTF8&s=electronics&qid=1283180816&sr=8-3"), as it got great reviews etc., and users said it worked great under Ubuntu.  However, at the moment, it does not work right away on plugging it in.  What steps should I be taking?  I guess I might be missing a driver or something?

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: default [C-Media USB Audio Device   ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

EDIT: When I unplug speakers from the laptop soundcard and put them in the usb one the laptop just uses its speakers to play the sound :(

EDIT2: a few better worded searches and a few pages down the google hole and I found this helpful user:

> My new Dell Vostro 1220 ran into issues with its audio card and after several calls back and forth with tech support I was considering having to send in my machine for repair - until I found this thing :) 

Just plug it in and Win7 (I have a 64 bit) detects it. My Ubuntu 10.04 also detected it (you have to go to System->Preferences->Sound->Output and choose to send output to the USB device). 

Its seems as good in audio quality as my built in sound card. 

The only minor cons I see is that its a bit wide and may block up an adjacent USB port, if your ports are close together.

---

### Post by JC Cheloven on 2010-08-30
Just in case, let's start by the beginning: There is an icon in the upper panel, typically at the right, with a loudspeaker. Pressing it you find a slider, a button for mute/unmute, and a button to open the preferences dialog. In the preferences dialog:

tab "hardware": do you see both audio cards?
tab "output": is your usb device selected?

This kind of cheap audio devices usually work flawlessly in linux... only, you need to select the right device.

---

