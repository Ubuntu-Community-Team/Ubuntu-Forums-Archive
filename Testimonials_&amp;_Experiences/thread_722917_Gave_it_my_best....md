---
title: "Gave it my best..."
date: 2008-03-13
forum: Testimonials &amp; Experiences
---

### Post by KraftSingle on 2008-03-13
I love the programs that came with Ubuntu 7.10. I also love the limitless customization. It really opened my eyes to how close-minded some software is. I find myself extremely annoyed by some proprietary limitations.

After hours upon hours, tons of posting for help, and researching on my own... I still could not get my system running properly. Just the other day I finally got my graphics card/video settings working right. At the same time I managed to somehow create a new kernel and totally wipe out all recognition of my sound card. So, after that... I went for some help to fix my sound. Good news is I got my sound back. Bad news is my graphics are messed up again! :( 

I really like Ubuntu, but I just cannot get it to work right! So frustrated!

HP M1170n + Ubuntu 7.10 = :confused:

---

### Post by jrusso2 on 2008-03-13
Yeah that stuff happens.  I would say try another distro that works with your hardware better.

Maybe something like Linux Mint, PCLinuxOS or Mandriva 2008 1 cd

---

### Post by agtownz on 2008-03-13
It's a shame that you're getting problems, my install worked perfectly, most likely because I used high quality hardware for my build.  I do have to mention though that pre-built computers aren't built with compatability in mind, so if Ubuntu has problems, it's very understandable.

> Bad news is my graphics are messed up again!
What exactly is wrong?  What graphics card and drivers (if you know) are you using?

---

### Post by KraftSingle on 2008-03-13
I will probably end up trying another distro. Once you go Linux you never go back.:lolflag:

---

### Post by KraftSingle on 2008-03-13
> What exactly is wrong? What graphics card and drivers (if you know) are you using?

I am using a ATI Radeon X300 SE. I encountered a few drivers that worked, but only one that worked properly. I used the ATI proprietary 8.3 driver with the "ATI accelerated graphics driver". The process of setting it up wiped out my sound though for some mysterious reason. I think it's Bill Gates messing with me!!!

---

### Post by agtownz on 2008-03-13
Alright, straightforward enough, then how did you go on to fix your sound?  Radeons, as you probably know, don't like Ubuntu very much.

---

### Post by tubasoldier on 2008-03-13
I had an HP laptop at one time. Mandriva was my only option to get it running, nothing else would even boot up on it. Mandriva is alright. It has some great graphical config tools that most other distros do not have. Their first 2008 release had a crazy kernel bug in it that made my system clock move extremely fast. So no more Mandriva for me.

But I would suggest giving something else a shot too.

---

### Post by KraftSingle on 2008-03-13
> Alright, straightforward enough, then how did you go on to fix your sound? Radeons, as you probably know, don't like Ubuntu very much.

Method A: Rebuild/install alsa-modules

Confirmed with kernel 2.6.22-13 and 2.6.22-14:

    *

      does work: Latitude D630, Latitude D830 (8086:284b (rev 02), codec: SigmaTel STAC9205), Precision M4300, XPS M1210, Vosro 1500 (Partial fix - issues with internal speakers not muting and microphone does not work - codec: SigmaTel 9205), Lenovo 3000 V200, Sager NP9880-C
    *

      does not work: Aluminium iMac, Asus F3SA, Dell Vostro 1400 (internal speakers still not working), HP Pavilion dv9000, Zepto Znote 6625WD, Toshiba Portege M600

cd /usr/src
sudo module-assistant update
sudo module-assistant prepare
sudo module-assistant auto-install alsa
sudo shutdown -r now

---

### Post by KraftSingle on 2008-03-13
> **tubasoldier said:**
> I had an HP laptop at one time. Mandriva was my only option to get it running, nothing else would even boot up on it. Mandriva is alright. It has some great graphical config tools that most other distros do not have. Their first 2008 release had a crazy kernel bug in it that made my system clock move extremely fast. So no more Mandriva for me.

But I would suggest giving something else a shot too.
Uh oh, I am downloading Mandriva 2008 as we speak!
It seems to come highly recommended. SuSE and Fedora I am skeptical about just because of their motivations (or proprietors in SuSE's case).

---

### Post by Shazaam on 2008-03-13
Mandriva's nice. Too bad you couldn't try Ubuntu Feisty though. Some have had great success with it.

---

### Post by pbpersson on 2008-03-13
You should try Mint.  It is basically a more friendly version of Ubuntu with better hardware detection and improved features.

I could not get my ATI card working on Ubuntu regardless of what I tried, but the Envy utility on Mint got it up and running  :)

---

### Post by KraftSingle on 2008-03-13
> **pbpersson said:**
> You should try Mint.  It is basically a more friendly version of Ubuntu with better hardware detection and improved features.

I could not get my ATI card working on Ubuntu regardless of what I tried, but the Envy utility on Mint got it up and running  :)

I haven't ruled it out. I will probably try that as well.

Gonna sleep on this Mandriva download now!

---

### Post by agtownz on 2008-03-13
I'm guessing you tried tweaking the driver settings for your sound by trying out every option?  Also, good luck with Mandriva.

---

### Post by 3rdalbum on 2008-03-14
> **pbpersson said:**
> 
I could not get my ATI card working on Ubuntu regardless of what I tried, but the Envy utility on Mint got it up and running  :)

Did you try Envy on Ubuntu though?

---

### Post by Ripfox on 2008-03-14
> **pbpersson said:**
> You should try Mint.  It is basically a more friendly version of Ubuntu with better hardware detection and improved features.

I could not get my ATI card working on Ubuntu regardless of what I tried, but the Envy utility on Mint got it up and running  :)

I don't think Mint has better hardware detection, it actually failed where Ubuntu succeeded on many of my machines. 
Envy is Envy. It works on Ubuntu "original" too:lolflag:

---

### Post by lcburgundy on 2008-03-16
> **KraftSingle said:**
> I am using a ATI Radeon X300 SE. I encountered a few drivers that worked, but only one that worked properly. I used the ATI proprietary 8.3 driver with the "ATI accelerated graphics driver". The process of setting it up wiped out my sound though for some mysterious reason. I think it's Bill Gates messing with me!!!

The X300 is supported, both 2D and 3D accelerated, by the open source radeon driver included with 7.1. Don't bother with the proprietary ATI drivers for it.

---

