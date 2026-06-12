---
title: "Canonical + Dell = LinuxBIOS"
date: 2008-11-24
forum: The Cafe
---

### Post by AnasR on 2008-11-24
I'm wondering if you are interested and planning for something regarding the LinuxBIOS project?
I think it could lead to very interesting product.
Again, my question is: Is there any plan for LinuxBIOS?

---

### Post by Sef on 2008-11-25
Moved to Community Cafe.

---

### Post by DeadSuperHero on 2008-11-25
First off, LinuxBIOS is technically known as the Coreboot project.

Secondly, that would be amazing. If this were the case, and Dell provided FOSS-compatible hardware, I'd slap gNewSense on it and finally be truly free.

This is a fantastic idea.

---

### Post by handy on 2008-11-25
> **Mr. Psychopath said:**
> First off, LinuxBIOS is technically known as the Coreboot project.

Secondly, that would be amazing. If this were the case, and Dell provided FOSS-compatible hardware, I'd slap gNewSense on it and finally be truly free.

This is a fantastic idea.

I think it would be great too.

Though as far as being truly free is concerned, that is impossible.

The multi-billion dollar mega corp's involved in the manufacture of computer components rules that entirely out of the question, I'm sorry to say.

---

### Post by Paqman on 2008-11-25
Coreboot will need support from an OEM to gain traction. I think for the majority of people, replacing the BIOS on their existing machine is pretty intimidating.

---

### Post by handy on 2008-11-25
> **Paqman said:**
> Coreboot will need support from an OEM to gain traction. I think for the majority of people, replacing the BIOS on their existing machine is pretty intimidating.

It is a simple process to flash the BIOS; a BIOS backup followed by flashing the new BIOS can be done whilst using the desktop. I think it can be made to be a very painless process, with very clear instructions to not allow the process to be interrupted, to the point of advising people not to do it if there is any chance of a power failure (storms or what have you).

---

### Post by KyTiX on 2008-11-25
Im not trying to be sarcastic or anything but Well what would your "LinuxBIOS" be able to do that your current bios can't?

Like what would you be wanting in a custom BIOS that you don't already have?

---

### Post by Capt. Mac on 2008-11-25
> **KyTiX said:**
> Im not trying to be sarcastic or anything but Well what would your "LinuxBIOS" be able to do that your current bios can't?

Like what would you be wanting in a custom BIOS that you don't already have?

It's not about added functionality, it's about being free software instead of proprietary. At least I believe this is the project these people are referring to.

---

### Post by Paqman on 2008-11-25
> **handy said:**
> It is a simple process to flash the BIOS; a BIOS backup followed by flashing the new BIOS can be done whilst using the desktop.

Sure, for flashing BIOS from one version to another. But Coreboot isn't BIOS.

---

### Post by KyTiX on 2008-11-25
I understand the "Free Software Stand" of it. But i'm i just curious to what can be implemented that isn't already in any BIOS?

---

### Post by tadcan on 2008-11-25
> **handy said:**
> It is a simple process to flash the BIOS; a BIOS backup followed by flashing the new BIOS can be done whilst using the desktop. I think it can be made to be a very painless process, with very clear instructions to not allow the process to be interrupted, to the point of advising people not to do it if there is any chance of a power failure (storms or what have you).

When I read about flashing the Bios it sounded dangerous. i.e One mistake and you has ruined the machine. Plus you need to have a floppy drive, which is not very common any more. Or were you thinking of another method.

---

### Post by Capt. Mac on 2008-11-25
> **tadcan said:**
> When I read about flashing the Bios it sounded dangerous. i.e One mistake and you has ruined the machine. Plus you need to have a floppy drive, which is not very common any more. Or were you thinking of another method.

I know that BIOS flashing can be done on the Acer Aspire One via a USB stick, so it's not necessarily limited to floppy drives. Though I've never done it myself.

> **KyTiX said:**
> I understand the "Free Software Stand" of it. But i'm i just curious to what can be implemented that isn't already in any BIOS?

If there are any features to be implemented in coreboot that would make it superior to a standard proprietary BIOS, I am not aware of them. I believe the only real goal is to replace one of the only remaining pieces of proprietary software that exist in essentially all Linux systems today. However, because of the nature of free software, anyone with such a skill could implement potentially groundbreaking features.

Edit: I may be missing something, a list of benefits is located here here: [http://www.coreboot.org/Benefits](http://www.coreboot.org/Benefits)

---

### Post by handy on 2008-11-25
> **Paqman said:**
> Sure, for flashing BIOS from one version to another. But Coreboot isn't BIOS.

It sure looks like it is from a quick glance at the website:

*coreboot (formerly known as LinuxBIOS) is a Free Software project aimed at replacing the proprietary BIOS (firmware) you can find in most of today's computers. It performs just a little bit of hardware initialization and then executes a so-called payload. *

---

### Post by Paqman on 2008-11-25
> **handy said:**
> It sure looks like it is from a quick glance at the website:

[I]coreboot (formerly known as LinuxBIOS) is a Free Software project aimed at replacing the proprietary BIOS (firmware) you can find in most of today's computers. 

It replaces BIOS, and does the same job, but AFAIK there's no desktop tool to flash from BIOS to coreboot.

> 
It performs just a little bit of hardware initialization and then executes a so-called payload. [/I]

This is referring to Coreboot's ability to start bringing up the system very fast. According to Wikipedia: *"A unique feature of coreboot is that the x86 version runs in 32-bit mode after executing only ten instructions"*

---

### Post by handy on 2008-11-25
> **tadcan said:**
> When I read about flashing the Bios it sounded dangerous. i.e One mistake and you has ruined the machine. Plus you need to have a floppy drive, which is not very common any more. Or were you thinking of another method.

You can also flash a BIOS with a desktop running, & some motherboards allow you to flash the BIOS over the internet.

The dangerous part of it is if for whatever reason the process is interrupted.

It does not have to be hard, it just has to have a couple of minutes to do what it does, so there is no reason why the coreboot people won't end up with a streamlined web centric process, I would think. :-)

---

### Post by tadcan on 2008-11-25
> **handy said:**
> You can also flash a BIOS with a desktop running, & some motherboards allow you to flash the BIOS over the internet.

Have you any links to tutorials etc?

---

### Post by handy on 2008-11-25
> **tadcan said:**
> Have you any links to tutorials etc?

I have an approx' 4 year old Gigabyte board that has the capacity to flash the BIOS from their website.  The system is called @BIOS.

Here is a link to instructions for using it:

***_[http://www.giga-byte.com.au/FileList/NewTech/old_motherboard_newtech/tech_a_bios.htm](http://www.giga-byte.com.au/FileList/NewTech/old_motherboard_newtech/tech_a_bios.htm)_***

I'm sure that not only Gigabyte have incorporated this type of system into whatever % of their motherboards.

So my reasoning is that if this kind of system has been available for at least 4 years now, then there should be no reason why a Linux system can not do the same & add improvements.

---

### Post by stalkingwolf on 2008-11-25
> I have an approx' 4 year old Gigabyte board that has the capacity to flash the BIOS from their website

Got ya beat. I have a gigabyte board that is the same as the one in my first computer (2001) that has that ability.  It is a GA7 something or other.

---

### Post by armandh on 2008-11-25
an open bios is a piece of the totally open puzzel.
it insures there is no hidden agenda in your computer.

for 99% of us it is one more cost item that could be free.
for the other 1% it provides the assurance lacking in closed software.

always fun to get
BIOS CHECKSUM ERROR A:\

I did fix it

---

### Post by smartboyathome on 2008-11-25
Just to let you know, coreboot has the FlashROM tool which allows you to flash your bios. I was thinking of using coreboot+etherboot on my 10 year old laptop that I was going to set up to be a thin client. I wonder if it will even fit on it. Any way to tell how big the flash storage is in it?

---

### Post by handy on 2008-11-25
> **stalkingwolf said:**
> Got ya beat. I have a gigabyte board that is the same as the one in my first computer (2001) that has that ability.  It is a GA7 something or other.

I'm sure your competitive streak feels better now that it has had a little feed. :lolflag:

---

### Post by handy on 2008-11-25
> **armandh said:**
> an open bios is a piece of the totally open puzzel.
it insures there is no hidden agenda in your computer.

for 99% of us it is one more cost item that could be free.
for the other 1% it provides the assurance lacking in closed software. 

I think that the chips used in computer technology are capable of holding privacy breeching code.  

I also find it a little strange that FOSS has such staunch advocates, who are still using hardware made by monstrously huge & ruthless corporations that care not a jot for anything else but their quarterly profits. (All driven by their shareholders of course.)

By the way I support FOSS, it is just that there seems to be an irreconcilable dichotomy of interests here.

---

### Post by Dvilef on 2011-01-13
my understanding is that it would not really matter, it is dangerous to mess with Bios , and if you are a slow learner like me, well it could be hazardous,  But on the other hand it would maybe improve your computers processes and other object's (computer term), I would do it, But it seems like alot and would be cool if you could get machine (on) with Bios , I have some problems with drivers for usb , but you can , i think it would be a good move, to total full integration of desktop.

Also if Bios is install Then you can get Bios  update's for  your laptop or Desktop and server, so there are a lot of plus, Just really know how is need to do it, be cool if there was a page for installation of Bios

---

### Post by overdrank on 2011-01-13
Back to sleep little thread. :)

---

