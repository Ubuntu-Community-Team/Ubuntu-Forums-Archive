---
title: "audio kontrol one problems maybe jack? or patchage?"
date: 2011-10-26
forum: Ubuntu Studio
---

### Post by rt-guitar on 2011-10-26
Okay maybe a noob question but I hope not, if it is then I am truly sorry and point me to a link. I switched to ubuntu about two or three years ago (screw vista), and i have lived happily ever after with it instead of windows. Fixing a large majority of my own and my friends problems with switching to ubuntu this is my first post on the forums!!!!
Now for the problem
I started with 10.10 and all was good then i tried my audio kontrol one sound card with jack and rakarrck so I thought I just wasnt getting it so I gonna wait till later and try again. installed ubuntu studio package and nothing was working,ubuntu sees the card says it's there and sound comes out but I can't record or use effects, tried to connect just about every connection i can see. This whole project has taken almost three days and no recording. I know the card works if i put it in the mac it fires right up in logic....worked in windows to. I read the card is now normally supported since like 10.04. Finally I just installed 11.04 ubuntu studio full download not just packages installed into ubuntu. 11.04 with unity doesn't work and i upgraded to 11.10 with xfce and still nothing is happening

hopefully im just a noob and there is an easy fix (tried adding myself as audio user when i installed packages but not the full studio desktop)

If there is more i should post or some readings that would help I gladly will 
thank you for your time

---

### Post by rt-guitar on 2011-10-26
:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 2222:3100 MacAlly 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 17cc:0815 Native Instruments Audio Kontrol 1
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by rt-guitar on 2011-10-26
here is sudo aplay -l

~$ sudo aplay -l
[sudo] password for zendojo:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AudioKontrol1 [Audio Kontrol 1], device 0: Audio Kontrol 1 [Audio Kontrol 1]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

trying to find more commands that may help

---

### Post by sgx on 2011-10-26
Hi, I would start by shutting off everything you don't need for audio,
in the bios. Take notes. Networking, acpi, power management, bluetooth,
webcam yada yada. Unplug every usb device, and don't use a usb hub.

Make a working jackd/qjackctl setup with your soundcard/chip

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

Use the 4th link and last link at the wiki, for screenshots
to set up jackd and qjackctl, and install wine and wineasio,
and run the command

regsvr32 wineasio.dll.

Once this works, plug in the RK in each usb port, between boots, checking lsusb each time, and check in qjackctl setup page, click the 
> widgets by

Input device  >
Output device  >

for the detected sound devices.

I would also do a fresh install of ubuntu studio 10.04 as the
stable basis for your tests and future daw. Uninstall pulseaudio
and libpulse using synaptic, if they exist.

put this in line google:

linux kernel "rig kontrol" 

for a little read.
Cheers

---

### Post by rt-guitar on 2011-10-26
First off thanks for a start all the stuff I see for the audio kontrol one is old news.

should I install just 10.04 ubuntu i have a dual boot half 10.04 and half 11.04 right now. It was already a clean install so i can try any distro at this time will a 10.04 ubuntu studio not help much?

Still reading through your wiki links thanks again!

---

### Post by rt-guitar on 2011-10-27
I know a virtual machine and wine are different but will i be able to use the rt kernel under wine or will that defeat the purpose?

---

### Post by Totalchaos on 2011-10-27
> **rt-guitar said:**
> I know a virtual machine and wine are different but will i be able to use the rt kernel under wine or will that defeat the purpose?

yes you will. But let me warn you about that i was having trouble with resent dev version of wine, so just if you can't reach the needed resilt, try it with some different version of wine (1.3.20 is the best hit for me now)

---

### Post by sgx on 2011-10-27
> **rt-guitar said:**
> First off thanks for a start all the stuff I see for the audio kontrol one is old news.

should I install just 10.04 ubuntu i have a dual boot half 10.04 and half 11.04 right now. It was already a clean install so i can try any distro at this time will a 10.04 ubuntu studio not help much?

Still reading through your wiki links thanks again!
No need for the whole studio, for many it is better to add just
what you know you will use. I would also avoid all 3d drivers
and windowing projects at this point. Simplicity is the gate
to excellence. :)
To me, it's good luck to always have a few working setups,
one .rpm based, one .deb based, and a puppy studio or two.

[http://www.bandshed.net/AVLinux.html](http://www.bandshed.net/AVLinux.html) is a good one, and has
the liquorix kernel available, as well as a really good
default kernel.

---

