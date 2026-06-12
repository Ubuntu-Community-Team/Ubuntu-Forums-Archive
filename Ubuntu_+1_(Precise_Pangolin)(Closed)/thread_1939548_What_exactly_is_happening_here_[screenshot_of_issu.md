---
title: "What exactly is happening here? [screenshot of issue]"
date: 2012-03-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by shamusl on 2012-03-11
My system keeps freezing in this way, seen below. It also keeps freezing completely, to where the capslock key is unresponsive (probably kernel panics). It seems after about 5-6 hours of uptime, a freeze like seen in this screenshot or a complete lockup (kernel panic?) locks the system, and the motherboard reports that hard drive activity is continuous, which I don't believe, and could be damaging my SSD?

[http://i.imgur.com/o8qKJ.jpg](http://i.imgur.com/o8qKJ.jpg)

---

### Post by cariboo on 2012-03-11
It looks almost like a video card issue, seeing as you neglected to tell us anything about your system, it's pretty hard to offer any suggestions.

---

### Post by effenberg0x0 on 2012-03-11
I concur. Use any tutorial for detecting VGA Brand/Model and install or reinstall your VGA drivers, as this is likely nor a Precise Pangolin issue. Also, since you mention 5/6 hours until defect, check PSU with a multimeter and CPU/GPU/MB temperature/cooling with a thermometer (don't trust software temperature reports too much - they're driver dependent).

No, this error won't cause any physical damage to your SSD. Nothing really causes physical damage to it. It's time to stop the FUD about these drives. Some people like to bring up old articles and analysis from unreliable sources feeding the myths about SSD technology, even thou they are not engineers, they know nothing about digital electronics and magnetic-persistent media, they do not know how the embedded controller and firmware works in these units, they do not have any RMA statistics. It's just FUD.   

I broke an entire RAID of SATA 3 Barracudas (conventional HDD) one month ago, they were almost 10 years old, Seagate asked no details: They sent me new ones via FEDEX. Intel, Corsair, Sandisk, WD, Crucial, OCZ, any SSD brand will do the same, no questions asked. Its cheap for them.

Banks are replacing SAS/FC for SSD on linux servers and storage. They have hundred thousand dollars/hour SLAs... They trust the SSD technology can maintain uptime during normal life cycle.

Just use Ubuntu and forget that you have a SSD.

Regards,
Effenberg

---

### Post by shamusl on 2012-03-12
> **cariboo907 said:**
> It looks almost like a video card issue, seeing as you neglected to tell us anything about your system, it's pretty hard to offer any suggestions.
Now that I check display driver is VESA on an ATI card, even though the driver manager says the ATI driver is installed properly. The sound manager shows my ATI card, and I've been using its sound output for weeks without issue. This is somewhat confusing.

I will check my PSU with a multimeter as well temps on the board and card. Sorry I'm misinformed about SSD technology. I wouldn't be surprised if most with these drives are though... Being able to hear a hard drive clicking/spinning away was always the best way to tell when it was being accessed, so now I rely on that stupid blinking light that probably isn't very accurate.

I also think it's a graphics issue because of weird black/white pattern that flashes at login for about 2 seconds. I reinstalled the latest driver directly from ATI with no change though. If you need any logs just tell me which and I'll drop them in here.

By the way, my machine configuration is:(sorry for not listing it in the OP)

Gigabyte GA-EP45-UD3P w/ Intel Q9400
ATI Radeon 4870 1GB (XFX)
4GB Kingston HyperX RAM
Corsair 620w (modular model)
160GB Intel 320 SSD w/ newest FW, also 2 750GB Seagate drives

Install media was 11.10, updated today to newest packages, although this issue existed before that.

---

### Post by effenberg0x0 on 2012-03-12
> **shamusl said:**
> Now that I check display driver is VESA on an ATI card, even though the driver manager says the ATI driver is installed properly. The sound manager shows my ATI card, and I've been using its sound output for weeks without issue. This is somewhat confusing.

I will check my PSU with a multimeter as well temps on the board and card. Sorry I'm misinformed about SSD technology. I wouldn't be surprised if most with these drives are though... Being able to hear a hard drive clicking/spinning away was always the best way to tell when it was being accessed, so now I rely on that stupid blinking light that probably isn't very accurate.

I also think it's a graphics issue because of weird black/white pattern that flashes at login for about 2 seconds. I reinstalled the latest driver directly from ATI with no change though. If you need any logs just tell me which and I'll drop them in here.

By the way, my machine configuration is:(sorry for not listing it in the OP)

Gigabyte GA-EP45-UD3P w/ Intel Q9400
ATI Radeon 4870 1GB (XFX)
4GB Kingston HyperX RAM
Corsair 620w (modular model)
160GB Intel 320 SSD w/ newest FW, also 2 750GB Seagate drives

Install media was 11.10, updated today to newest packages, although this issue existed before that.

VESA will be loaded as a fallback when proper drivers for your card fail to load. This is certainly the cause for what you are seeing there. There are detailed tutorials in this forum and Ubuntu Wiki about installing proper drivers for ATI, I think you won't have any problems installing the correct ones with small efforts. I had suggested looking at power and cooling as I had understood the problem used to manifest after using the PC for a while. But now that we know you're running with incorrect VGA drivers, and seeing that you have a very nice PSU (unlikely to be overloaded), I'd focus on the VGA first.

Regards,
Effenberg

---

### Post by 2F4U on 2012-03-12
As a starting point, look into /var/log/Xorg.0.log. There, the X server goes through the available drivers should provide information why the ATI driver is not used.

---

