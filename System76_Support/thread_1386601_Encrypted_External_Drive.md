---
title: "Encrypted External Drive"
date: 2010-01-20
forum: System76 Support
---

### Post by Cygnia on 2010-01-20
Greetings, the backstory here is that I just destroyed my PanP4n bought last year with a glass of orange juice into the keyboard... I'm looking into taking it to a repair shop but it's going to be a while, and anyway I don't have high hopes. OJ was pouring out of the laptop when turned upside down.

Anyway on to the main issue at hand: Would you believe that I stupidly formatted my external backup drive with a linux-only file system (I believe ext3, but possibly ext4,) and further saw fit to use Ubuntu's Disk Utility to encrypt the external drive with a password, even though the only other computers I have access to are my 2005 iMac G5 and my roommate's Windows computer? So my problem is that even though I did do a very recent backup, I can't access it.

So we come to the specific problem (thanks for reading this far!) I did think to use a Live CD on my roommate's computer to access the external drive, but neither Ubuntu's nor SuSE's Live CD (Gnome versions in both cases) will work. When I try to mount the drive, it asks for my password and I supply it, but then nothing happens. When I click on the drive entry in the sidebar, an error message says the drive cannot be mounted because it already is. Then when I try to eject it, an error message says it cannot be unmounted because it is busy. Long story short I can't get to the files on the drive.

If anyone can think of a way for me to access this drive other than with a fully installed Ubuntu system I would appreciate it greatly. Thanks for reading.

---

### Post by jdb on 2010-01-20
> **Cygnia said:**
> Greetings, the backstory here is that I just destroyed my PanP4n bought last year with a glass of orange juice into the keyboard... I'm looking into taking it to a repair shop but it's going to be a while, and anyway I don't have high hopes. OJ was pouring out of the laptop when turned upside down.

Anyway on to the main issue at hand: Would you believe that I stupidly formatted my external backup drive with a linux-only file system (I believe ext3, but possibly ext4,) and further saw fit to use Ubuntu's Disk Utility to encrypt the external drive with a password, even though the only other computers I have access to are my 2005 iMac G5 and my roommate's Windows computer? So my problem is that even though I did do a very recent backup, I can't access it.

So we come to the specific problem (thanks for reading this far!) I did think to use a Live CD on my roommate's computer to access the external drive, but neither Ubuntu's nor SuSE's Live CD (Gnome versions in both cases) will work. When I try to mount the drive, it asks for my password and I supply it, but then nothing happens. When I click on the drive entry in the sidebar, an error message says the drive cannot be mounted because it already is. Then when I try to eject it, an error message says it cannot be unmounted because it is busy. Long story short I can't get to the files on the drive.

If anyone can think of a way for me to access this drive other than with a fully installed Ubuntu system I would appreciate it greatly. Thanks for reading.

I'm currently booted to a live USB with Ubuntu 9.10 on it.

I plugged in a USB 250 GB external drive that's encrypted.

I went to
Places > Removable Media
and clicked on 250 GB Encrypted

A box came up that said:
The device "250 GB Hard Disk" contains encrypted data on partition 1.
Password:

I typed in my password and in about 15 seconds the disk showed up on
the desktop and auto-opened in nautilus.

It still showed up in
Places > Removable Media
but without the "encrypted" label

jdb

---

### Post by imhavoc on 2010-01-20
You know, this is why I fear drive encryption. I know it's a good idea. I know it's foolish to not use it (in some cases). But what if the Orange Juice of Doom visits my house?

Fear the OJ!

(I do use some encrypted volumes for some things.)

---

### Post by Cygnia on 2010-01-20
Thanks jdb for confirming that it works as advertised. That's the way it's supposed to work, but it seems strange that the same error messages would occur with both Ubuntu and SuSE's Live CDs. Maybe it's a hardware issue on my roommate's computer, in which case I'm out of luck.

Imhavoc, I now share your reservations about backup drive encryption, as well as the more obvious of my mistakes in not formatting the drive with a cross-platform file system. I must have been drinking something other than OJ that day!

---

