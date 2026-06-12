---
title: "Piano player"
date: 2009-01-03
forum: Ubuntu Studio
---

### Post by axelsax on 2009-01-03
Hi,

I've just switched to Ubuntu 8.04 :o and I'd like to play piano like I've done previously on Mac OS X with GarageBand.
I use an M-Audio keyboard (Keystation 49e) connected to my Mac via USB to drive GarageBand where different type of pianos can be selected (an eventually record the sequence).
Could you suggest a software with similar capabilities for Ubuntu?
I had a look at Synaptic and google but I didn't found a solution.:confused:

Thank you in advance

---

### Post by babarosa on 2009-01-04
Hi axelsax,

possible solutions are

[LIST]
[*]Rosegarden (Sequencer) + Fluidsynth (Soundfont Player) + Soundfont
[*]Muse + Fluidsynth + Soundfont
[/LIST]

Get the latest rosegarden from [www.getdeb.net](www.getdeb.net), Fluidsynth should come with it, get FluidR3_GM.sf2, muse v0.9 can be downloaded from [https://launchpad.net/~weboide/+archive](https://launchpad.net/~weboide/+archive), fluidsynth comes with it.

You also can use wine and a windows software like reaper with a dedicated piano synth, but you have to deal with latencies too large for playing live.

I use muse\\:D/ and it works very well.

Regards, Michael

---

### Post by plivvit on 2009-01-05
Hi,
I have a M-Audio 49e too. I would like to test if it works. And to see if the keyboard is properly installed. Which application can be used best to do so?
Tx so much.

---

### Post by xeth_delta on 2009-01-10
> **plivvit said:**
> Hi,
I have a M-Audio 49e too. I would like to test if it works. And to see if the keyboard is properly installed. Which application can be used best to do so?
Tx so much.

I just got an M-Audio 49e myself today. It is working really well. I use Rosegarden+Timidity. Just make sure you have the snd-usb-audio module loaded into the kernel:

```
lsmod | grep snd
```

if it is not loaded you can load it yourself:
```
sudo modprobe snd-usb-audio
```

If you don't have the module, you can compile it yourself, it is not very difficult. I can help you out with some indications, should you need them.

To check if your device had been recognized have a look in the output of:
```
dmesg
```
and
```
lsusb
```
To check if your device is sending any data:
```
cat /dev/midi1
```
when you press a key, you should be able to see some characters being sent to the terminal screen.

---

