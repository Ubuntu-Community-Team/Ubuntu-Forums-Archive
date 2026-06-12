---
title: "Fighting EFI for Free BIOS"
date: 2008-12-01
forum: The Cafe
---

### Post by DPic on 2008-12-01
EFI seems to be a pretty big threat to Free Software since as it becomes the standard, it will disable projects like Coreboot and OpenBIOS, and it will make a fully open system impossible. 

I've posted to Dell's IdeaStorm to ask that they try to resist it:
[http://www.ideastorm.com/ideaView?id=087700000000ECsAAM](http://www.ideastorm.com/ideaView?id=087700000000ECsAAM)

What efforts are there to oppose EFI?

[I]**_Update [2008.01.09]:_** I blogged about it here: [http://pinstack.blogspot.com/2009/01/efi-hidden-threat-to-computing-freedom.html](http://pinstack.blogspot.com/2009/01/efi-hidden-threat-to-computing-freedom.html)

And here is a more detailed explanation of why EFI is bad news from [http://archive.fosdem.org/2007/interview/ronald+g+minnich](http://archive.fosdem.org/2007/interview/ronald+g+minnich)
>     I have spoken with the EFI authors at length. They make no secret of the fact that a "core value" of EFI is the preservation of intellectual property related to chipset programming and internal architecture. To put it another way, EFI is dedicated to the preservation of "Hard" hardware (as defined above), and the provision of binary interfaces and subsystems to BIOS vendors and others.
    It is not really possible to build a full open-source BIOS if EFI is involved. The Tiano system, which Intel claims is an open source BIOS, can not be used to build a BIOS unless it is attached to proprietary, binary-only BIOS code provided by a vendor. 

    Another important thing to realize about EFI is that it also contemplates enabling chipset features that will trap certain OS operations to an EFI-based control system running in System Management Mode. In other words, under EFI, there is no guarantee that the OS owns the platform.
    Accesses to IDE I/O addresses, or certain memory addresses, can be trapped to EFI code and potentially examined and modified or aborted. Many see this as an effort to build a "DRM BIOS".
    I am not sure what the real intent of this design is, but is is a real concern in secure environments (such as those found in governments, banks, and large search engine companies). A number of vendors and users have told me that they are not sure they can ship an EFI system they are willing to trust in a secure environment. [/I]

---

### Post by zmjjmz on 2008-12-01
Wait hold on how is EFI supposed to prevent coreboot from being installed?

---

### Post by collinp on 2008-12-01
At least it appears that AMD is not going to be taking part in this. Hopefully.

---

### Post by Polygon on 2008-12-01
isnt efi like 20000 times better (technically?) then BIOS?

---

### Post by DPic on 2008-12-01
> **Polygon said:**
> isnt efi like 20000 times better (technically?) then BIOS?

From what i've read, it will add complexity without any real advantages. Even a free BIOS will requite some proprietary bits to work with EFI. It would be better to just have Free BIOSes

---

### Post by RaZoR1394 on 2008-12-21
AMD is a very strong supporter of Coreboot, they are not going to adopt EFI just like that, that's one reason we only have AMD computers here except an Intel ARM based Pocket PC but that's different.

Two of my desktops boots partially with Coreboot.

I have had a lot of problems with buggy bios:es on several computers.

Coreboot is also not a BIOS. It's a totally different firmware that doesn't use BIOS calls unless you use a payload like Seabios.

---

### Post by DeadSuperHero on 2008-12-21
I really want to get a laptop with Coreboot. If System76's machines ever get labeled Coreboot-compatible, I'll be jumping for joy.

---

### Post by cb951303 on 2008-12-21
> **Mr. Psychopath said:**
> I really want to get a laptop with Coreboot. If System76's machines ever get labeled Coreboot-compatible, I'll be jumping for joy.

I believe it depends more on the motherboard manufacturer than system76. It would be really good to have a coreboot laptop though.

---

### Post by MikeTheC on 2008-12-21
Who is pushing these locked-down EFI configurations?

---

### Post by MaxIBoy on 2008-12-21
Apple.

---

### Post by cb951303 on 2008-12-21
> **MaxIBoy said:**
> Apple.

And I believe Intel

---

### Post by Polygon on 2008-12-21
well bios is very old and decrepit. If there is going to be any alternative for the BIOS, i think its going to come from one of the major players, and i dont think coreboot goes anywhere unless it specifically gets backed by some huge company.

---

### Post by jrusso2 on 2008-12-21
> **cb951303 said:**
> And I believe Intel

I don't know about the locked down part, I mean you can still run Linux fine on Apple, I think Intel feels EFI is an improvement.

---

### Post by handy on 2008-12-22
I use [***_rEFIt_***]("http://refit.sourceforge.net/") on my iMac to dual boot Leopard & Arch.  It works really well.

---

### Post by glotz on 2008-12-22
[QUOTE=handy]I use [***_rEFIt_***]("http://refit.sourceforge.net/") on my iMac to dual boot Leopard & Arch.  It works really well.[/QUOTE]Looks to me it has nothing to do with BIOS.

---

### Post by handy on 2008-12-22
> **glotz said:**
> Looks to me it has nothing to do with BIOS.

Here is more info' on how Apple do it:

***_[http://developer.apple.com/technotes/tn2006/tn2166.html](http://developer.apple.com/technotes/tn2006/tn2166.html)_***

Here is a link to a wiki article I wrote on installing Arch on the iMac, the first parts up to section 1.4 give details on handling EFI & the GPT partitioning scheme that Apple uses:

***_[http://wiki.archlinux.org/index.php/IMac_Aluminium](http://wiki.archlinux.org/index.php/IMac_Aluminium)_***

---

### Post by glotz on 2008-12-22
I stand corrected.

---

### Post by DPic on 2009-01-09
> **Mr. Psychopath said:**
> I really want to get a laptop with Coreboot. If System76's machines ever get labeled Coreboot-compatible, I'll be jumping for joy.

Check this thread out: [http://ubuntuforums.org/showthread.php?t=887170](http://ubuntuforums.org/showthread.php?t=887170)

Anyways, back to the original question-- what can we do to oppose EFI besides pushing Dell on IdeaStorm? 

Petition? Boycott whoever is pushing for it? Get the FSF to start a campaign? Start a riot?

---

### Post by smartboyathome on 2009-01-09
> **DPic said:**
> Anyways, back to the original question-- what can we do to oppose EFI besides pushing Dell on IdeaStorm? 

Petition? Boycott whoever is pushing for it? Get the FSF to start a campaign? Start a riot?

I would say boycott whoever does it. We may be a small(ish) community in terms of how many people use computers, but we can still be mighty when it comes to the wallet of major companies. If we promote a boycott, then we are hurting the companies during a time when they should be hurting already, and rubbing salt in their open wounds.

---

### Post by Polygon on 2009-01-10
FSF has almost no credibility now. having them start a campaign would just have the opposite effect really.

---

### Post by eragon100 on 2009-01-10
> **Polygon said:**
> FSF has almost no credibility now. having them start a campaign would just have the opposite effect really.

+1 The FSF is behaving like a group of extremist 4 year old.

Free Software Freaks

---

### Post by DPic on 2009-01-10
> **eragon100 said:**
> +1 The FSF is behaving like a group of extremist 4 year old.

Free Software Freaks

Yes they are extremist but i think they are a necessary end of the spectrum just like the ACLU.

---

### Post by ov3rcl0ck on 2010-04-16
EFI in no way promotes propriety, it just allows the BIOS to be stored on the mother board and some say it will also be able to get rid of MBR's and boot directly from the EFI firmware, which has already been done by apple.

Open Source EFI firmware already exists, its called rEFIt. EFI is supposed to be better than BIOS in the way that it can handle cross platform drivers, thus you will only need the EFI firmware driver to support a piece of hardware on 2 different platforms(like windows and linux for example), but that includes the OS to support EFI. If the OS doesn't support EFI, most EFI firmwares will emulate a BIOS and MBR. Personally I have an EFI based system, since Linux doesn't support EFI yet I have to emulate BIOS & MBR with rEFIt, it works fine, but nothing to special.

Just because theres Open source projects for BIOS firmware, doesn't mean its bad to stop using BIOS and move on. Theres just as many open source projects for EFI.

---

