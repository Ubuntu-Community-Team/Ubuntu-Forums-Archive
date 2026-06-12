---
title: "No playback or live sound when using JACK"
date: 2011-11-08
forum: Ubuntu Studio
---

### Post by Tallguitarguy on 2011-11-08
I've finally got JACK set up and appears to be working fine. I used these two videos to help. 
[http://www.youtube.com/watch?v=w2gPqH6kNJU&feature=related](http://www.youtube.com/watch?v=w2gPqH6kNJU&feature=related)
[http://www.youtube.com/watch?v=fMz6fDGBnA4](http://www.youtube.com/watch?v=fMz6fDGBnA4)

Anyway, the mixer in Ardour, tuner in rakarrak, etc, all show that there is a signal coming through from my USB microphone. It doesn't look like there is any latency or anything. For some reason though, even though everything is connected to (system: playback 1) and (system playback 2) it still does not produce sound through my speakers or headphones if I plug them in.

Please help, I have been trying to use programs other than audacity for recording my guitar, or even effects in realtime.

---

### Post by jejeman on 2011-11-08
Give us output from
```
aplay -l
```
```
cat .jackdrc
```

---

### Post by Tallguitarguy on 2011-11-09
For aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [C-Media USB Audio Device   ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
``` and for cat .jackdrc
```
/usr/bin/jackd -t2000 -dalsa -dhw:1 -r44100 -p128 -n3
```(C-Media USB Audio Device is my microphone btw, no idea why it shows as a playback device)

---

### Post by jejeman on 2011-11-09
Looks like you are using hw:1 as duplex. You need to separate capture and playback devices, by changeing playback to use hw:0 and capture to use hw:1.

---

### Post by Tallguitarguy on 2011-11-09
What you just said really seemed to make alot of sense, but I just tried changing to capture only which didn't work so here's a picture of what I've got at the moment.

---

### Post by jejeman on 2011-11-09
If you set just capture you can't have any playback, just recording.
You need to set duplex. And than to set separate cards for capture and playback.
Maybe you should first set to use onboard card for both. If that works, then set captureing to usb mic.

---

### Post by Tallguitarguy on 2011-11-09
The only way JACK runs without any xruns is if "Interface" is set to hw:1. If I set "Input Device" to the mic aswell, but leave "Output Device" as default, it will start but still no sound(as would be expected). But if I change "output device" to anything else, "interface" will not be able to be chosen.

What I can choose from for interface, input, and/or output:
HDA ATI SB
STAC92xx Analog
C-Media USB Audio Device
USB Audio
(default)

---

### Post by jejeman on 2011-11-09
I've created similar setup as yours using usb webcam which has microphone on it. Jack is running fine with this options

```
/usr/bin/jackd -dalsa -r48000 -p128 -n3 -S -D -Chw:1,0 -Phw:0,0 -i2 -o2
```One can see here that I've set:
periods 3 (because of usb device)
duplex
capture hw:1,0
plaback hw:0,0
input channels 2
output channels 2

When you specify input and output device, the interface field is greyed out. So it is not important what have you selected there.
In your setup you should select:
hw:1,0 for capture (USB Audio)
hw:0,0 for playback (STAC92xx Analog)

---

### Post by Tallguitarguy on 2011-11-09
I just tried that and it just says, "Failed to start JACK" and I tried fiddling with the other things like the input and output channels, but everything but what I originally had causes JACK to fail.

---

### Post by sgx on 2011-11-10
> **Tallguitarguy said:**
> The only way JACK runs without any xruns is if "Interface" is set to hw:1. If I set "Input Device" to the mic aswell, but leave "Output Device" as default, it will start but still no sound(as would be expected). But if I change "output device" to anything else, "interface" will not be able to be chosen.

What I can choose from for interface, input, and/or output:
HDA ATI SB
STAC92xx Analog
C-Media USB Audio Device
USB Audio
(default)
Hi, I have had qjackctl 'Interface' grayed out for years. Choosing your Input Device and Output device are the important part. Don't
worry about xruns until you have established the proper connections.
I would follow jejeman suggestion to choose duplex, and get the motherboard sound working in and out, then configure the usb mic input. I would also google that device to see if it is highly regarded among users of other operating systems.
Cheers

---

