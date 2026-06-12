---
title: "No M-Audio Fast Track Input, no readable system output in JACK"
date: 2010-05-06
forum: Ubuntu Studio
---

### Post by Monona on 2010-05-06
&#65279;I'm having trouble getting input on an M-Audio Fast Track Pro.  The input doesn't seem to be on in the device.  There's no readable system output on JACK either.  I can get output to headphones, though.

I'm on Hardy 8.04.

How can I get a mic in?

---

### Post by AutoStatic on 2010-05-06
Hello Monona, the M- Audio Fast Track Pro is for the most part an USB1 class compliant audio device. Could you post the output of **aplay -l** and **arecord -l** ? And what are your current JACK settings? Could you post a screenshot or give the output of **cat ~/.jackdrc** ?

---

### Post by Monona on 2010-05-06
Playback seems to be working fine.  As in, I get the output from the Fast Track Pro using jack.  

It might be hardware related, since I'm not getting signal lights on the inputs.  Ubuntu seems to be recognizing it ok:

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Pro [FastTrack Pro], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Pro [FastTrack Pro], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Pro [FastTrack Pro], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Pro [FastTrack Pro], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

:~$ cat ~/.jackdrc
/usr/bin/jackd -R -dalsa -r44100 -p128 -n2 -D -Chw:1 -Phw:1

---

### Post by AutoStatic on 2010-05-07
Thanks! I should've posted this screenshot right away: [http://www.joegiampaoli.com/blog/wp-content/uploads/2009/11/qjackctl.jpg](http://www.joegiampaoli.com/blog/wp-content/uploads/2009/11/qjackctl.jpg)

I don't own a Fast Track Pro myself but apparently you need to specifically indicate a subdevice for this device in order to get any inputs. So for the input device you need to enter hw:1,1 and for the output device just hw:1

---

### Post by Monona on 2010-05-07
Thanks, Autostatic!

That seems to have gotten it working.

---

### Post by Bristen Bourque on 2011-03-08
> **AutoStatic said:**
> Thanks! I should've posted this screenshot right away: [http://www.joegiampaoli.com/blog/wp-content/uploads/2009/11/qjackctl.jpg](http://www.joegiampaoli.com/blog/wp-content/uploads/2009/11/qjackctl.jpg)

I don't own a Fast Track Pro myself but apparently you need to specifically indicate a subdevice for this device in order to get any inputs. So for the input device you need to enter hw:1,1 and for the output device just hw:1

Hi, since I'm a Linux newbie, I was wondering if someone would be kind enough to explain what entering "hw:1,1" means?  As for me, Fast Track is recognized and I have output, but no input...

Thanks,
  Bristen.

---

### Post by sgx on 2011-03-09
Hi, on my maudio 24/96, both windows and linux see there are two separate record/play possibilities, and the output of aplay -l  is

card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

To list your linux kernel modules:

lsmod

the output on my setup includes  snd_ice1712

In qjackctl setup, both input device and output device > I have 

M Audio Audiophile 24/96, and ICE1712 multi

One is hw:0,0 the other is hw:0

Now in my textfile .jackdrc

/usr/bin/jackd -P69 -dalsa -r44100 -p128 -n2 -D -Chw:0,0 -Phw:0,0

Chw:0,0  is Capture Hardware0,0
Phw:0,0  is Playback Hardware0,0

These relate to the Input device > and Output device >
settings in qjackctl, which outputs the text file .jackdrc,
when you save you settings.

So you find what your system sees, then make your settings.
The input and output choices can be different devices, and each system
may vary, but have common denominators to help us sort things.

Cheers

---

### Post by Pablo_F on 2011-03-09
To sum up,

hw:1,1 means card 1, device 1

A card can have more than one so called "device".

*arecord -l* lists capture card and devices (and subdevices).
*aplay -l* lists playback card and devices (and subdevices).

I don't think you have to worry about subdevices. 

There are cards with a unique device which can do capture and playback at the same time through several ports (duplex). 

There are cards with several devices, and some of them can be duplex, and some only capture, and some only playback, and through different ports, analog or digital.

So, take a look at the terminal output of *arecord -l && aplay -l*

---

### Post by Bristen Bourque on 2011-03-09
> **Pablo_F said:**
> To sum up,

hw:1,1 means card 1, device 1

A card can have more than one so called "device".

*arecord -l* lists capture card and devices (and subdevices).
*aplay -l* lists playback card and devices (and subdevices).

I don't think you have to worry about subdevices. 

There are cards with a unique device which can do capture and playback at the same time through several ports (duplex). 

There are cards with several devices, and some of them can be duplex, and some only capture, and some only playback, and through different ports, analog or digital.

So, take a look at the terminal output of *arecord -l && aplay -l*

Ok, here's what I get:

[INDENT]**** List of CAPTURE Hardware Devices ****
card 0: Track [Fast Track], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
[/INDENT]

[INDENT]**** List of PLAYBACK Hardware Devices ****
card 0: Track [Fast Track], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/INDENT]

My issues could very likely simply be due to the fact that I've used so little of Ubuntu... a few years back, I experimented (and joined these forums) with some success... I've found however things to have gotten incredibly better since then... was hoping to use "Ubuntu Studio" (what got me to try Ubuntu again).  However, I have an M-Audio FastTrack USB Sound Card, and I've seen to have read most people having a hard time with that...

Here is my current situation... it appears like I can have sound when I play a YouTube video, no problem.  If I look at "Sound Preferences" dialog, there is an "Input Level" meter there... when I have my guitar plugged into the USB sound card, I see the meter move... however, if I try to record anything in Audacity for example, I don't get anything... or if I try to use Rakarrack, I also don't get anything.

Is my problem more related to understanding configuration, JACK and such?

Hopefully I'm not being a burden to anyone... even though I know Windows very well, I'm very, very green with Ubuntu...

Thanks,
  Bristen.

---

### Post by Pablo_F on 2011-03-09
Hi Bristen,

> Is my problem more related to understanding configuration, JACK and such?

Yes. 

Summarizing, in ubuntustudio there are two sound servers, pulseaudio and jack.


Sound servers or systems such as jack or pulseaudio manage audio data between the driver and the applications, making possible, for example, that two or more applications can make sounds at the same time, while none of them is talking directly to the driver.

Your cards are supported by alsa kernel modules, i.e., the drivers.

Gnome sound preferences is a pulseaudio frontend and it has nothing to do with jack. Don't get confused with this.

We normally use pulseaudio or jack depending on what we want to achieve. Pulseaudio is for "desktop" use and Jack is for the audio studio. See [1] for a very well informed (and technical) explanation in Lennart's blog (Pulseaudio developer) and [2] for jack official documentation. Don't miss the faq.

Music production apps, such as qtractor, ardour and many more depend on jack to capture and playback audio. They can't be used with pulseaudio. Multimedia players such as rhytmhbox or the adobe flash player work with pulseaudio by default, but most of them can be made "jack-aware". See [3] to know how (it depends on the case).

Eventually you will want to make music, then you need jack and you don't need the sound preferences.

Now, you have two audio cards. The Fast Track and the onboard. The Fast Track has a unique device (device 0) which is used for capture and playback (see below). In this case, you don't need to specify an input device and an output device separately in the jack setup. It is enough if you choose the right card in the "Interface" field

```
    **** List of CAPTURE Hardware Devices ****
    **card 0**: **Track** [Fast Track], **device 0**: USB Audio [USB Audio]

    **** List of PLAYBACK Hardware Devices ****
    **card 0**: **Track** [Fast Track], **device 0**: USB Audio [USB Audio]
```
    
The confusion grows when cards are given different index numbers by alsa. Now, the Fast Track is number 0. In the following computer boot
it could be number 1. You need to avoid this! In qjackctl's setup call the card by name, not by number. In the interface field, write down: 

**hw:Track**

instead of hw:1 or hw:0 which you would need depending on the way the wind may blow. 

Anyway, if you don't intend to use the onboard at all is a good idea to disable it in the BIOS.

You also will want realtime mode. Make sure that your user has rtprio and memlock privileges. Check 

**ulimit -r -l**


[1] [http://0pointer.de/blog/projects/when-pa-and-when-not.html](http://0pointer.de/blog/projects/when-pa-and-when-not.html)
[2] [http://jackaudio.org/](http://jackaudio.org/)
[3] [http://www.linuxmusicians.com/viewtopic.php?f=19&t=2507&p](http://www.linuxmusicians.com/viewtopic.php?f=19&t=2507&p)


EDIT:

Some specialized distros leave out pulseaudio so they are much more easy to get going. If you are used to gnome and like it, [Tango Studio]("http://tangostudio.tuxfamily.org/en/tangostudio") is highly recommended.

Cheers! Pablo

---

### Post by Bristen Bourque on 2011-03-09
Wow Pablo, thank you for being so kind and providing all this information... one thing that hasn't changed in the 3 years I've been away from Ubuntu, is the community seems to be as nice as ever (or more!).  I will review all the information and links you have so kindly provided.

One question before I dive into all of this... How would I find out the differences between Tango Studio and Ubuntu Studio?  Any links I could check out that compares the two?  I may just partition the disk and have multiple installs so I can try both, but I don't know how much effort I want to spend on both.. I'd probably want to learn one and stick with it...

Do you recommend Tango OVER Ubuntu Studio?

Thanks again!
  Bristen.

---

### Post by Pablo_F on 2011-03-10
Hi Bristen, 

Both Tango Studio and UbuntuStudio are basically ubuntu, as they share the same repos. 

In fact, the main difference is the ubuntu version they are based on. Tango Studio Karmasutra is based on ubuntu 10.04 (aka lucid) whereas the current UbuntuStudio is based on 10.10 (aka maverick). 

This does not necessarily mean that Tango is less up to date with regards to (some) audio production tools as this is the field Tango is good at. 

In adition, lucid is better supported by community members who package bleeding edge versions of programs through PPA's. Of course, PPA's for lucid are compatible with Tango Studio.

If you use the PC mainly for music creation (even if you can always install more programs not related to music) I recommend Tango Studio as your first distro (march 2011). 

Cheers, Pablo

---

### Post by Bristen Bourque on 2011-03-10
just a quick progress report... Since I had Ubuntu Studio installed, I decided to mess around with it a bit... I disabled the on-board sound card from BIOS as recommended and starting to grasp what JACK is all about after quickly reading a few things... I'm not sure, but I think everything appears to be working right now! I was able to record a quick track in Audacity and Ardor and Rakarrack appears to be working fine.

I'm just I'll hit more roadblocks, but so far so good... thanks!

Regards,
  Bristen.

---

### Post by Monona on 2011-05-22
This is a helpful discussion here.

Just for my two cents, I've been using pulse-jack with Lucid 10.04, and it's been great with my Fast Track Pro.  It's nice for having all my audio (listening and production both) coming out the same place, and being able to switch back and forth, or input pulseaudio into recording software.

I've also been using the Launchpad PPA from falktx, and the audio software available on that is nice.

---

