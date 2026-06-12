---
title: "I am proud of myself for this / Installing on UEFI"
date: 2013-10-16
forum: Ubuntu, Linux and OS Chat
---

### Post by boyo1991 on 2013-10-16
Well, it was pretty difficult, but I finally got lubuntu 13.04 up and running. This may not be a big thing for most linux people, but for me, its a pretty high achievement.

First, I tried installing it from within the live cd. I got the error message of "grub2 bootloader could not be installed, without a boot loader..." ect...
Then I tried installing it from the BIOS (which I now learned was actually UEFI, I had no idea what this meant) with the same error message.
THEN. I was getting mad. So, i disabled UEFI from inside the UEFI settings (pretty freaky thinking that you have no BIOS? or am I sort of wrong in thinking that I have no BIOS? lol)
This worked, but I had no sound (Im pretty bad with the terminal so here comes some fun! :P)
I went into the the .cfg file, no go as everything was proper
I then FINALLY found --purge and --reinstall... this worked

but first i tried "sudo apt-get update", "sudo apt-get install pulseaudio" among others, to no avail. I wanted to rip my teeth out!

I've never had a "newer computer" always building my own out of peoples parts from their upgrades. So I have had no experience with UEFI, and the last Ubunu (12.04 LTR) that I had was even done through Wubi. Doesn't mean I couldnt have done it, just never tried.

Normally I'd get stuck on problems like these for WEEKS, this time however, was resolved OVERNIGHT!

Pretty proud of myself, but theres so much more to learn :P

Boyo

---

### Post by ajgreeny on 2013-10-16
Well, done for getting to this point!

Nomenclature is a bit confusing I agree when dealing with BIOS/UEFI, but a motherboard has either one or the other.  BIOS (Basic Input Output System) is the old style MBR system using an msdos partition table which allows only four primary partitions or three primary and one extended which can itself contain many logical partitions; UEFI (Unified Extensible Firmware Interface) is the new version with a GPT partition table which can have a large number of primary partitions.

If you have a UEFI system you can choose to boot any install medium in either UEFI or legacy mode by going into the UEFI settings and choosing how you wish to manage the system; see [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") for details of all this, which even though you've managed so far with your setup, may be helpful in future.

---

### Post by boyo1991 on 2013-10-16
right. much appreciated. this is part of what i looked at in order to get the system running ;) i hate doing things without knowing what im doing lol. so everything that i got going i knew how to do.. ive had plenty of work in BIOS, but i had never had experience with UEFI so it was a bit confusing when i was originally hearing I had to "disable the BIOS" I was like "WHAT! disable the BIOS?????" lol so i did some looking and figured it out :P

---

### Post by coldraven on 2013-10-17
Well done, I'll probably be in the same boat when this ancient laptop dies. I'm not looking forward to learning the dark art of UEFI tinkering.

---

### Post by boyo1991 on 2013-10-17
> **coldraven said:**
> Well done, I'll probably be in the same boat when this ancient laptop dies. I'm not looking forward to learning the dark art of UEFI tinkering.

after sitting in it for a little while its not nearly as difficult as youd think. After a youtube video I was like well duh! LOL

---

