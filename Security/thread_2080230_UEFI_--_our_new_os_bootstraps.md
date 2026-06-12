---
title: "UEFI -- our new o/s bootstraps"
date: 2012-11-03
forum: Security
---

### Post by mike acker on 2012-11-03
UEFI is a fascinating topic

the idea is to load the bootstrap from firmware together with PGP keys

the PGP keys to be used to validate the O/S components being loaded

this could help block root-kit infections 

why they are using a MSFT key in the firmware is a question though,... the key should be provided by the O/S OEM ...

that would be MSFT for their Windows systems; Apple for their MAC systems, and various  Linux makers, Canonical, RedHat &c *

the implications are monumental from a security standpoint. we finally have the ability to **AUDIT** the critical O/S software .... as it is loaded and before it is allowed to execute

a word of caution though: hopefully it is **not possible to flash the UEFI **firmware once it is initialized

this will need some careful thought: a physical switch will be needed.   I would prefer UEFI to be on an EPROM so that updates would need to be mailed.

Updates should not be needed unless the key needs to be revoked -- or the motherboard is replaced.

I'll be looking forward to UEFI support in Ubuntu
~~~~~~~

* remember: you can have multiple keys on your key-ring. this could help if you want a dual-boot or multiple boot. PGP(GnuPG) will automatically select the public key with a UserID matching the key used to sign the software

---

### Post by Cheesemill on 2012-11-03
> **mike acker said:**
> I'll be looking forward to UEFI support in Ubuntu
Ubuntu already has support for UEFI and has done for the last few releases.

---

### Post by JKyleOKC on 2012-11-03
Mike, you might want to Google "secure boot" (with the quotes to search for the phrase rather than the individual words) to sample the full depth and controversy.

UEFI does not insist on a key for booting, it just allows the hardware provider to require one in the BIOS chip. Since all hardware providers want to make it possible to boot Windows, they all (except Apple, of course) use the Microsoft key as the one to require.

However at present Microsoft requires all X86-compatible motherboards (I'm not sure but I think 64-bit units also) to provide means in the BIOS to disable the need for a key, or "secure boot" option. No such opt-out capability is required for ARM devices, however. And nobody guarantees that opt-out will remain an option for next year's hardware, or the year after that, and so on...

It's a most controversial subject. I would not buy hardware that was limited to "secure boot" and had no opt-out feature, but I fear that my opinion is a minority view -- and that building my own might not be an option, if no motherboards with opt-out capability are available on the market!

---

### Post by mike acker on 2012-11-03
well rats. I carefully selected a motherboard without UEFI because i thought UEFI was for MSFT only

glad to find out i'm wrong!!

I wonder if I can take apart the CPU and CPU cooler fan and change out the mother board ???? hmmmmm I'll have to replace that special cement they have in there to transfer the heat from the CPU to the heat sink/fan assembly ...

I already have another ASUS motherboard selected (M5A97)

---

### Post by mike acker on 2012-11-03
> **JKyleOKC said:**
> {snip}

It's a most controversial subject. I would not buy hardware that was limited to "secure boot" and had no opt-out feature, but I fear that my opinion is a minority view -- and that building my own might not be an option, if no motherboards with opt-out capability are available on the market!

I would think "opting out" would have to be selected from the BIOS options by hitting F4 or whatever at the critical moment ... My M5A88 gives me a huge display of the "Critical Moment" 

this would seem to place the option to opt out under physical security as the choice is taken before the o/s is functional

...of course I did note that UEFI firmware includes net communication capability.  As Bruce Schneier has noted "Complexity is the enemy of security". The more bells and whistles they add on the more opportunities there are for tampering.

Canonical should not be signing software using MSFT key. To my thinking UEFI keyring should hold keys from MSFT, Red Hat, Canonical ...

---

### Post by JKyleOKC on 2012-11-03
I think you're better off without it! That "special glue" between the CPU chip and the cooler isn't glue at all; it's a silicone grease to improve heat transfer. However it's really easy to damage CPU chips; the slightest hint of static electricity can fry one.

Using UEFI requires rather different installation techniques, and so far the standard Ubuntu installer program doesn't always do it right. There's an explanation of the differences at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and I recommend it to anyone concerned about the issues involved.

EDIT: My impression is that future versions of Windows will require UEFI being active in order to boot at all. If you opt out, then you simply cannot boot Windows, so there's no security risk involved -- at least, not from opting out of EFI. My recently acquired system that came with Win7 installed at the factory uses UEFI to boot, so I learned about the installer problems the very hard way since I wanted to retain Win7 in usable form although I've not booted into it since finally getting my Xubuntu installation usable. In fact, that machine runs 24/7 and has been up for several weeks now...

---

### Post by OpSecShellshock on 2012-11-04
I think one of the requirements for devices to be "certified" to run Win RT on ARM is that they use UEFI with SecureBoot, which requires keys for anything to run prior to the OS, and that the opt-out feature be disabled. Since Microsoft is the company with the relationship to the hardware manufacturers, and since they want the hardware to run Win RT, that means having their key in the firmware. Now, under regular manufacturing conditions the key used would be determined by the consumer the first time they boot up the device, but that's more than most folks buying consumer electronics would be inclined to do. So what's happening with these "certified" for Win RT devices is that that step is being taken care of before the devices ship, locking a brand new device with a Microsoft key. So the reason that you're seeing Canonical and Red Hat signing pre-OS code with Microsoft keys is because that's the only way to load and install those distros on those Win RT certified devices (since the opt-out is disabled and the key is pre-loaded when they ship).

I'm pretty sure part of the reason they do it is so they can get into enterprises. Most OEMs aren't going to differentiate consumer-grade and enterprise-grade product lines, because it's a hassle. That means consumers will have no choice of which OS to run, but there aren't enough consumers who are going to want to boot their own choice of OS anyway. They know what they're getting when they decide between a Win RT device, Android device, or iOS device. Now, that's mostly for tablets, but that's where things are going anyway. The desktop computer is fixing to be a niche market here really soon.

This of course affects as as Ubuntu users because generally when we buy something, we like to also own it.

Bringing it back to security: they say it's a security feature because code that isn't properly signed can't load before the OS does. That kind of sort of addresses the specific classes of malicious software made to do that. But it does presume that the code-signing infrastructure is reliable (it's not).

---

### Post by mike acker on 2012-11-04
The Platform Key

X

When a board is configured there is no reason to limit it to one "Platform Key": It can just as well support whatever software OEM care to participate

The reason for this lines in the nature of PGP/GnuPG : you can have as many keys as you like on your keyring, and on receipt of a signed message -- such as a software distribution -- PGP will locate the key needed to authenticate the transmittal

we all know about the MSFT||Intel "group".  But ASUS has already  been noted for supporting Linux and are not likely to limit their sales opportunities by supporting only MSFT's O/S. and let's not forget the good folks from VM Ware.

to my thinking UEFI presents a real opportunity  to implement the detection and consequently response elements necessary to a Security Plan.  As the O/S loads we can check the signature on every element loaded.

this won't create a 100% secure system. As noted above the "code signing infrastructure" is not secure.  What he's referring to is malware that gets included in the manufacture and distribution of software components and products.

we have to close 1 door at a time

expanding UEFI into a System Boot Audit helps add detection ( and thus enable response ) against un-authorized programming that our systems may acquire from web-sites, e-mail, and ordinary operation

protecting the software distribution channel is a zero-defects project that will need to be addressed separately .

---

### Post by oldfred on 2012-11-04
Windows RT is not even Windows. It will not run most Windows 8 software nor any x86 software you have. It is more like an iPad or phone in that all your apps have to be downloaded from Windows store. 

x86 runs Windows 8
ARM run Windows RT
Windows RT has this new touch user interface called 'metro' that only runs apps you buy online from the microsoft app store. It doesn't run anything else. Its a lot like how an ipad works with itunes.
Windows 8 has everything Windows RT has, but it also has an extra tile called "Desktop Mode" where you can run software designed for desktop mode. It will also run software from previous versions of windows in "desktop mode".
More Details
[http://www.wired.com/gadgetlab/2012/10/windows8-windows-rt-explainer/](http://www.wired.com/gadgetlab/2012/10/windows8-windows-rt-explainer/)

---

