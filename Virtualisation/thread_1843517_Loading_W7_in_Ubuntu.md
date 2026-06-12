---
title: "Loading W7 in Ubuntu"
date: 2011-09-13
forum: Virtualisation
---

### Post by cpu2007 on 2011-09-13
Hello everyone, 
I hope someone can help me out with this problem as there seems to be no solution.

I have two operating systems installed on my laptop sony vaio VGN-FW21L.
I want to be able to use my windows 7 operating system and access it while I am using ubuntu.
The only solution I found is to install virtual box which allow to install a virtual operating system but this is NOT what I want as what I am looking for is to be able to use both my operating systems with already installed application and saved documents.

So, is it there anyway I can access my W7 while i'm on ubuntu or viceversa?

Thank you

---

### Post by drdos2006 on 2011-09-13
Ubuntu plus Virtualbox plus Windows 7 is the only way you are going to be able to run two operating systems at the same time, and access the Windows 7 files from Ubuntu.

regards

---

### Post by cpu2007 on 2011-09-13
I am aware of that, what I am asking is, I already have the two operating system installed, how do I access windows 7 through virtualBox while I am on ubuntu?
The only way to access is to make a new installation of windows 7 but this is not what I want, I want to access my  current w7 operating system with all files and application installed.

---

### Post by tweezak on 2011-09-14
I'm trying to do the same thing.

This guy has done it:
[http://wafitz.net/2011/03/converting-duel-boot-windows-7-partition-to-a-vm/](http://wafitz.net/2011/03/converting-duel-boot-windows-7-partition-to-a-vm/)

Unlike most of the others I have found he doesn't image the drive to an external drive and then recreate it as a VM. He actually works with the partition.

The problem is...his method won't work for me. His technique requires having a Windows7 install CD and once he's manipulated the partition he runs the recovery from the CD. I don't have a Windows7 CD...my laptop is one of those wonderful ones that just has a recovery partition.

So it would appear I'm hosed. Does anyone know if I can use the recovery partition in a method similar to an install CD by imaging it to a USB drive?

---

### Post by SecretCode on 2011-09-14
You can do it with Virtualbox - basically step 2 of the page tweezak linked to is all that's needed. Step 0 and 1 are about setting up dual boot - I've never had problems setting up dual boot using just the Ubuntu installation disc.

But accessing a physical partition via a vmdk is fraught with problems - mostly to do with an installed windows not liking to be booted with what it thinks is different hardware. I'd advise you to go to [http://forums.virtualbox.org/](http://forums.virtualbox.org/) and read at least this thread and all its linked threads: [virtualbox.org • View topic - HOWTO: Windows 7: In both VM and native -- VBox3.x](http://forums.virtualbox.org/viewtopic.php?f=28&t=33356) - especially the linked discussion thread on using Vbox 4.

It looks like you only need the Windows installation disc to fix the mbr and there are other solutions to that.

---

### Post by SeijiSensei on 2011-09-14
If you only need access to the files on the Windows side, just mount that partition in Linux with ntfs-3g.  Add an entry to /etc/fstab that looks something like

```
UUID=28BC68DBBC68A552 /windows ntfs defaults,umask=007,gid=46 0 0
```

replacing the UUID above with the one from your Windows partition. You can list the UUIDs on the drive with "sudo blkid".

---

