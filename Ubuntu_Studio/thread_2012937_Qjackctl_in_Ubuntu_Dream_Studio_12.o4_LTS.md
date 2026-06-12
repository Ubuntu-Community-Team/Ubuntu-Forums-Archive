---
title: "Qjackctl in Ubuntu Dream Studio 12.o4 LTS"
date: 2012-06-30
forum: Ubuntu Studio
---

### Post by tnob on 2012-06-30
[FONT=Arial]Greetings all,
 
After years of disappointment and frustration, the virtual music studio/video editing suite I have been dreaming of seems finally within my reach: with Ubuntu Dream Studio 12.04 LTS, my fortunes appear to have turned for the better.
 
It looks terrific - on paper at least. YouTube tutorials have been whetting my appetite as well. But one thing is still escaping me.
 
To my understanding, Qjackctl is the core of the operation, running connections "automatically". Now I wonder what will happen if applications from Ubuntu Software Centre are added to those already available on the desktop. Should the former be configured manually, after installation, or is this something Qjackctl will also take care of?
 
I surely could use some enlightenment on this point.
 
By the by: Ubuntu Dream Studio 12.04 LTS is not up and running yet. For everyday traffic, Ubuntu 10.04 LTS is still in use, on an old Dell desktop on which applications like Ardour and PiTiVi (the ones I need the most) have never been functional, for some reason or other. I hope a laptop I presently have a greedy eye on (a Toshiba Satellite C660@ with 4Gb RAM and a whopping 750 HDD on board) will remedy this, sometime in the foreseeable future.
 
tnob
[/FONT]

---

### Post by tnob on 2012-06-30
[FONT=Arial]A quick PS, with respect to the above, from the same author.[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]From several posts in this forum, I now understand that jackd is for audio and qjackctrl for all the rest. And as I am a complete newbie in the Ubuntu Dream Studio area, is it also correct that an internet connection is required to make jackd and qjackctrl work for me?[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]I feel a little stupid asking, but I have to start somewhere.[/FONT]
 
[FONT=Arial]tnob[/FONT]

---

### Post by CrocoDuck on 2012-06-30
Hi. jack is an audio server that provides low latency connections between applications designed to use it. Qjackctl is a program that let you to start jack and tweak it's settings (in and out device, sample rate, etc...) using a GUI (Graphical User Interface), as jack itself runs from console. With Qjackctl you can also manually menage audio connections between programs, like if they were just like guitar stompboxes. You can do all these things (and more) also without Qjackctl, because they are jack's features, but you have to do them from command line. If you'll install a new application you won't have to rebuild or reconfigure jack. jack's settings and configuration are stored in a number of configuration files. With Qjackctl you can save your settings. Every application you'll install from software center will interact with jack just out of the box (if designed to be used with jack, like Ardour, Guitarix, LV2 rack, AT1, etc... etc... applications that are not "jack-designed" won't interact directly with him). Of course you can use jack and related software without internet connection, I'm usually turn off my internet devices when making music (in order to have the best audio performances). If you want to buy a new computer have a look at hardware support or at forums to know if it's hardware is supported.

[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)

On ubuntu the device driver for audio cards is ALSA, here you find a list of audio devices tested with him:

[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

If you don't find the hardware you like in the official support it doesn't mean that hardware won't work. Search on forums and post questions about it before reject it.

---

### Post by sgx on 2012-07-01
Don't buy without confirmation, unless you have friends to
give/trade/sell the 'experimental' gear to. As a rule, the newest video cards, and motherboards, take time to get linux support, best to get slightly older gear, and use nvidia videocards.

maudio pci are easy to use, if you play electric guitar,
Fender Mustang amps are great usb input devices, with 
excellent sound/features.
Cheers

---

