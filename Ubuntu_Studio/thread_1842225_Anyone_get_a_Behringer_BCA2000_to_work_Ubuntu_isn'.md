---
title: "Anyone get a Behringer BCA2000 to work? Ubuntu isn't even detecting it."
date: 2011-09-11
forum: Ubuntu Studio
---

### Post by bikerbomber on 2011-09-11
I have dug around the internet for a couple of hours already trying to find the answers, but I haven't found anything on how to get it to work. I am a little new with Linux and so that might be hurting me as well. Can anyone shoot me some advice?

---

### Post by Sylos on 2011-09-11
Looking on google isnt too promising. Seems it might not be a runner with alsa but we might as well try.

First off, is it detected at all?

With it plugged in type the following command and post the output:

```
lsusb
```

This will tell us if it is being detected as a USB device. If it doesnt show up first time, try leaving it plugged in and cycling the power on and off.

---

### Post by mue.de on 2011-09-11
I have it on my todo-list (for years now), my behringer runs under Windows with firewire-I/F. It's connected with an PCI-Firewire I/F to a siemens desktop, where i have natty narwhal running: 
I'm still interested in finding a linux solution: I'll review my (year old) notes an post the experiences.

mue.de

---

### Post by bikerbomber on 2011-09-11
I did try the power-cycle and Jack nor ALSA saw it, however, It did show up with the 

lsusb 

jonathan@jonathan-OptiPlex-GX620:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 413c:2010 Dell Computer Corp. 
Bus 004 Device 002: ID 413c:1003 Dell Computer Corp. Keyboard Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1397:00bb BEHRINGER International GmbH    ):P
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

So I am guessing it is a driver issue at this point. I have a copy of the drivers, but have been unsuccessful at getting them installed. Tired Wine and only got to where it states, *"Please follow the instructions from the hardware manager. After the driver has been installed windows will tell you." (Press continue)*  

When I press continue nothing happens. I also tried opening up the exe to get any dll files, but that didn't work either.

---

### Post by sgx on 2011-09-11
Hi, if you have it installed in windows, there may be an install log on the hard-disk, which you could use as a map to copy the files manually to the /home/username, and .wine folder equivalents. I did
that with some Native Instruments demos. Like sorting through
the aftermath of a tornado! :p

---

### Post by bikerbomber on 2011-09-11
I tried extracting the files manually but was unable to do so. It is an exe file and archive manager says it cannot open it. Is there another avenue?

---

### Post by jejeman on 2011-09-12
what is the output of
```
aplay -l
arecord -l
```

---

### Post by bikerbomber on 2011-09-12
I got this after typing those commands:
jonathan@jonathan-OptiPlex-GX620:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH7 [Intel ICH7], device 0: Intel ICH [Intel ICH7]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH7 [Intel ICH7], device 4: Intel ICH - IEC958 [Intel ICH7 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jonathan@jonathan-OptiPlex-GX620:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: ICH7 [Intel ICH7], device 0: Intel ICH [Intel ICH7]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH7 [Intel ICH7], device 1: Intel ICH - MIC ADC [Intel ICH7 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH7 [Intel ICH7], device 2: Intel ICH - MIC2 ADC [Intel ICH7 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH7 [Intel ICH7], device 3: Intel ICH - ADC2 [Intel ICH7 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

----------------------------------------------

No behringer listed here though.

---

### Post by bikerbomber on 2011-09-13
Ok, I got my driver CD here. And I have a number of files that could be useful. Here is a list of the files in the 'drivers' section of the cd:

bca2Kasio.dll
bca2Kcpan.exe
bca2Ksrvc.exe
bca2Ksrvst.dll
bca2Ktray.exe
bca2000.inf
bca2000.sys
bca2000ldr.sys
bcaloader.inf


tried running the exe under wine. Didn't seem to do anything

---

### Post by sgx on 2011-09-13
Did you try the driver at their website?

[http://www.behringer.com/EN/Products/BCA2000.aspx](http://www.behringer.com/EN/Products/BCA2000.aspx)

The device is to be plugged in during the install, but
turned off, until the installer prompts you to turn on the power.
Do you have the proper power supply? Have you tested the installer and the hardware on XP?
Cheers

---

### Post by bikerbomber on 2011-09-13
Yes sir. I tried installing it powered down and powered up just to see if it would work differently. Both have the same result I posted about earlier. I really don't want to have to use winbox but it is beginning to look that way. 

And yes, that was the driver I tried the first time. I found the CD with the original drivers hoping they might work, but no avail...so far. 

:confused::confused::confused:

---

### Post by miggols99 on 2011-09-14
First of all, using Wine to install the Windows drivers will not work. Wine is made for running Windows programs, not for installing drivers.

It looks like the drivers for the Behringer BCA2000 are proprietary so they will only work if someone reverse-engineers them.

USB 2.0 audio interfaces normally have problems with Ubuntu as they are not class compliant. Firewire (check first) and just about every USB 1.1 audio interface should work.

---

### Post by westie457 on 2011-09-14
Hi.

Have you tried installing the drivers with ndiswrapper? 

Ndiswrapper allows you to install Windows XP drivers. Just point it at the .inf file on the cd and it should do the rest for you.

---

### Post by jejeman on 2011-09-14
Ndiswrapper is for wifi cards.
(Network Driver Interface Specification)wrapper.
> Although ndiswrapper is intended for wireless network cards, other devices are known to work: e.g., ethernet cards, USB to serial port device, home phone network device etc. 

---

### Post by bikerbomber on 2011-09-15
Yeah, I knew wine was for running programs only, but I thought it was worth a shot. I will give ndiswrapper a try, I don't know if I have anything to lose at this point. I'm bummed this isn't working.

I feel like I wasted money buying this dang interface, I guess I had too much confidence in Ubuntu. 

I heard one guy got it working through a winbox. I have never used winbox though, is it difficult to configure? 

I'll let you folks know if ndiswrapper works or not.

---

### Post by sgx on 2011-09-17
I tried unshield and cabextract on this driver file:

BCD2000-driver-setup-1-1-1-0.exe  but they did not detect
either type of file, installshield, or cabinet.

You could ask Behrs tech support to send or point you to a log file listing where all the components get installed, then if you can unpack,
or install on some windows version somewhere,
copy them manually to the same spots in .wine and /home/username.

It is a great looking device!

if you have a windows partition, you could try a wubi ubuntu install,
and link the files from the 'host' (windows) partition, to the
wubi ubuntu areas.

---

### Post by bikerbomber on 2011-09-18
Hmmm, I guess I can try this. I'm not sure how it would make it work with Ubuntu, but I don't have much else to lose at this point. I'll let you know.

---

### Post by audiomike on 2012-06-04
Are anybody still interested in a Linux driver for the BCA2000?

I am trying to write one.

Audio Mike

---

### Post by sgx on 2012-06-04
Its a common and useful product, so making it work will attract
new users, inspire more purchases, and no doubt improve
your coding, which may lead to unforeseen benefits, and future
products.
Cheers

---

### Post by maheha on 2012-06-28
Wow sounds amazing!!!! With all the windows compatability issues with this mixer I think you can revive a brilliant pice of hardware.

I really hope you make it! If you need someone to do some testing I am in!

Yours
Mathias

maheha at a gmail . something :D

---

### Post by Masterblah on 2012-07-30
Hey Audio Mike, i just registered on this forum to give a very big thumbs up ... 

The BCA2000 is a great device, if you manage to make some drivers or it, i will be forever in your debt ... i still run windows only to use that sound card ... i love it .. not windows hehehe 

Go Linux users, and good luck to you Audio Mike ;)

:guitar:

---

### Post by yug23 on 2013-03-08
> **Masterblah said:**
> Hey Audio Mike, i just registered on this forum to give a very big thumbs up ... 

The BCA2000 is a great device, if you manage to make some drivers or it, i will be forever in your debt ... i still run windows only to use that sound card ... i love it .. not windows hehehe 

Go Linux users, and good luck to you Audio Mike ;)

:guitar:

I would also love to have this working on linux! Please post any updates here.

---

### Post by btsimonh on 2013-12-09
Anyone still interested in writing a driver?  I have done a lot of investigation; i intend to try to get it going in Win7 64 bit, but the info i have would be useful for a linux driver too.
Simon

---

### Post by stefbu on 2014-06-30
> **btsimonh said:**
> Anyone still interested in writing a driver?  I have done a lot of investigation; i intend to try to get it going in Win7 64 bit, but the info i have would be useful for a linux driver too.
Simon
Yes please, that would be a great thing to revive this good piece of hardware!

---

### Post by brianmc on 2014-07-11
There's various gripes about this box over an eight-year period. Behringer did something weird with the box because Windows doesn't play nicely with multi-input USB 2.0 devices. Hence the closed-source custom drivers. A lot of reverse-engineering would be required to get ALSA support for this; that's not too-likely to be undertaken unless you've a spare one to hand over to someone with the experience to do the relevant hacking (not me, I'm afraid!)

---

