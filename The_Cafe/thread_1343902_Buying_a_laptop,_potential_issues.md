---
title: "Buying a laptop, potential issues?"
date: 2009-12-02
forum: The Cafe
---

### Post by LinuxFanBoi on 2009-12-02
Okay.  I've decided on the laptop that I'm going to buy,  Now,  I would like to prepare myself for the potential issues that may arise  due to technology common to laptops that you don't find in desktop machines, such as touch pads and wireless network adapters.

What issues have you come across with laptops and are there any that you've yet to resolve?

---

### Post by pi4r0n on 2009-12-02
Most common issues are:

[LIST=1]
[*] Wireless cards - Due to missing modules and sometimes drivers issues as well.
[*] Graphic cards - Due to drivers issues. CHeck this before you get you laptop
[*] Music cards - Due to alsa drivers. Easy to fix
[/LIST]

But with good research you can get it working.

---

### Post by whiskeylover on 2009-12-02
My wifi card didn't work out of the box with Ubuntu. 

And touchpad is a bit... moody. Sometimes the cursor flies all over the screen when I accidently put 2+ fingers on it.

Other than that... no issues.

And I'm a new linux user, recently gave up windows... been using linux exclusively for 2+ months now (except when I'm at work). So far, I'm happy, no major issues.

---

### Post by Marlonsm on 2009-12-02
If possible, I'd suggest taking a LiveCD with you when buying the computer and booting with it, so you can have an idea of how well it will run.

---

### Post by scottuss on 2009-12-02
> **Marlonsm said:**
> If possible, I'd suggest taking a LiveCD with you when buying the computer and booting with it, so you can have an idea of how well it will run.

Exactly what I was going to say. If the store won't let you try it, take your custom elsewhere!

It's the best way to know beforehand, not to sound harsh, but don't just take the word of sales people to tell you it will work, they may not actually know (highly likely) and often they'll say anything to get the sale, even if they don't have a clue what Ubuntu is.

Disclaimer: I'm sure there are sales people on these very forums, and I mean no offence by my comments, I'm simply stating the fact that a large proportion of sales people are pressured to get the sale, and may not know what Linux is. I say this as I used to be a mobile telephone salesperson, and I know what pressure is placed upon them.

---

### Post by LinuxFanBoi on 2009-12-02
> **Marlonsm said:**
> If possible, I'd suggest taking a LiveCD with you when buying the computer and booting with it, so you can have an idea of how well it will run.

This is a good idea, it never occurred to me to do this.  I'm buying from Newegg.com,  but I think I'll take a trip to fry's and try this on a machine with the same hardware.

The machine I'm planning to buy has an NVIDIA GeForce GT 230M, In my desktop I use a GTS 250 with no issues what so ever,  so I'm optimistic about that.  The specifications don't give a make/model of the wireless and audio devices it simply says "802.11b/g/n wireless LAN" and "Integrated Sound card." It's a Toshiba laptop so I would imagine that they use one brand of these devices fairly exclusively in most of their laptops.

---

### Post by golusweet on 2009-12-02
My laptop died cause of design flaw by Nvidia in GPU.

  It's the most common problem in laptops. buy laptop with a good GPU.

  :p

---

### Post by mamamia88 on 2009-12-02
i would look for one with nvidia chip and broadcom card.  makes setting everything up easy

---

### Post by LinuxFanBoi on 2009-12-02
> **golusweet said:**
> My laptop died cause of design flaw by Nvidia in GPU.

  It's the most common problem in laptops. buy laptop with a good GPU.

  :p

Are you saying nVidia doesn't make good GPU's?  If so,  was your experience Isolated or a wide spread issue? Please keep in mind that nVidia makes the chip.  They merely license third party vendors, Some better than others, to package and sell it on their display adapters. 

Was it really nVidia's  fault or was is the fault of say XFX, BFG EVGA, Powercolor or any one of the many of licensed nVidia adapter manufacturers that created the design flaw? I find it hard to believe that a design flaw in the GPU core itself could brick your laptop.  There are so many other components that support it that are not within nVidia's realm of control to make such a generalization.

---

### Post by yossell on 2009-12-02
There was a well known problem with the 8400gs nvidia series - and some other lines were also affected. The problem was particularly acute in notebooks. It seems that the repeated heating-cooling cycle would cause microfractures in the solder holding the chip, leading to high failure rates. Because of the higher temps generally reached in laptops, the failure was very noticeable. This does seem to be mainly nvidia's responsibility - I believe nvidia eventually admitted culpability and there were large payouts to cover Dell and other's extended warranties.   I don't think this problem affects more recent gpus and, as a Linux user, though I was burned (haha) by the 8400, I would still go with nvidia because of the drivers.

---

### Post by LinuxFanBoi on 2009-12-02
> **yossell said:**
> There was a well known problem with the 8400gs nvidia series - and some other lines were also affected. The problem was particularly acute in notebooks. It seems that the repeated heating-cooling cycle would cause microfractures in the solder holding the chip, leading to high failure rates. Because of the higher temps generally reached in laptops, the failure was very noticeable. This does seem to be mainly nvidia's responsibility - I believe nvidia eventually admitted culpability and there were large payouts to cover Dell and other's extended warranties.   I don't think this problem affects more recent gpus and, as a Linux user, though I was burned (haha) by the 8400, I would still go with nvidia because of the drivers.

Thank you for this tid-bit of info.  I was able to find [this]("http://www.theinquirer.net/inquirer/news/1028703/nvidia-g84-g86-bad").  I hope NV learned from this.  However their Linux driver support being what it is, as compared to the alternatives (Yes I'm giving ATI the stink eye again) I would say NV's Reputation out shadows this blip on their record. 

I've only been an NV user for about 3 months and I constantly wonder why I was so loyal to ATI. when Jaunty came out and I discovered that the X.org that was released with it broke the current X1950 GT driver that coincidently had just been relegated to legacy (that's ATI's language for "We don't care anymore") My card was useless for anything other than non eye candy uses.  Ever since then I've been waiting for ATI to announce their bankruptcy so I can fictionalize their downfall as a direct result of their extremely lacking product support for Linux.  which we all know would never happen,  but damn it if I'm going to let anyone piss on my dreams :D

---

