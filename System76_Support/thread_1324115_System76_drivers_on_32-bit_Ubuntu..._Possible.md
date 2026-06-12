---
title: "System76 drivers on 32-bit Ubuntu... Possible?"
date: 2009-11-12
forum: System76 Support
---

### Post by samalex on 2009-11-12
Hi,

This is probably more directed at Thomas or one of the S76 folks, but if anyone running 32-bit Ubuntu (9.04 or 9.10) can verify this I'd appreciate it.

I'm getting ready to install Karmic soon, and in doing so my goal is to resize my home partition to give enough room to install 32-bit Karmic along side my current install of 64-bit Jaunty.  By running 32-bit I hope this'll detour the problems I'm having with Flash plus allow me to run/compile some apps that just aren't happy under 64-bit Ubuntu.  But will the System76 drivers work under 32-bit Ubuntu Karmic?  If not, for anyone running 32-bit Karmic or Jaunty, what problems did you run into getting hardware to work?  

Thanks for any advise... One of the reasons I went with System76 was for the driver support, but I didn't anticipate the problems I've ran into with 64-bit Linux.  

Take care,

Sam

---

### Post by robtg on 2009-11-12
Sam:  I "accidentally" installed a 32-bit version of Ubuntu 9.04 on my PanP5 (reached for the wrong Ubuntu CD) and the system76 driver worked fine.  You shouldn't have any issues doing this. 

Rob

---

### Post by echo314 on 2009-11-12
Does flash not work in the browser on System76 systems, such as that used for Youtube? 64bit Linux can view Youtube, right?

---

### Post by thomasaaron on 2009-11-12
Yes. Flash works in both 32-bit and 64-bit, although 64-bit still has the occasional issue.

---

### Post by Eldera on 2009-11-12
Tom: Please correct me if I'm wrong.

 I have been getting the impression that when one does an clean install and follows it up with installing the 76 driver, that the driver checks the model of one's computer and installs any patches appropriate for that computer. If there are no patches needed it does nothing. So, if one ran it without needing it, it would be no big deal. Is that true?

I am studying VirtualBox, so set up my panp4n with three partitions:
One: Jaunty 64 bit for things I don't want messed up. Two: Hardy 32 bit to host a VirtualBox for 32 bit guests. Three: Jaunty 64 bit to host a VirtualBox for 64 bit guests.

When I did the Hardy install, I also installed the 76th driver. I later read a post that the driver was only for 64 bit systems, but everything was working so I did not worry about it. 

Was poster correct? Is the 76 driver only for 64 bit?

Thanks in advance for making everything clear. You always do.

---

### Post by samalex on 2009-11-12
> **echo314 said:**
> Does flash not work in the browser on System76 systems, such as that used for Youtube? 64bit Linux can view Youtube, right?

Adobe doesn't currently have a stable version of Flash 10 for 64-bit Linux, so Ubuntu uses a wrapper (nspluginwrapper I think) which allows 32-Bit Flash 10 to work on 64-bit Ubuntu.  

It works, and yes Youtube, Hulu, etc work on 64-bit Ubuntu, but it's not perfect.  For example none of the webcam features in Flash 10 work using the wrapper (ustream.tv and stickam.com for example), and at times Flash will crash requiring the browser to be reloaded before it'll work again.  Also a hand full of times the wrapper has pegged the CPU 100% which requires me to kill the process manually.

Adobe has an alpha version of 64-bit Flash 10 for Linux, but I've never been able to get it working, though I hear it works in 64-bit Karmic rather well.  But the 32-bit Flash 10 is stable, and as much as I depend on flash-enabled sites I'm looking at going to 32-bit Linux to get these problems ironed out.

Sam

---

