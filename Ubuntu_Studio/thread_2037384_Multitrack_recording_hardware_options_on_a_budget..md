---
title: "Multitrack recording hardware options on a budget..."
date: 2012-08-04
forum: Ubuntu Studio
---

### Post by jesushero on 2012-08-04
I have been a recording engineer for many years now, but most of it has been on analog equipment. I eventually ventured into the world of digital recording and I am currently using Ubuntu Studio 12.04 with an M-Audio Delta 1010LT (8 input 8 output) PCI card. It works great and I am really happy with this setup.

I now want to expand my recording capabilities and I am researching the right option for a mobile studio, able to record more than just 8 channels of audio simultaneously. 

I have decided to go for a rackmount computer box with solid state hard drives (traditional ones probably won't last long when you're always moving on bumpy roads). But I am terribly undecided on the soundcard front. I am so happy with the Delta (and its price) that I wish they just made a 24 input version!! But they don't. 

So far I've also looked into the RME interfaces, which I've used in the past with Ubuntu Studio and worked good, but their prices are astonishing. I've also never set up this system with separate PCI card and separate rackmount AD converter with ADAT out or so, which makes me even more afraid of making the wrong choice with these things.

I've also read that it is possible to just install two Delta 1010LTs and have 16 inputs. Could I make that three, for 24 inputs? Does it take endless hours of software mangling to get Jack to work with two or three 1010LTs, or will it be as simple as just installing one?

I don't need mic preamps, I've got enough already. I only need line inputs at a decent enough quality (which the Delta can definitely provide), an affordable price (not more than 600 euros all together), and ease of installation (not enough time for endless hours of trying to make it work).

What do you people use? How well does it work? How expensive was it? How long did it take to get it working?

Thanks in advance. 

Also any suggestions for the generic hardware (rackmount computer box, motherboard, processor, ram, solid state hard drives, graphics card, etc) would be hugely appreciated.

Compatibility with Ubuntu Studio is an absolute must for all the hardware. I don't dual boot. I only use Ubuntu.

PS: Forgot to ask, is the MOTU 424 PCIX (with something like a MOTU 24I/O) compatible with Ubuntu Studio?

---

### Post by fedexnman on 2012-08-05
I don't know about on Linux , but this page says you can install up to 4 m-audio 1010lt cards , [http://www.m-audio.com/products/en_us/Delta1010LT.html](http://www.m-audio.com/products/en_us/Delta1010LT.html)   .  Another option is to get one of the RME  cards and some kind of adat in/out device for it .  Also check the ALSA site for compatible sound cards  .  There is also firewire too , FFADO , but its a little harder to setup then PCI stuff .  I have a Echo Audiofire4  firewire and have good luck with it if I use a light desktop environment like xfce or lxde . If I use Unity or Gnome3 I get lockups and xruns .   The Echo audio Layla , mia stuff is pci with a breakout box , it might have adat on it to , I believe its known to work  . You might be able to find some stuff used and save some money .  You have to check ALSA site for pci , pci-e and usb sound cards and the FFADO site for firewire devices and always google it .

---

### Post by sgx on 2012-08-05
> **jesushero said:**
> 
I've also read that it is possible to just install two Delta 1010LTs and have 16 inputs. Could I make that three, for 24 inputs? Does it take endless hours of software mangling to get Jack to work with two or three 1010LTs, or will it be as simple as just installing one?

[http://www.remastersys.com/forums/index.php?PHPSESSID=speii8dd185cllsil74j644gk3&board=20.0](http://www.remastersys.com/forums/index.php?PHPSESSID=speii8dd185cllsil74j644gk3&board=20.0)

The distro maintainer of AVLinux uses, or has used dual 1010 cards,
dig back through the forum, make a new query about 3 cards, or put

maudio "multiple 1010" in google

Cheers

---

### Post by Sylos on 2012-08-06
Hello.

Try this as an example for 3 cards:

[http://www.jrigg.co.uk/linuxaudio/asoundrc24](http://www.jrigg.co.uk/linuxaudio/asoundrc24)

I didnt write it nor understand it - just read this thread and did some absent minded googling.

Cheers

---

