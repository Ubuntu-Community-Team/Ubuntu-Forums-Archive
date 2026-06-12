---
title: "line 6 guitarport xt"
date: 2009-12-29
forum: Ubuntu Studio
---

### Post by AnarchistForPrez on 2009-12-29
Hey guys, I am new to Ubuntu and am trying to setup my line6 guitarport xt. currently i have it recognized by my system as an audio input. i have tried several different means of getting it to work properly (via Jackrack, Wine, etc.) but as of now it plays through my headphones but only as a low sharp buzzing noise. assumably i could fix this in a software interface by editing tone, etc. i have tried using jack but jackrack opens and closes, jackcontrol gives me an error message citing jackd as a problem. however it is installed and as near i can tell works. i downloaded line6-usb-source through the terminal and was able to open gearbox this way. yet, still it just buzzes, no effects. anybody have any suggestions? any help would be greatly appreciated.

---

### Post by JC Cheloven on 2009-12-30
Hi, I'm at all unsure about what "line6 guitarport xt" is. I assume it's an audio device. Is it usb? Is it [supported by alsa]("http://www.alsa-project.org/main/index.php/Matrix:Main")? Is it firewire? Is it ffado supported?

Perhaps if you give more details, or even a link to the product, you'd better chances to get an answer...

---

### Post by dawiba on 2009-12-31
Do you have a Guitarport or a PodXT?

Are you using regular Ubuntu or UbuntuStudio?

How have you connected to your computer?

---

### Post by AnarchistForPrez on 2010-01-05
I have a guitarport xt, not the podxt. it is a usb device. it looks like this <img src="[http://www.americanmusical.com/ProductImages/Large/p39539.jpg](http://www.americanmusical.com/ProductImages/Large/p39539.jpg)"/>.
i have ubuntustudio installed and when i power the computer down i see the ubuntustudio screen.
i have been able to get jack and jackrack working properly, but i still cannot get them to recognize the guitarport correctly, i get a garbled sound with no ability to mix, edit, or add effects. the system recognizes it as sound input device, but without being able to run it through an amp modeling program properly, it's just a useless hundred dollar investment. I have ladspa and alsa all set, and still nothing.
i decided when i couldnt run the guitarport xt properly through jackrack with rosegarden to try to use wine instead. so i installed the gearbox prog that came with it, and to try to run it in wine. same results, garbled noise, no control. through tenacious research i have found that wine does not offer the proper usb support to do this.
i would very much like to run a home studio through ubuntu, or if need be another linux distro. however this device is my only means, and i have come to a wall. if i cant figure it out i will have to reinstall... vista ::shudders:: and run a dual boot. the issue there is the amount of space it would take up on my hard drive. recording while simultaneously playing back and processing softsynths demands alot from a pc and the master copies of songs themselves become very large files.

---

### Post by dawiba on 2010-01-06
Sorry, I hadn't realised the Guitarport was now an XT model.

I don't think you'll be able to use it as it needs the software (Windows or Mac only) to run. I hoped you had a PodXT as I might have been able to help you get it working.

I guess using it under Wine is your best bet, but I don't use that myself so can't help you there. Perhaps someone else can offer help with that.

Good luck

---

### Post by AutoStatic on 2010-01-06
AnarchistForPrez, I fear that your device is unsupported: [http://www.tanzband-scream.at/line6/driverdocs.pdf](http://www.tanzband-scream.at/line6/driverdocs.pdf)

Page 4, chapter 2.

But what do the following commands (in this order) do with the device plugged in:
**lsusb**
**sudo modprobe line6usb**
**lsmod | grep line6**
**aplay -l**
**amidi -l**

It should look a bit like this:
```
jeremy@soushi:~$ lsusb | grep -i line6
Bus 005 Device 002: ID 0e41:5051 Line6, Inc.
jeremy@soushi:~$ lsmod | grep line6
line6usb               98156  0 
snd_pcm                91912  6 snd_usb_audio,line6usb,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_rawmidi            27104  3 snd_usb_lib,line6usb,snd_seq_midi
snd                    77576  24 snd_usb_audio,snd_usb_lib,line6usb,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
jeremy@soushi:~$ amidi -l
Dir Device    Name
IO  hw:1,0,0  Line 6 Pocket POD MIDI 1
```

I have a pocketPOD which only has MIDI, no USB sound so **aplay -l** does not apply for my situation.

---

### Post by Monkeys Worship Me on 2010-02-15
> **dawiba said:**
> Sorry, I hadn't realised the Guitarport was now an XT model.

I don't think you'll be able to use it as it needs the software (Windows or Mac only) to run. I hoped you had a PodXT as I might have been able to help you get it working.

I guess using it under Wine is your best bet, but I don't use that myself so can't help you there. Perhaps someone else can offer help with that.

Good luck

I am new as well (<two weeks Ubuntu user), I own a PodXT Live, and I am having a similar problem: I was able to load the Gearbox program using Wine, but it does not recognize the USB or the MIDI connection.  Through the sound preferences settings, I am able to record from and playback through the USB connection; I haven't tried the MIDI connection, although the computer does recognize the M-Audio Uno USB port.

[to anybody reading this:]  I don't know what all is available as far as Windows emulation, but would any one other than Wine be more compatible for running general Windows programs requiring USB devices?   The Line 6 Gearbox program is not required to run the PodXT, but it is essential for downloading effects settings directly to the device, plus the Line 6 Monkey program searches for and downloads any software updates for the effects processor.  If any more explanation of the device and programs I described are necessary, please let me know.

---

### Post by Zimmer on 2012-03-13
> I am new as well (<two weeks Ubuntu user), I own a PodXT Live, and I am having a similar problem...

In case you are still having problems... I currently use the PODXTLive in a virtual machine running XP, using 'ORACLE' VMware(version 3, I think, as I have not upgraded to version 4 )and the additions pack that provides USB support... works fine ..

Looking at the moment for a way to get WINE to recognise the hardware.....

---

### Post by sgx on 2012-03-13
[http://packages.debian.org/sid/line6-usb-source](http://packages.debian.org/sid/line6-usb-source)

This can help some Line6 users. I would also try the 1.4x version of wine, or Crossover, to help with Gearbox

But a Fender Mustang 1 usb amp/interface, for $100 or less, is great for linux guitarists. In addition to plug/play simplicity, Amplitube, Guitar Rig, and a plethora of fine linux and windows fx apps and plugins work with it. The hardware itself is a joy to use, inhabits qjackctl by name, and a software editor is available called Plug

[http://pkgs.org/debian-sid/multimedia-main-i386/plug_1.0-0.0_i386.deb.html](http://pkgs.org/debian-sid/multimedia-main-i386/plug_1.0-0.0_i386.deb.html)

If finances are a problem, sell/trade Line6, if linux is in your future.
Cheers

---

### Post by sgx on 2012-03-14
In qjackctl setup page, Input Devices  >
click  > and see what are available.

the output of

cat /proc/asound/cards   and

arecord -l  should also detect and list available devices

Choose your regular soundcard for the output device.

Periods/Buffer setting in qjackctl should be 3

A usb hub should not be used.  lsusb can list detected devices.
------------------------------------------------------------------
If there is no sign of life,

[http://www.tanzband-scream.at/line6/INSTALL](http://www.tanzband-scream.at/line6/INSTALL)

This may require a compile operation, remove what you installed, using synaptic, and read the compile
steps at this link, scroll down to 'source installation' paragraph.

and a good how2

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Cheers

---

