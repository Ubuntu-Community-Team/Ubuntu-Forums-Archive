---
title: "Pulling my hair out over midi out"
date: 2015-11-15
forum: Ubuntu Studio
---

### Post by bigbrother on 2015-11-15
Im trying to get a simple setup going where I can use my netbook as a sequencer for my drum machines and synth while I jam on the other one. But I can not figure out midi out. Ive got an m-Audio usb to MIDI device and it shows up as Midiman M-Audio Uno 0763:0150 when I run lsusb and Ive tried a few different daws but nothing will find the midi out. Not new to linux but linux audio has always seemed like a total mess to me so I'll happily tell you anything you need just ask. Its a stock ubuntu studio install of the newest release that I installed 3 hours ago.

---

### Post by zequence on 2015-11-15
You probably need to install the non-free package **midisport-firmware**.  You will know if it works when it shows up in *qjackctl -> Connect  -> ALSA* (jack itself does not need to be running).

To install the firmware, do this in a terminal:

```
sudo apt-get install midisport-firmware
```

---

### Post by jejeman on 2015-11-15
Plug it in.
give
```
amidi -l
```

---

### Post by CrocoDuck on 2015-11-15
I got one of [these]("http://www.m-audio.com/products/view/uno#.VkkQvJ5anQU") working few Ubuntu releases ago. The package suggested by zequence was needed.

> **bigbrother said:**
> ...linux audio has  always seemed like a total mess to me...

:lolflag: Well, it is pretty quirky indeed... with kernel drivers + daemons... multiple things to configure system-wise... But when you crack it you are all suddenly happy! And believe me, it is not even remotely hard as it was 10 years ago...

---

### Post by alexrosi on 2015-11-21
[COLOR=#000000]Plug it in.[/COLOR]
> [COLOR=#000000][FONT=Ubuntu Mono]amidi -l[/FONT][/COLOR]

---

