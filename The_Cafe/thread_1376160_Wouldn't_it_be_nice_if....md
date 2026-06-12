---
title: "Wouldn't it be nice if..."
date: 2010-01-08
forum: The Cafe
---

### Post by Roasted on 2010-01-08
There was some sort of crazy boot program that would allow users to put any bootable ISO file onto a flash drive and have them multi boot at the splash screen?

I'm looking at it like this. I use quite a few LiveCDs. I utilize several different Linux operating systems... whether it's out of curiosity reasons or to try them out to see if they're worthy to install at work.

I'm cleaning up my case of CDs I use at work. I work in tech so I have all sorts of troubleshooting stuff here, not to mention anytime a new Fedora, openSuSE, Mandriva, BackTrack, Ubuntu, Kubuntu, Xubuntu, etc etc comes out, I bring a new copy of it to work.

It would be so nice to just have some sort of crazy boot loading flash drive that's like 32gb in size and I could just toss whatever bootable iso to it I wanted.

Imagine having one flash drive to boot:

Fedora 12
Ubuntu 9.10
Kubuntu 9.10
Xubuntu 9.10
OpenSuSE 11.2
Clonezilla LiveCD
GParted LiveCD
ReMasterSys
Knoppix LiveCD
Super Grub LiveCD
Helix Forensics LiveCD

etc...

Maybe someday. :)

---

### Post by NoaHall on 2010-01-08
> **Roasted said:**
> There was some sort of crazy boot program that would allow users to put any bootable ISO file onto a flash drive and have them multi boot at the splash screen?

I'm looking at it like this. I use quite a few LiveCDs. I utilize several different Linux operating systems... whether it's out of curiosity reasons or to try them out to see if they're worthy to install at work.

I'm cleaning up my case of CDs I use at work. I work in tech so I have all sorts of troubleshooting stuff here, not to mention anytime a new Fedora, openSuSE, Mandriva, BackTrack, Ubuntu, Kubuntu, Xubuntu, etc etc comes out, I bring a new copy of it to work.

It would be so nice to just have some sort of crazy boot loading flash drive that's like 32gb in size and I could just toss whatever bootable iso to it I wanted.

Imagine having one flash drive to boot:

Fedora 12
Ubuntu 9.10
Kubuntu 9.10
Xubuntu 9.10
OpenSuSE 11.2
Clonezilla LiveCD
GParted LiveCD
ReMasterSys
Knoppix LiveCD
Super Grub LiveCD
Helix Forensics LiveCD

etc...

Maybe someday. :)

What? You mean like Unetbootin bootloader?

---

### Post by Roasted on 2010-01-08
> **NoaHall said:**
> What? You mean like Unetbootin bootloader?

Haven't used unetbootin. It'd just be nice to instead of burning all of these CDs and DVDs I have that I can just get one big fat flash drive, toss whatever ISO I want on it, and it shows up in the boot loader ready to run the LiveCD, install, etc.

---

### Post by NoaHall on 2010-01-08
> **Roasted said:**
> Haven't used unetbootin. It'd just be nice to instead of burning all of these CDs and DVDs I have that I can just get one big fat flash drive, toss whatever ISO I want on it, and it shows up in the boot loader ready to run the LiveCD, install, etc.

Use it then. :)

---

### Post by Roasted on 2010-01-08
> **NoaHall said:**
> Use it then. :)

You're telling me unetbootin is one big fricken boot loader to handle whatever ISO I toss on the flash drive?

---

### Post by NoaHall on 2010-01-08
> **Roasted said:**
> You're telling me unetbootin is one big fricken boot loader to handle whatever ISO I toss on the flash drive?

It should be able to, I've found it can boot most things.

---

### Post by Roasted on 2010-01-08
> **NoaHall said:**
> It should be able to, I've found it can boot most things.

wtf... I must look into this. now.

---

### Post by HappyFeet on 2010-01-08
> **Roasted said:**
> I work in tech so I have all sorts of troubleshooting stuff here

And you don't use Hirens Boot CD? Any tech worth his salt, uses it.

---

### Post by Frak on 2010-01-08
> **HappyFeet said:**
> And you don't use Hirens Boot CD? Any tech worth his salt, uses it.
I've been using WinPE for the longest time. When you work around Windows computers, not surprisingly the best LiveCD is one made from Windows.

---

### Post by Redache on 2010-01-08
I install everything from Flash Drives now, I had one bad DVD burn too many.

Unetbootin is handy for this sort of stuff as well.

---

### Post by CharmyBee on 2010-01-08
Unetbootin only allows you to use one ISO at a time so that's annoying. I wanted to have a stick full of ready-to-boot distros to try.

---

### Post by Roasted on 2010-01-08
> **CharmyBee said:**
> Unetbootin only allows you to use one ISO at a time so that's annoying. I wanted to have a stick full of ready-to-boot distros to try.

awwwwwwwwwww. You're kidding.

That's a killer right there...

However, I could probably get a batch of 2gb flash drives on ebay pretty cheap. That wouldn't be so bad I guess. But it'd be nice to have 1 massive setup...

---

### Post by Nerd King on 2010-01-09
How about this solution.. you need 2 flash drives. One will be your final device.

1. Get ISOs.
2. Use Unetbootin to setup ISO on flash drive A.
3. Boot from flashdrive A, and use live usb to install OS to flash drive B Make sure partition leaves sufficient space for other OSs.
4. Reboot to main OS.
5. Repeat steps 2,3,4 with each ISO.

PS you'll need one hell of a big flash drive for flash drive B!

---

### Post by Frak on 2010-01-09
I keep thinking, it wouldn't be difficult to allow standard ISOs to boot from a boot loader. The only restriction is that the boot loader would need to read from a partition that it can, ehem, read.

---

### Post by NoaHall on 2010-01-09
> **Nerd King said:**
> How about this solution.. you need 2 flash drives. One will be your final device.

1. Get ISOs.
2. Use Unetbootin to setup ISO on flash drive A.
3. Boot from flashdrive A, and use live usb to install OS to flash drive B Make sure partition leaves sufficient space for other OSs.
4. Reboot to main OS.
5. Repeat steps 2,3,4 with each ISO.

PS you'll need one hell of a big flash drive for flash drive B!

You can resize partitions on the flash drive, make lots of 700 MB partitions.

---

### Post by CharlesA on 2010-01-09
I created a bootable flash drive with a bunch of ultilites on it using GRUB4DOS (mapping isos sucks big time). I've read that GRUB2 can boot isos directly, but I've not tried it)

[Link]("http://hak5.org/forums/index.php?showtopic=13842").

---

### Post by oldos2er on 2010-01-09
> **Frak said:**
> I keep thinking, it wouldn't be difficult to allow standard ISOs to boot from a boot loader.

[http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/](http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/)

I haven't looked into this much, but it could be fun to play with.

---

### Post by chris4585 on 2010-01-09
> **CharmyBee said:**
> Unetbootin only allows you to use one ISO at a time so that's annoying. I wanted to have a stick full of ready-to-boot distros to try.

Wrong

A while ago I mastered a process of using unetbootin to make as many distros (that will work with unetbootin) work as you wish. Look down this thread to review what I did.


[http://ubuntuforums.org/archive/index.php/t-1056220.html]("http://ubuntuforums.org/archive/index.php/t-1056220.html")

---

### Post by qalimas on 2010-01-10
> **chris4585 said:**
> Wrong

A while ago I mastered a process of using unetbootin to make as many distros (that will work with unetbootin) work as you wish. Look down this thread to review what I did.


[http://ubuntuforums.org/archive/index.php/t-1056220.html]("http://ubuntuforums.org/archive/index.php/t-1056220.html")


Awesome :D  Doing it now with my collection of ISOs.  Thank you! :popcorn:

---

### Post by Gizenshya on 2010-01-10
> **chris4585 said:**
> Wrong

A while ago I mastered a process of using unetbootin to make as many distros (that will work with unetbootin) work as you wish. Look down this thread to review what I did.


[http://ubuntuforums.org/archive/index.php/t-1056220.html]("http://ubuntuforums.org/archive/index.php/t-1056220.html")

orly?

I'mma have to check that out

---

