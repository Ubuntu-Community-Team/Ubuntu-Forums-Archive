---
title: "Old Sun Machines: good for home use?"
date: 2007-01-02
forum: Sun Sparc Users
---

### Post by teejay17 on 2007-01-02
I have the opportunity to get a computer from the Mathematics and Computer Science dept. at my university. They have available:

> 30 Sun Ultra 10 Workstations (tower configuration)
- Hard drive either 4.1 GB or 9.1
- Memory 256 MB
- Processor either 360 or 400 MHz Sparc

40 Sun Ultra 5 Workstations (desktop configuration)
- Hard drive 4.1 GB
- Memory 128 MB
- Processor either 270 or 333 MHz Sparc

I'm wondering if it's possible to make a real good desktop computer out of one of these things, for basic computer needs, like net surfing, word processing, etc. 
How would Ubuntu 6.10 for SPARC work on these machines? What would installing it be like? What should I be aware of before going down this path? 
All the experience I have so far with Ubuntu has been with Intel x86 machines.

---

### Post by netztier on 2007-01-02
> **teejay17 said:**
> They have available:

30 Sun Ultra 10 Workstations (tower configuration)
- Hard drive either 4.1 GB or 9.1
- Memory 256 MB
- Processor either 360 or 400 MHz Sparc

40 Sun Ultra 5 Workstations (desktop configuration)
- Hard drive 4.1 GB
- Memory 128 MB
- Processor either 270 or 333 MHz Sparc

I'm wondering if it's possible to make a real good desktop computer out of one of these things, for basic computer needs, like net surfing, word processing, etc. 


Well, the U10 you have there might do the trick the way they are.  The U5s are are lacking memory to run Ubuntu (with GNOME), IMHO. Xubuntu with it's lighter footprint might run better - altough I keep experiencing problems with thunar, the file manager/browser on Ubuntu-SPARC.

Alternative window managers/desktop environments may be a clever choice, but then you leave the well-trodden Ubuntu path.

> **teejay17 said:**
> How would Ubuntu 6.10 for SPARC work on these machines? What would installing it be like? What should I be aware of before going down this path? 

Be wary of Ubuntu 6.10.  X currently (ew.. that was 2 weeks ago, haven't re-checked yet) does not seem to like the onboard ATI Chip. I had to get the X.org executable from Debian Etch to make it work. 

If the U10s happen to have UPA graphic cards (Creator or Creator3D cards), you're better off, these are supported with the sunffb modules. Browse around in the forums on how to deal with these - they're the same as the ones in the Ultra60s and Ultra2s.

For this reason, I suggest staying with 6.06.1 LTS for ubuntu-sparc with ubuntu-desktop.

Altogether however, I discourage using Ubuntu-SPARC as a general purpose desktop. It lacks Java (the Sun version), it lacks Flash and Shockwave as browser plugins. But that's just my CHF 0,05, and your opinion may of course differ.

best regards

Marc

---

### Post by teejay17 on 2007-01-02
> **netztier said:**
> Well, the U10 you have there might do the trick the way they are.  The U5s are are lacking memory to run Ubuntu (with GNOME), IMHO. Xubuntu with it's lighter footprint might run better - altough I keep experiencing problems with thunar, the file manager/browser on Ubuntu-SPARC.

Alternative window managers/desktop environments may be a clever choice, but then you leave the well-trodden Ubuntu path.

How would Ubuntu 6.10 for SPARC work on these machines? What would installing it be like? What should I be aware of before going down this path? 

Be wary of Ubuntu 6.10.  X currently (ew.. that was 2 weeks ago, haven't re-checked yet) does not seem to like the onboard ATI Chip, i had to get the X.org exectutable from Debian  Etch. If the U10s happen to have UPA graphic cards (Creator or Creator3D cards), you're better off, these are supported with the sunffb modules. Browse around in the forums on how to deal with these - they're the same as the ones in the Ultra60s and Ultra2s.
For this reason, I suggest staying with 6.06.1 LTS for ubuntu-sparc with ubuntu-desktop.

Altogether however, I discourage using Ubuntu-SPARC as a general purpose desktop. It lacks Java (the Sun version), it lacks Flash and Shockwave as browser plugins. But that's just my CHF 0,05, and you opinion may of course differ.

best regards

Marc

Yes, I never considered 6.06, but that would probably be the more stable version to put on these machines. (Again, I would be really new with this architecture, so everything about the machine would be a learning experience).
If I do get one of the machines with 128 mb, I would definitely put Xubuntu on it, as I have experience with that particular distribution and would feel comfortable with it.
This next bit might be a little naive, but what makes the architecture on these machines unable to support Java, Flash, and Shockwave?

---

### Post by hw-tph on 2007-01-02
> **teejay17 said:**
> This next bit might be a little naive, but what makes the architecture on these machines unable to support Java, Flash, and Shockwave?

The software you mention are not open source (well, Java is about to become that at some point in the future). They are distributed in binary form, compiled for the old "PC" (Intel x86) architecture and in some cases for 64bit Intel. So even if there are versions for Linux there are no versions of them for Linux on the (Ultra-)Sparc.

I don't see Adobe spending any time at all developing Flash/Shockwave for Linux on non-mainstream architectures any time soon. The Sparc is not considered a desktop processor. About the only ones left in the game by now are Intel and AMD 386 - which is the same architecture...


Håkan

---

### Post by teejay17 on 2007-01-02
Thank you. Now I understand a little better. It's mostly a hardware's popularity that gets drivers developed. 
If I do end up getting one of these older Sun machines, I guess it would be a good experiment, but they would be kind of limited. 
Unless, of course, I write my own code, but that's not something I'm even remotely qualified to do:)

---

### Post by netztier on 2007-01-03
> **teejay17 said:**
> If I do end up getting one of these older Sun machines, I guess it would be a good experiment, but they would be kind of limited. 

Well, beefing them up with more RAM actually does help. My U5 has 512MB RAM, which I found for reasonable prices on ebay.

> **teejay17 said:**
> Unless, of course, I write my own code, but that's not something I'm even remotely qualified to do:)

Well, they can make a nice **file**, **mail** or **web** server that sits in a corner somewhere, even a firewall if you put in another Ethernet Card (cards based on Intel's 8255x Chips should do nicely). 

On an U5 (maybe also on a U10), the noise can be substantially reduced if you connect the front case fan to +7V instead of +12V. On a standard power plug for an internal device (CD-ROM), connect it to the +12V and +5V lines (watch for polarity!). Or use a fan regulator from the start...

best regards

Marc

---

### Post by deserthowler on 2007-02-02
I use an Ultra 30 as my only computer, I have been using Debian Etch. I downloaded Ubuntu and will nstall it on a Ultra 60. There are some of the extras for web browsing that are missing but I don't want or miss them. It's similar to a PII speedwise. I have a 386 which I seldom use. For me the big problem was finding a good monitor for the Creator 3d card. I find it a good solid reliable desktop machine. I am running 1.5 GB memory and 2 9GB hard drives.

Earl

---

### Post by Moulton on 2007-02-03
> **deserthowler said:**
> For me the big problem was finding a good monitor for the Creator 3d card.
There is a passive cable adaptor that will convert from the Sun W3 connector to the VGA connector.  The Sun monitors are interchangeable with VGA monitors if you have the right cable adaptor.

---

### Post by wolfe716 on 2007-02-05
> **teejay17 said:**
> I have the opportunity to get a computer from the Mathematics and Computer Science dept. at my university. They have available:



I'm wondering if it's possible to make a real good desktop computer out of one of these things, for basic computer needs, like net surfing, word processing, etc. 
How would Ubuntu 6.10 for SPARC work on these machines? What would installing it be like? What should I be aware of before going down this path? 
All the experience I have so far with Ubuntu has been with Intel x86 machines.

teejay, I run Ubuntu Server for Sparc on two ultra 5 machines at home and both machines are excellent with Ubuntu/  If you can pick up both a U5 as well as a U10, by all means, I recommend that you do so. :)  I, myself, want an Ultra 10 :)  But, my two Ultra 5s keep me just as happy.

---

