---
title: "*sigh* I have to install Windows..."
date: 2007-02-14
forum: Windows
---

### Post by Velotix on 2007-02-14
Yes indeed, I have come to this most unfortunate conclusion. The reason? I need an OS that can actually play games without excessive time and effort (Wine) or a ridiculous subscription fee that'll end up costing me more than Windows (Cedega). As much as I don't like it, this leaves Windows as the best option. *sigh*

So! I hear that setting up a dual-boot system Linux first and Windows second is a major pain in the butt. It's taken me ages to get my Linux install just how I like it, so I don't want to mess with it at all if I can help it. Hence, I plan on buying a new hard drive to put Windows on.

I'm getting Windows XP Pro 32-bit, but I need advice:

[i]How exactly do I go about this without nuking my Linux install?
Do I get an IDE drive, or a SATA?
How big a drive if the drive is only going to store games?[/i]

---

### Post by mrmonday on 2007-02-14
The way I'd go about it is:

when installing the new drive remove the one with Linux on, then windows will think it is the first, then replace the old drive, boot to Linux and install grub, (I would get advise from someone else first though, I am not great at the whole multi booting thing)

If your PC supports it, go for SATA II if not SATA, If not IDE, these are in order of release, SATA II is supposed to be fastest (read reviews online for more information look at speed for games)

250GB or bigger.

Have you considered a virtualisation program such as VMware I think there is an open source project as well, however I am not an expert.

---

### Post by Velotix on 2007-02-14
The reason I ask about drive type is that XP apparently performs poorly if you try to install it to a SATA drive, but there are ways around it. Stupid but true, considering how easily my existing 400GB SATA was set up and formatted for my Linux install.

---

### Post by insane_alien on 2007-02-14
for games you would probably want a high RPM, low-ish capacity ~120GB SATA drive. yes, there are problems installing windows on SATA's but it could be worth it if you're playing high end games seriously.

---

### Post by KAL9000 on 2007-02-14
I didnt know there were any problems with SATA and Windows. all you need is a Floppy or a CD and 2 CD drives, the SATA driver goes on there and during the XP loader it will ask to press "F9" I think to install any 3rd party raid or storage controlers. then its done. as faras im aware.

Now i have heard of conflicts with dual boot when one OS is on SATA and the other is on a PATA.
Somethign about the BIOS will favour the PATA see the MBR then cos its already looking in a PATAdrive it will try to find annother PATA drive and not see grub on the SATA.

you could get around this im sure by putting grub on the PATA and not on the SATA.

---

### Post by Coelocanth on 2007-02-14
There shouldn't be any problem installing XP on a SATA drive. I did it with mine without issue. Didn't even need to install third party controllers.

---

### Post by GFree on 2007-02-14
Some motherboards/chipsets can provide a generic controller for the SATA drives so they look like IDE connections during the install. I know my nForce 4 mobo can allow me to see my drives during XP installation without needing extra drivers, but I still install the motherboard drivers afterwards to improve speed/functionality.

---

### Post by aysiu on 2007-02-14
> **Velotix said:**
> As much as I don't like it, this leaves Windows as the best option. *sigh* Unless you get a gaming console.

---

### Post by KAL9000 on 2007-02-15
Consoles  suck *** tho. everyone knows all the games worth playing areon PC :P

---

### Post by Velotix on 2007-02-16
> **aysiu said:**
> Unless you get a gaming console.

That's a common misconception of the videogames industry in general by people that don't play games - that a games console is an acceptable substitute for a gaming-capable PC and vice-versa. The PC is a distinct platform, like each console platform, with its own strengtths and weaknesses. To suggest I buy a games console when I want a suitable gaming PC is as stupid as suggesting I get a Wii because I can't afford a PS3, or a more familiar analogy, that I get Linux because I can't afford Windows - you get a platform *for a specific experience that you can't find anywhere else*. You want Linux because it's Linux, not because it's free - that's just an incentive to purchase it.

For the record, I already have a Wii, Xbox, Gamecube, N64, PlayStation, Saturn, etc. If that were satisfactory, I wouldn't have bought a PC in the first place, but the PC gaming experience is a world removed from the experience given by a console and control pad. Please appreciate this in future replies to this topic and others - I was actually quite offended by the dismissive nature of your suggestion. :(

> **KAL9000 said:**
> Consoles  suck *** tho. everyone knows all the games worth playing areon PC :P

For similar reasons, this is also an ignorant comment, but this one's a matter of opinion anyway, so nyeh to you. :P


Back to topic:

> **GFree said:**
> Some motherboards/chipsets can provide a generic controller for the SATA drives so they look like IDE connections during the install. I know my nForce 4 mobo can allow me to see my drives during XP installation without needing extra drivers, but I still install the motherboard drivers afterwards to improve speed/functionality.

Aha! Thanks for that. This computer has a very new motherboard so perhaps I too will not experience any issues. I suppose I can always try it, then. The only thing I'm not comfortable with is that I have a Linux swap partition and I think it's going to cause problems here:

My main hard drive is split into *sda1*, the main bit, and *sda2*, the swap bit. (*sda2* is actually a primary partition which holds the logical partition *sda5*, which is the actual swap partition. I'd not normally be so pedantic but this may prove helpful information here.) Theoretically, if I put a new hard drive in and set it as the master drive, all the drive designations will be pointing to the wrong place and my Linux install will be lost to the ages without editing the bootloader file, which I'll need to do anyway because of Windows. I'd also need to install GRUB to the new drive over the Windows MBR.

In other words, I could use some help as to what I do here, and how I configure GRUB to point to everything properly. Thanks, folks. ^^

---

### Post by KAL9000 on 2007-02-17
Over priced console = playing over priced games...and thats about it...

with a PC you can play games (Which can also be overpriced - But they tend to ome down lower then Console games do when they get old) and also when your done you can use the same hardware to browse online, do office type work...ect....

Sony are trying to do this in a way with the PS3 but boy they sure have a way of doing things. 

I used to love my PS2 but it seems they are coming with the same old games again and again. this of course is happening with the PC as well but as theres more flexibility in the PC to start with it should hold on for longer. (he says :P)

It annoys me that games developers don't include some limited support for Linux, After all it still X86, it uses the same instructions, same hardware, what could be so hard to make it install to the Linux file system. 

Maybe Microshaft is playing them off to keep games Windows compatible only.

---

