---
title: "Install linux on this laptop?"
date: 2009-02-17
forum: The Cafe
---

### Post by dragos240 on 2009-02-17
Okay, so i want some soft of linux on my laptop, problem is, it doesn't have a cd drive or an Ethernet port. Although it can boot from a floppy, lets say i wanted to install ubuntu into this laptop, how could i, is there a file splitter for linux that can do this? Anyways i need some method of installing a linux on my laptop. Any seggestions.

---

### Post by gn2 on 2009-02-17
[Here's one method]("http://support.zenwalk.org/viewtopic.php?f=9&t=12923&p=73070#p73070").

There are others.
I believe it's possible to write an .iso to a hard drive partition and use a floppy to boot it.

---

### Post by Eclipse. on 2009-02-17
There is a very small .iso (couple of mb) which can be used to install, although packages need to be downloaed from the internet and since you have no ethernet cable I guess thats a no.

If your laptop can boot from USB drives then thats your best bet.

---

### Post by dragos240 on 2009-02-17
> **Eclipse. said:**
> There is a very small .iso (couple of mb) which can be used to install, although packages need to be downloaed from the internet and since you have no ethernet cable I guess thats a no.

If your laptop can boot from USB drives then thats your best bet.

It's a windows 98, well used to anyway, so thats a nope. I need some sort of way to install via floppy.

---

### Post by gymophett on 2009-02-17
Wow, the laptop seems old. Would it even be capable or running Ubuntu? Maybe Damn Small Linux.

EDIT: Or Xubuntu. but is there a way you get take teh hard drives out and get the files on it elsewhere? Or maybe you can just buy an external CD drive, I'm sure it would be lots of help along the way.

---

### Post by dragos240 on 2009-02-17
> **gymophett said:**
> Wow, the laptop seems old. Would it even be capable or running Ubuntu? Maybe Damn Small Linux.

It has 256 mb of ram, so it should be able to run gnome. Although, i know this is off topic, but is there a desktop environment that is bare, that could simply display graphics, stuff put in the desktop folder on the desktop and be able to browse files? And possibly be used with TWM? Because i really like that window manager.

---

### Post by gymophett on 2009-02-17
> **dragos240 said:**
> It has 256 mb of ram, so it should be able to run gnome. Although, i know this is off topic, but is there a desktop environment that is bare, that could simply display graphics, stuff put in the desktop folder on the desktop and be able to browse files? And possibly be used with TWM? Because i really like that window manager.

Hmm. Truthfully I don't know.
I'm somewhat of a noob to Linux. Ubuntu should be able to run greatly because I know Windows XP ran fine on 256 mb or ram.
But I still do think and external CD drive would be your best bet. Although they are a little expensive, could you maybe borrow one from a friend?

---

### Post by Sunflower1970 on 2009-02-17
Would this work? Can you take out the hard drive and put it into another laptop with a CD player and install it that way?

Does it have a PCMCIA slot? You could buy a wireless card for it then to install something on it...

---

### Post by venator260 on 2009-02-17
The way that I got Ubuntu on to my laptop was to install on the hard drive with a USB enclosure. Be sure to make that drive bootable. After it was done, I replaced the hard drive and ran sudo dpkg-reconfigure xserver-xorg. I then had to run a Grub rescue disk on the original machine and clean up Grub on the laptop. 

Messy, but it worked just fine. I made sure to partition the disk and I have 2 Linux distros on it, so that I have my main partition and a partition to bail to and run Unetbootin should anything go wrong.

---

### Post by wolfen69 on 2009-02-17
you can get a laptop hard drive to usb adaptor, plug it into a computer, then install whatever on it. i recommend puppy linux for an old computer like that.

---

### Post by zmjjmz on 2009-02-18
256MB RAM will run GNOME, but it will be glacially slow. I would recommend trying Crunchbang Linux, Sidux Xfce, KNOPPIX 6, Damn Small Linux, and others like them.

---

### Post by ssam on 2009-02-18
> **Sunflower1970 said:**
> Would this work? Can you take out the hard drive and put it into another laptop with a CD player and install it that way?

i have done this before. for a laptop with a broken CD drive, that i could not reliably boot over ethernet (seemed to boot from ethernet if it was rebooting, not from cold boots).

i think ubuntu adapts itself fine to different hardware being present than at install. but other distros might for example write an xorg.conf specific to that machines graphics card.

---

### Post by dragos240 on 2009-02-18
> **Sunflower1970 said:**
> Would this work? Can you take out the hard drive and put it into another laptop with a CD player and install it that way?

Does it have a PCMCIA slot? You could buy a wireless card for it then to install something on it...

Yeah, i have 2 laptops, 1 has 4 gb on it with no cd drive and a screen resolution of 1024 by 768 and the other has a cd drive and 1 gb of space and has 800 by 600 screen resolution. Problem is, the laptop with the cd drive can't boot from cds. What now?

---

### Post by dragos240 on 2009-02-20
Bump

---

### Post by dragos240 on 2009-02-21
double bump

---

### Post by ymo on 2009-02-21
> **dragos240 said:**
> Yeah, i have 2 laptops, 1 has 4 gb on it with no cd drive and a screen resolution of 1024 by 768 and the other has a cd drive and 1 gb of space and has 800 by 600 screen resolution. Problem is, the laptop with the cd drive can't boot from cds. What now?I have read (years ago) of using a boot floppy to boot a CD on a computer that has a CD-ROM drive but had no BIOS support for booting directly from a CD.
What devices can each of the laptops boot from?

---

### Post by dragos240 on 2009-02-21
> **ymo said:**
> I have read (years ago) of using a boot floppy to boot a CD on a computer that has a CD-ROM drive but had no BIOS support for booting directly from a CD.
What devices can each of the laptops boot from?

They both can boot from 3.5in floppies and hard drives. Although thats it.

---

### Post by kerry_s on 2009-02-21
try this:
[http://linux.simple.be/debian/floppy](http://linux.simple.be/debian/floppy)

---

### Post by dragos240 on 2009-02-21
> **kerry_s said:**
> try this:
[http://linux.simple.be/debian/floppy](http://linux.simple.be/debian/floppy)

Thanks, i just need 1 more floppy, and this will work, it's lying around somewhere.

EDIT: Found it! Now i just need to wait for my dad to copy the files.

---

### Post by dragos240 on 2009-02-22
BUMP! It says i need to connect to a debian ftp site, i can't connect to the internet!

---

### Post by kerry_s on 2009-02-22
> **dragos240 said:**
> BUMP! It says i need to connect to a debian ftp site, i can't connect to the internet!

you don't have internet? or it doesn't detect it?
please give more details, the more we know, the more we can help.

---

### Post by dragos240 on 2009-02-22
> **kerry_s said:**
> you don't have internet? or it doesn't detect it?
please give more details, the more we know, the more we can help.

I have no Ethernet support whatsoever on my laptop, and the only internet port 1 have is a telephone jack. Also i have a linksys wireless PCMCIA card, but no linux driver or anything.

---

### Post by kerry_s on 2009-02-22
> **dragos240 said:**
> I have no Ethernet support whatsoever on my laptop, and the only internet port 1 have is a telephone jack. Also i have a linksys wireless PCMCIA card, but no linux driver or anything.

okay, that would have been nice to know since the only way your going to get a full install is over the internet.
can you get a ethernet card? i use a speedstream card on this laptop i'm typing on now, it don't have ethernet either. ;)

i'll get back to you let me look around.

---

### Post by dragos240 on 2009-02-22
> **kerry_s said:**
> okay, that would have been nice to know since the only way your going to get a full install is over the internet.
can you get a ethernet card? i use a speedstream card on this laptop i'm typing on now, it don't have ethernet either. ;)

i'll get back to you let me look around.

My dad claims he had a PCMCIA Ethernet card, would that work, does debian have drivers for that?

---

### Post by Compucore on 2009-02-22
Well if you have a usb port available and a external cd rom or dvd player that you can hook it up to your laptop there. Then go it that root. If not then find out which one you can install via floppy.

Compucore

---

### Post by dragos240 on 2009-02-22
> **Compucore said:**
> Well if you have a usb port available and a external cd rom or dvd player that you can hook it up to your laptop there. Then go it that root. If not then find out which one you can install via floppy.

Compucore

I have an old external cd-rom drive that hooks up to the PCMCIA slot, but it requires drivers.

---

### Post by kerry_s on 2009-02-22
> **dragos240 said:**
> My dad claims he had a PCMCIA Ethernet card, would that work, does debian have drivers for that?

it's worth a shot. linux has the best hardware support out of the box of all os's.

i'll look into floppy booting that cdrom just in case, i know i saw something on that a long time ago.

---

