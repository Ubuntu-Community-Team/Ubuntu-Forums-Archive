---
title: "What do I do with the gentoo stage 3 tarball?"
date: 2010-01-21
forum: The Cafe
---

### Post by rajcan on 2010-01-21
Ok, so I want to try out gentoo, and I downloaded the strage 3 tarball so I can go along with their manual, but what do I do with it? I'm not a linux noob so once it's in the computer I know what to do, but what am I supposed to do inorder to get it onto a live cd?

---

### Post by ~sHyLoCk~ on 2010-01-21
Did you read the Handbook?

---

### Post by Techsnap on 2010-01-21
You never followed the manual did you.

---

### Post by rajcan on 2010-01-21
I read the manual, but it doesn't tell you what to do with a *.tar.bz2.tar file. It tells you how to burn a .iso, but not the tarball.

---

### Post by Xbehave on 2010-01-21
gentoo is best installed to a chroot (possibly from a liveCD), the stage3 tar is what you unpack to the root filesystem, it's not a liveCD.

---

### Post by rajcan on 2010-01-21
Ok, I suppose the better question is, do I burn the file to a cd or just copy it over to the cd? Because as far as I know a computer cannot boot off of a .tar file.

---

### Post by Xbehave on 2010-01-21
> **rajcan said:**
> Ok, I suppose the better question is, do I burn the file to a cd or just copy it over to the cd? Because as far as I know a computer cannot boot off of a .tar file.
1) be in a working os (could be ubuntu/debian or a liveCD)
2) create root filsystem(s) and mount it/them (/->/mnt/gentoo,/usr->/mnt/gentoo/usr,etc)
3) unpack the tar into /mnt/gentoo/
4) chroot into /mnt/gentoo/
5) setup core os and kernel
6) boot directly to new install
7) do rest of install
[I]8) ...
9) realise how great binary package managers are
10)come back to ubuntu[/I]

this is all in the guide.

---

### Post by Regenweald on 2010-01-21
> **rajcan said:**
> Ok, I suppose the better question is, do I burn the file to a cd or just copy it over to the cd? Because as far as I know a computer cannot boot off of a .tar file.

dude, shelve your Gentoo aspirations for a few weeks and read the Gentoo handbook. thrice. It is ridiculously detailed and documents *every* step.

---

