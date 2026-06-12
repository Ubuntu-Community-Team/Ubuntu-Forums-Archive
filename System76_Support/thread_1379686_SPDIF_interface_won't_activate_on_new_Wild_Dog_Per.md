---
title: "S/PDIF interface won't activate on new Wild Dog Performance"
date: 2010-01-12
forum: System76 Support
---

### Post by DonnyViszneki on 2010-01-12
Hi System76! I just got my new Wild Dog Performance machine with Ubuntu 9.10 pre-installed.

Problem: **No sound on S/PDIF** optical audio interface.

Exploring: I right clicked the volume control icon on my gnome panel, and clicked **Sound Preferences**. I clicked the **Profile drop-down list** and chose the profile **Analog Stereo Output.** This gives me sound output on the DAC. Phew, at least I can plug in my headphones now!

No profile or setting I have tried enables the S/PDIF optical audio interface. The digital settings available are **Digital Stereo Duplex (IEC958[B]**)[/B] and **Digital Stereo (IEC958[B]**) Output + Analog Stereo Input[/B].

Irrelevant detail: I am using the HDMI video output from my nVidia GeForce 9600 GT. I'm only listing this because I know HDMI transports audio, and although it seems pretty impossible to me that this could interfere in any way, I'm mentioning it because besides setting up my user account and connecting my keyboard and mouse, this is the only other thing I had done to my system and machine before seeing the problem.

**This problem was present "out-of-the-box"**, as they say, so I assume they should be easy to reproduce at System76. Here is the machine hardware spec as emailed to me when I placed my order:

```
1 x Wild Dog Performance (WIL-P5)
       Graphics 512 MB nVidia GeForce 9600 GT
       Hard Drive 160 GB SATA II 300 Mbps - 7200 RPM 8MB Buffer
       Hardware Warranty 1 Yr. Ltd. Warranty and 1 Yr. Technical Support
       Keyboard and Mouse no keyboard and mouse
       LCD Monitor no monitor
       Memory 4 GB - 2 x 2 GB - DDR3 - 1333 MHz
       Operating System Ubuntu 9.10 (Karmic Koala) 64 Bit Linux
       Optical Drive CD-RW / DVD-RW
       Portable Flash Drive no flash drive
       Processor Quad Core Q9550 2.83 GHz FSB 1333 MHz L2 12 MB
       Second Optical Drive no second optical drive
       Speakers no speakers
       Wireless no wireless
```

Thanks for reading, have a nice day

---

### Post by thomasaaron on 2010-01-13
There might be a pulseaudio issue with s/pdif. Please see...
[http://forum.boxee.tv/showthread.php?t=13040](http://forum.boxee.tv/showthread.php?t=13040)
...and...
[http://ubuntuforums.org/showthread.php?p=8655551](http://ubuntuforums.org/showthread.php?p=8655551)

However, I don't have an s/pdif device to test with here in my shop. If the above threads don't help you let me know. We may need to file a bug report on it and let the R&D guys have at it.

---

### Post by DonnyViszneki on 2010-01-13
Thanks for the tips. Trying the options given there, I still get no light coming out of the S/PDIF interface :(

I even managed to get my system to freeze hard when switching to the Analog 7.1 profile just to see if it would work :(

---

### Post by thomasaaron on 2010-01-13
OK. Please file a bug report on it at...

[http://launcpad.net/system76](http://launcpad.net/system76)

I'm gonna need the R&D guys to assist with this one.

---

### Post by Ed.Corcoran on 2010-08-31
I am having the same problem with no audio coming from the optical out. Has there been any progress on this?

---

