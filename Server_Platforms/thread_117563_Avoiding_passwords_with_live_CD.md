---
title: "Avoiding passwords with live CD"
date: 2006-01-15
forum: Server Platforms
---

### Post by zugvogel on 2006-01-15
I was slightly concerned the other day to discover that all I needed to do to bypass all login passwords was to run the live CD, change to root user and mount the hard drive, to give full access to all files on my computer. Is there any way to prevent this, or is it just a case of putting a password on the bios and disabling boot-by-cd?

---

### Post by Lord Illidan on 2006-01-15
Encrypting your hard drive might work. I dunno how to go about it in Linux, but I think it would work.

---

### Post by LordHunter317 on 2006-01-15
No, there's no easy way to avoid this besides taking the CD-ROM out.  Physical security isn't the operating system's problem.

---

### Post by Mustard on 2006-01-15
[QUOTE=zugvogel]...or is it just a case of putting a password on the bios and disabling boot-by-cd?[/QUOTE]

I would think that is a working solution. :)

I hadn't thought of that one myself.

---

### Post by imagine on 2006-01-15
[QUOTE=zugvogel]I was slightly concerned the other day to discover that all I needed to do to bypass all login passwords was to run the live CD, change to root user and mount the hard drive, to give full access to all files on my computer. Is there any way to prevent this, or is it just a case of putting a password on the bios and disabling boot-by-cd?[/QUOTE]This is no solution, since it takes two minutes to either reset the BIOS or attach the harddisk to another computer.

The only thing which protects your data from someone who has physical access to your harddisk/computer is encryption. This is true for Ubuntu as it is for every other operating system.

---

### Post by gord on 2006-01-17
there is allways [truecrypt](http://www.truecrypt.org/), an opensource peice of software that will create a file on your filesystem that houses a virtual filesystem inside of it that you can move files into, they get encrypted and decrypted automatically.

i havn't had chance to play about with this yet though so it might be rubbish ;)

---

### Post by Mustard on 2006-01-17
[QUOTE=gord]there is allways [truecrypt](http://www.truecrypt.org/), an opensource peice of software that will create a file on your filesystem that houses a virtual filesystem inside of it that you can move files into, they get encrypted and decrypted automatically.

i havn't had chance to play about with this yet though so it might be rubbish ;)[/QUOTE]

I just gave it a go, and its a dog to install. :)

The ubuntu specific .deb package for TrueCrypt 4.1 needs an older kernel installed than the latest kernel ubuntu has.  That meant compiling from source.  This wasn't straightforward either.  I'm going to wait for TrueCrypt to release another ubuntu .deb package that works with the latest kernel, as I really can't be bothered with the 40 mb download of the linux-source that you need to do to get the installation going.

---

### Post by earobinson on 2006-01-17
even a bios password can be reset. [QUOTE=LordHunter317]No, there's no easy way to avoid this besides taking the CD-ROM out.  Physical security isn't the operating system's problem.[/QUOTE] this is correct, for both windows, linux, mac and any other os.

encryption is the only true way to stop this, even then you are not stoping the user from looking at your data only from understanding it. they could copy it off take it to a lab and try and crack it. also they could deleat it.

---

### Post by BSDFreak on 2006-01-18
[quote=earobinson]even a bios password can be reset.  this is correct, for both windows, linux, mac and any other os.

encryption is the only true way to stop this, even then you are not stoping the user from looking at your data only from understanding it. they could copy it off take it to a lab and try and crack it. also they could deleat it.[/quote]

A fully encrypted file system with secure keys would be next to impossible to crack, to delete it is another thing though, backups are essential.

Someone who has access to your computer could easily boot it with a cd/usb stick or whatever and read or copy your files without you even knowing it, or install a keylogger/spyware/whatever. Or if someone stole it...

It's a huge problem security wise, especially with laptops, MS is going in the right direction with their encrypted filesystem in Vista, that's for sure.

---

### Post by earobinson on 2006-01-18
Im with you bsd, it really depends on what you are trying to stop, If you are trying to stop a user gaining axcess to your data then encryption will work, however a user can still tamper with your data.

---

### Post by Copter on 2006-01-25
another thing is performance of encrypted hard disks. data has to be coded decoded on the fly. does any one know how much slower it is comparing to not encrypted drive? (more or less)

copter :]

---

### Post by earobinson on 2006-01-25
It would depend on a lot of things, the strength of the encription, what alg you used.

The best way to put it, is the better the encryption the slower the hd.

---

