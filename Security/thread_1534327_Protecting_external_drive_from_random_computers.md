---
title: "Protecting external drive from random computers?"
date: 2010-07-19
forum: Security
---

### Post by knurledflanges on 2010-07-19
Hi everyone,
I'm not a super technical user, but I get by. I have Ubuntu 9.10 right now and almost always use xfce (old, low-end computer).
I have a 1tb WD Elements external drive that I store a lot of stuff on. Model is WD10000EB035-01. Although I've been being lazy about it, sooner or later I want to get another one just to keep it backed up - with the amount of stuff I've got on it and how cheap they are, seems like there's not really much alternative.
I know it's stupid of me, but I've got no kind of security on the drive right now. I pretty much hit the ground running with it; it's got the one FAT32 partition it came with.
I'm not really worried about encryption or even password protection for privacy's sake with this drive, although I would use them if I knew of a way to do it that worked on any Linux/mac/windows computer I want to plug it into without a hitch. Having things turn into a project when I want to use the drive and just the drive to put some files onto a friend's laptop is something I don't want. It would also ideally be something that doesn't bog down the already-overtaxed hardware I'm usually on. (I have no experience with encrypting drives and don't know how resource-intensive it is).
What I do really worry about is write protection when plugging it into said random friends' laptops and such, which are often windows machines. I don't like that those machines and whatever junk is running on them can do whatever they want to my drive as soon as the OS sees it. Even Ubuntu puts stuff on there that I bet it doesn't need to in order to work. Is there an easy, cross-platform, host-machine-independent way of just making the drive absolutely read-only until a password is given? I know there's probably some way in every OS to make the drive show up as read-only, but I don't want to have to trust that it's going to work right, or learn how to do it in a fully trustable manner for every single computer.
If it's not possible to do this, is there something that I could use to make it read-only for all machines except my own?
Again, I plan on getting another drive to back it up anyway, so solutions where I have to reformat are okay.
Maybe some kind of simple USB device that goes between the host machine and the drive and blocks all write commands?
Thanks all for your help, I really appreciate it.

---

### Post by sgosnell on 2010-07-19
I don't know of a way to do that.  You can either encrypt the drive, or let every computer access it.  I don't know of a way to make a drive read-only by itself, that's done in the OS.  It's simple with an SDHC card, because you can just move the switch on the side and the card is read-only, but I don't know of a way to do that with an HDD.  Not saying it's impossible, just that I've never heard of doing it.

---

### Post by Joe of loath on 2010-07-19
Truecrypt is cross-platform, so if you want to encrypt it it won't be a big issue. There must be an easier way to do it though...

---

### Post by bodhi.zazen on 2010-07-19
> **Joe of loath said:**
> Truecrypt is cross-platform, so if you want to encrypt it it won't be a big issue. There must be an easier way to do it though...

Why would you think there is an easier method then encryption ?

At any rate, you may also use LUKS

LUKS is also available cross platform and does not have the same licensing issues as Truecrypt.

[http://www.freeotfe.org/](http://www.freeotfe.org/)

---

### Post by alphaamanitin on 2010-07-19
Well, TrueCrypt (TC) is all well and nice but you would probably want to set it up to run from the hard drive itself.  But TC has its downfalls, particularly with SSD drives with files already in place when you do the encryption.  Also, unless you do a back up of the headers on the hard drive if they are ever damaged you will never be able to recover your data.  I still think this may be the only solution for you as TC works on Linux, OS, and Windows.  Drives mount in less than a second because it is on the fly encryption.  However, you seem worried about having it be accessable to multiple computers, which indicates to me it is moved around a lot.  If this is true and you use it in multiple locations realize that it would be easy for someone to have a keylogger on the computer and compramise your security.

Anyway, these are just thoughts, some you probably have already had.

AlphaA

---

### Post by alphaamanitin on 2010-07-19
> **bodhi.zazen said:**
> 

[http://www.freeotfe.org/](http://www.freeotfe.org/)

I have not heard of this one, looks very interesting.

AlphaA

---

### Post by WinstonChurchill on 2010-07-19
All ATA (Parallel and SATA) hard drives have a very strong password system implemented in the hardware of the device - you have the ability to set the hard drive so that nobody can access the data on the drive without the password, and I think you can set a user-password that allows it to be accessed read-only like you want. It's an official part of the ATA standard, so it should be pretty universally supported; however, I'm not sure how it works with external hard drives - I haven't really experimented with it before.
See: [http://en.wikipedia.org/wiki/Parallel_ATA#HDD_passwords_and_security](http://en.wikipedia.org/wiki/Parallel_ATA#HDD_passwords_and_security)

Compared to encryption, this isn't quite as impenetrable - there are data recovery services that claim to be able to recover data from locked drives. But unless you're hiding government secrets or something, nobody's going to go to that much trouble. Also, with encryption you have to deal with processor overhead of the cipher, which although minimal with AES on most modern computers, might slow you down on old/lightweight hardware.

btw, It's worth knowing that the read-only switch on SD cards is NOT a hardware thing; it's something the OS/Card Reader has to recognize and enforce. I have an SD reader that completely ignores it.

---

### Post by Joe of loath on 2010-07-19
> **WinstonChurchill said:**
> 
btw, It's worth knowing that the read-only switch on SD cards is NOT a hardware thing; it's something the OS/Card Reader has to recognize and enforce. I have an SD reader that completely ignores it.

It also doesn't work if the two pins assigned to it are particularly dirty or corroded.

---

### Post by FuturePilot on 2010-07-19
> **WinstonChurchill said:**
> All ATA (Parallel and SATA) hard drives have a very strong password system implemented in the hardware of the device - you have the ability to set the hard drive so that nobody can access the data on the drive without the password, and I think you can set a user-password that allows it to be accessed read-only like you want. It's an official part of the ATA standard, so it should be pretty universally supported; however, I'm not sure how it works with external hard drives - I haven't really experimented with it before.
See: [http://en.wikipedia.org/wiki/Parallel_ATA#HDD_passwords_and_security](http://en.wikipedia.org/wiki/Parallel_ATA#HDD_passwords_and_security)

Compared to encryption, this isn't quite as impenetrable - there are data recovery services that claim to be able to recover data from locked drives. But unless you're hiding government secrets or something, nobody's going to go to that much trouble. Also, with encryption you have to deal with processor overhead of the cipher, which although minimal with AES on most modern computers, might slow you down on old/lightweight hardware.


The problem is not all ATA commands can be passed over USB.

---

