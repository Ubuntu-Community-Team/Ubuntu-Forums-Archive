---
title: "VirtualBox: Wrong Audio Sample Rate"
date: 2015-03-05
forum: Virtualisation
---

### Post by marseille2 on 2015-03-05
Hello, and thanks for looking!

I'm running VB 4.3.22 r98236 (ubuntu 14.04 host / win7 guest), and somehow... the sample rate has gone haywire. It wasn't this way on the initial install, but after reinstalling guest additions (trying to fix hardware acceleration) ... all sound is now super-slow, with a low pitch. How can I fix the sample rate?

Note: I have a few sound cards on the host, and switch between wired and bluetooth speakers):

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: UA700 [EDIROL UA-700], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


```

** Update: Some more information...**

I retraced some of my steps, and think that something happened when I had a USB audio inteface plugged in (then pulled it out at some point). Currently, if I disable onboard audio, and just use the external sound card... I'm able to get the right sample rate in VB, but the sound icon in Win7 guest is gone (have to access sound from Control Panel ... Also lost networking icon, have to access cmd > ipconfig to know what's going on). 

With onboard audio only, (and the output from graphics card -- but I don't use it), the sample rate is all wrong. Here's some info from the vbox log:

```
00:00:01.485210 Audio: Trying driver 'pulse'.
00:00:01.493925 Pulse: open **PCM_IN** rate=44100Hz channels=2 format=s16le
00:00:01.493970 Pulse: Requested record buffer attributes: maxlength=26460 fragsize=17640
00:00:01.496206 Pulse:  Obtained record buffer attributes: maxlength=26460 fragsize=8820
** 00:00:01.496251 HdaCodec: can't open in fmt(freq: 44100)**
00:00:01.496262 Pulse: open **PCM_OUT** rate=44100Hz channels=2 format=s16le
00:00:01.496273 Pulse: Requested playback buffer attributes: maxlength=26460 tlength=17640 prebuf=-1 minreq=-1
00:00:01.498485 Pulse:  Obtained playback buffer attributes: maxlength=26460 tlength=12348 prebuf=8824 minreq=3528
**00:00:01.498578 HdaCodec: can't open out fmt(freq: 44100)**
```

---

