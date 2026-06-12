---
title: "Finally! An Ubuntu that works!"
date: 2010-10-22
forum: Testimonials &amp; Experiences
---

### Post by LiamWilson on 2010-10-22
Hi all. 

I've been trying to use Ubuntu since 7.10 (Gutsy Gibbon!) on a relatively cheap Ei Systems Desktop PC for many many years to no avail, I had been suffering with severe lockups at random intervals that made using the desktop with Ubuntu unusable, causing me to revert back to windows XP, and abandoning the desktop for a laptop and netbook - both of which ran Ubuntu fine. And nor I or anybody else I asked for help could solve this somewhat crazy problem.

A few weeks back, I installed 10.04 on the desktop to see if anything had changed, but to no avail, the lockups were still occuring. Until 3 days ago, when I upgraded to 10.10, so far I have had zero lockups, and the system runs like a dream! 

I don'know what was changed to make it work nicely, but I'd just like to thank the community and developers for an awesome job they did!

Thanks again!

---

### Post by johntaylor1887 on 2010-10-22
That's great! But your machine probably has some esoteric hardware that wasn't supported properly until recently, which is not ubuntu's fault. Anyway, enjoy ubuntu!

---

### Post by coffeecat on 2010-10-23
> **LiamWilson said:**
> I've been trying to use Ubuntu since 7.10 (Gutsy Gibbon!) on a relatively cheap Ei Systems Desktop PC

> **johntaylor1887 said:**
> But your machine probably has some esoteric hardware that wasn't supported properly until recently

I wouldn't be surprised if there were SiS chipsets all over the place. Judging by the threads I've read over the years they have hitherto often been a nightmare, and SiS is often found in budget machines.

@LiamWilson, out of interest, can you post the terminal output of:

```
lspci
```

But whatever the chipsets, I'm glad hardware support for your machine has improved.

---

### Post by LiamWilson on 2010-10-23
> **coffeecat said:**
> I wouldn't be surprised if there were SiS chipsets all over the place. Judging by the threads I've read over the years they have hitherto often been a nightmare, and SiS is often found in budget machines.

@LiamWilson, out of interest, can you post the terminal output of:

```
lspci
```

But whatever the chipsets, I'm glad hardware support for your machine has improved.

Yeah, here it is:

```
liam@liam-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
01:05.1 Display controller: ATI Technologies Inc Radeon Xpress Series (RC410)
02:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

I actually think it was an APCI or RAM issue over anything else, since I am fated with a wonderful foxconn motherboard :rolleyes:

---

### Post by coffeecat on 2010-10-23
> **LiamWilson said:**
> I actually think it was an APCI or RAM issue over anything else, since I am fated with a wonderful foxconn motherboard :rolleyes:

I think you're right. My guess about SiS was wrong.

There was a little spat a year or so ago about ACPI in Foxconn motherboards and from what I remember Foxconn responded in a responsible and professional way. Or rather, they realised that a significant income was coming from Linux users and decided it was pragmatic to accommodate them. :wink: So things should be better with current Foxconn boards. But, whatever, good luck with Maverick and beyond.

---

### Post by LiamWilson on 2010-10-23
> **coffeecat said:**
> I think you're right. My guess about SiS was wrong.

There was a little spat a year or so ago about ACPI in Foxconn motherboards and from what I remember Foxconn responded in a responsible and professional way. Or rather, they realised that a significant income was coming from Linux users and decided it was pragmatic to accommodate them. :wink: So things should be better with current Foxconn boards. But, whatever, good luck with Maverick and beyond.

Yeah, I saw that, and followed the instructions posted. Didn't do anything though, but I'm not exactly complaining now! ;)

---

