---
title: "ExpressGate install from VirtualBox"
date: 2008-08-23
forum: Virtualisation
---

### Post by AClark on 2008-08-23
So I just built a new machine with a Asus P5QL-E Motherboard.  I was interested in the ExpressGate feature they were advertising (not the main reason for buying the board - but a bonus I thought)

All the hype I had seen before the purchase implied that it was built into flash memory on the motherboard.  It turns out that it is - but you also have to install about 400 meg of files to enable it and it's a Windows based install.

Also buried in the motherboard manual is this little tidbit: 
"ASUS Express Gate supports installation on SATA HDDs in IDE mode only"

This presented a problem as I intended to set my bios to AHCI mode.

Then a little further in the manual a ray of hope:
"ASUS Express Gate supports installation on USB HDDs and Flash drives"

I was planning on installing Hardy as my only OS on this machine - using VirtualBox for any Windows stuff I couldn't get along without so I thought I might be able to install ExpressGate from within my Win2K VM.
I have tested VBox out on a couple of my other machines with Fiesty, Gutsy and Hardy installs and was pretty sure it would serve my needs.

It's ironic that what is a custom Linux distro can only be installed from Windows!

So now I have my machine put together and running with Gutsy installed and VBox with USB enabled and a USB flash drive read/writable from within my Win2K VM.

But when I run the install CD it only gives me C: as a choice for install location. (also reporting there isn't enough space)

I can browse to the flash drive F: in the "change location" portion of the installer but the installer won't let me choose it as a destination.  I have tried formating it as Fat, Fat32 & NTFS with the same result.

I realize I'm pushing it and this isn't what ASUS had in mind but the idea of an "instant on PC" is interesting and I would love to try it out.

I have searched quite a bit but there really isn't much info beyond press releases and a few reviews that don't mention installation.

I checked out the ASUS forums but didn't find anything about installing on a flash drive.  I was going to ask a question there but decided they required too much personal information to register for the forum. 

Anybody installed on a flash drive ?  Anybody know anything about Express Gate ?  Anybody got any ideas about what I might be doing wrong ?  (other than trying to do something that was probably never intended to be done)

---

### Post by quill7111 on 2008-08-26
> It's ironic that what is a custom Linux distro can only be installed from Windows!

Ironic might be too soft a word for it. Maybe "ridiculous"? All the things that I had read about Expressgate were very explicit about it being linux-based, so naturally I assumed it would work with any major distro. It seems like a really cool feature; hopefully asus will come to their senses and release a way to install it under linux. But I am also running my harddrives in AHCI mode, so I guess I'm out of luck too unless you figure out how to get it installed on a USB drive. Very frustrating.

---

### Post by AClark on 2008-08-27
> **quill7111 said:**
> Ironic might be too soft a word for it. Maybe "ridiculous"? 

Ironic, ridiculous, Frustrating - All good words to describe the situation.  

Still hoping someone sees this that has installed Expressgate on a USB flash drive so I can get a clue on where to go from here.

---

### Post by AClark on 2008-09-23
Bump -- Anybody have expressgate installed on a flash drive? 

Anybody figured out a way to have expressgate on a Linux only computer?

---

### Post by esaym on 2008-10-12
These guys have: [http://www.phoronix.com/forums/showthread.php?t=11653](http://www.phoronix.com/forums/showthread.php?t=11653)

Although I can't make any since of their scripts.  Looks like they install expressgate to flash using some kind of img file and then tie it into your current grub menu

---

### Post by AClark on 2008-10-15
A quick look at the post leaves me a little confused as to exactly what they are doing.  Hopefully when our busy season here on the farm slows down a bit I will have time to study it and understand better.  Thanks again.

---

### Post by Mr Henderson on 2010-06-13
I realise this is an old thread, but just thought I'd post a word of warning, having just bought an Express Gate motherboard.

Express Gate doesn't have the necessary drivers to support add-on wireless - e.g. PCI cards. This was stated in an e-mail to me by an Asus rep. after I'd struggled fruitlessly to get my card recognised. Wired LAN is OK.

---

