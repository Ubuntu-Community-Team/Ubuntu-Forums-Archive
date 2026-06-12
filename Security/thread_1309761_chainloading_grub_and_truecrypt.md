---
title: "chainloading grub and truecrypt"
date: 2009-11-01
forum: Security
---

### Post by n00b512 on 2009-11-01
I've been trying to follow the instructions here:   [http://ubuntuforums.org/showthread.php?t=761530](http://ubuntuforums.org/showthread.php?t=761530)    But those instructions were written for Ubuntu 8 and there seem to have been some changes to grub and the commands used.  I'm too new to linux to fix the instructions or translate into what it should be.  Can anyone help me with this?  So far I've run into several problems.  In the beginning it says to mount the partition containing grub as /mnt/boot/ but on my system grub has been overwritten by truecrypt and is not on any volume header.  I did manage to create a 100 Mb volume labeled &quot;boot&quot; at the beginning of my linux partition and mark it as bootable, but it has no boot files.    Copying the truecrypt mbr files went ok, but then trying to create a grub boot loader hit a wall.  I had booted off the live cd, since I can't get into my ubuntu install, but when I tried to run grub it told me it was not installed.  I finally managed to connect to the internet and download grub using get app, but then when I tried to run the install command it didn't work.  I think the command syntax needs tweaking but I don't know what to change.  I think the new grub takes different commands.

---

### Post by fargle on 2009-11-10
Are you really stuck on full-disk encryption with TrueCrypt?  The reason I ask is that, you can pretty easily do full-disk with dm-crypt built into Ubuntu quite a lot more easily and with less to break.

In either case, you're going to have some unencrypted boot files, the question is whether those are TrueCrypt boot files that you have no clue about, or the files in your /boot partition which are quite straightforward.

I have everything on my system except /boot encrypted and it works great, just requires a boot-up passphrase to unlock the root drive.  It also has encrypted swap (with a random key) and an auto-mounting encrypted home directory that's encrypted with my user account login passphrase.

Two big advantages in my book: very well supported, open source, and no tedious mucking about during upgrades.

Anyway, I can't help you with TrueCrypt full-disk, but it doesn't appear anyone else can either - but I'll be glad to help with what I described, it's easy to set up with the alternate install disk.  Just did it last week with Karmic.

---

