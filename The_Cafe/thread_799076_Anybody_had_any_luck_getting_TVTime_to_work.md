---
title: "Anybody had any luck getting TVTime to work"
date: 2008-05-18
forum: The Cafe
---

### Post by Methuselah on 2008-05-18
I've never been able to get my TVTuner card to work with any other OS but windows using the provided driver disc. I tried it in FreeBSD and now I'm trying it in ubuntu and still no luck. I found the site below where the writer seems to be configuring the same hardware. I followed the instructions and tvtime still picks up no signal. I'm using Hardy and tuning NTSC/broadcast rather than cable.

Has anyone been successful with this?
I'm out of ideas.

[http://wiki.linuxhelp.net/index.php/TV_Tuner](http://wiki.linuxhelp.net/index.php/TV_Tuner)

dmesg | grep bttv

[   32.889082] bttv: driver version 0.9.17 loaded
[   32.889085] bttv: using 4 buffers with 2080k (520 pages) each for capture
[   32.889128] bttv: Bt8xx card found (0).
[   32.889155] bttv0: Bt878 (rev 17) at 0000:05:02.0, irq: 20, latency: 32, mmio: 0xe8200000
[   32.889591] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
[   32.889593] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
[   32.889614] bttv0: gpio: en=00000000, out=00000000 in=003ff502 [init]
[   32.889955] bttv0: tuner type=2
[   32.889956] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   32.890573] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   32.891208] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   32.946268] bttv0: registered device video0
[   32.946284] bttv0: registered device vbi0
[   32.946297] bttv0: registered device radio0
[   32.946318] bttv0: PLL: 28636363 => 35468950 .<4>Driver 'sr' needs updating - please use bus_type methods
[   32.979290] input: bttv IR (card=34) as /devices/pci0000:00/0000:00:1e.0/0000:05:02.0/input/input7
[   97.693831] bttv0: PLL can sleep, using XTAL (28636363)

---

### Post by Xerp on 2008-05-18
Yeah, TVTime worked out of the box for me.

00:0c.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
00:0c.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)

I even got more channels than normal :)

---

### Post by Methuselah on 2008-05-18
Just my luck.
For me, it scans and just reports no signal for all the channels.

---

### Post by Ocxic on 2008-05-18
try turning off signal detection

---

### Post by Methuselah on 2008-05-18
Tried that...I just get white noise instead of a blue screen.

---

### Post by Methuselah on 2008-05-19
Woohoo...extensive googling bore fruit.

[http://ubuntuforums.org/showthread.php?t=45220](http://ubuntuforums.org/showthread.php?t=45220)

I ended up back on the ubuntu forums from another site.
Now I'm picking up channels! 
But no sound unfortunately.

That's what I have to work on next.
If anyone has any experience here I'm all ears.

---

### Post by Methuselah on 2008-05-19
Yeah, I'm all set...CD in was muted.
The card refuses to set as 35.
It ignores the modprobe options and it autodetects as 34.
35 was recommended at the sites I checked.

---

### Post by adrian.todireanu on 2008-12-29
leave it card=34 just put tuner=43
[GO HERE AND SOLVE IT]("http://ubuntuforums.org/showthread.php?t=647129")

---

