---
title: "Full disk encryption on dual boot system"
date: 2011-04-13
forum: Security
---

### Post by Monsuco on 2011-04-13
I currently have a system running Ubuntu 10.10 64-bit and Windows 7 Ultimate SP1 64-bit. I currently use [EXT3 file system drivers]("http://www.ext2fsd.com/") so that Windows 7 can read and write to my ext3 partition and obviously Ubuntu has NTFS-3G built in. Is there any way to implement a full disk encryption system that would still allow the two OSes to read and write to each other's drives?

At the very least I would like it to be possible to have at least one of the two systems be encrypted so I could make an effort to store sensitive information on that drive.

I also plan to move over to EXT4 come 11.04. I used EXT3 because the EXT3 drivers for Windows used to have a lot of problems with EXT4.

---

### Post by ChrisWells on 2011-04-13
I think if you log into windows and use truecrypt to encrypt entire disk it should let you. I made it work with XP/Windows 7, you have to choose the options carefully and make sure the pre boot authentication doesn't overwrite the bootloader.

I made a post on a forum I'll try find it

Edit- ok it was a long time ago what I did was dual boot with 2 partitions and only wanted to encrypt 1 of them that's why I had to mess about with it. I think truecrypt should let you do it from windows.

If the 2 OS's are on diferent drives then I'm not sure if you can read them, I'm not sure if you can mount a full disk encrypted drive either never tried it. Couldn't you just create an encrypted container on whatever drive for sensitive info that way you can read from both OS's?

---

### Post by bodhi.zazen on 2011-04-13
I do not think you can do it easily.

Use Truecrypt for your windows install and LUKS for your Ubuntu install.

The hang up will be to configure a boot loader ;)

---

### Post by Monsuco on 2011-04-13
So will it be possible to install TrueCrypt on Windows and encrypt Windows with TrueCrypt, install the Linux port of TrueCrypt and mount my Windows partition, then, using LUKS and the EXT2/3/4 drivers, encrypt my Linux partition and mount it in Windows with [FreeOTFE]("http://www.freeotfe.org/")? It looks like FreeOTFE [does do]("http://www.freeotfe.org/docs/Main/FAQ.htm#ad") this sort of thing with EXT2/3/4 with the appropriate drivers. Has anyone done something like this and how on earth will I set up my bootloader?

Needless to say I will be saving a fresh image of my HDD just in case this ends up frying my data though I might wait and do this when I install 11.04 (just doing a fresh install, no big deal since I need to do some housecleaning anyways and this gives me a chance to cleanly upgrade to EXT4 now that those drivers appear to support it on Windows 7 reliably).

Also from what I have seen (at least with TrueCrypt), full disk encryption doesn't seem to hurt performance all that much, but I have never used LUKS. Does LUKS hurt performance too much?

---

### Post by bodhi.zazen on 2011-04-13
You can do it exactly as you outline, but it would probably be easier simply have a shared encrypted data partition.

Perhaps the easiest method of full encryption would be to use a removable flash drive for the linux /boot partition (install grub to the /boot partition, not the hard drive).

You can then select to boot from usb (linux) or hard drive (windows) from your BIOS.

---

