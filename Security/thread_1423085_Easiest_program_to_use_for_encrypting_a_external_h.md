---
title: "Easiest program to use for encrypting a external hard drive"
date: 2010-03-06
forum: Security
---

### Post by dogdo on 2010-03-06
Hi

I currently have my home folder encrypted with 128 bit encfs but i have the back up of that 'in the clear' on my back up hard drive. Im not that great with complicated instructions and especially the terminal so what if any is the easiest program to encrypt with?

---

### Post by HermanAB on 2010-03-06
There are some LUKS wizards here:
[http://www.aeronetworks.ca/luks-usb-howto.html](http://www.aeronetworks.ca/luks-usb-howto.html)

---

### Post by iavor on 2010-03-06
How about TrueCrypt?

---

### Post by Funkey Monkey on 2010-03-06
> **iavor said:**
> How about TrueCrypt?

Agreed. [TrueCrypts]("http://www.truecrypt.org/") is quite nice.

(You need to download it from their site as it is not in the repository)

---

### Post by dogdo on 2010-03-08
Thanks am using truecrypt to put basic aes 128 bit on all my exteranal devices-besides all the information on the truecrypt website is there any tips/important info i should know in advance? 

One thing i noticed is that i can only mount/unmount devices from with the truecrypt interface, not the gnome 'computer-file browser'-is this normal?

---

### Post by rileinc on 2010-03-08
> **dogdo said:**
> One thing i noticed is that i can only mount/unmount devices from with the truecrypt interface, not the gnome 'computer-file browser'-is this normal?yes, dont worry about it.

---

### Post by dogdo on 2010-03-08
But hold on if the ubuntu gnome interface cant mount/unmount my external hard drive-that means the accessing of my data is completely dependent on truecrypt. So while truecrypt is free and open source if this program were to be discontinued or corrupted or for what ever reason unusable this means i could never ever access my data right? 

Is there a way to access data on a truecrypt aes protected external hard drive without using truecrypt?

---

### Post by Funkey Monkey on 2010-03-09
> **dogdo said:**
> But hold on if the ubuntu gnome interface cant mount/unmount my external hard drive-that means the accessing of my data is completely dependent on truecrypt.

Yip, that is why your data is "safe" as truecrypt is responsible for encrypting/decrypting your data.

> So while truecrypt is free and open source if this program were to be discontinued or corrupted or for what ever reason unusable this means i could never ever access my data right?

Make a Truecrypt rescue disk (not sure how its done, ask google)

> Is there a way to access data on a truecrypt aes protected external hard drive without using truecrypt?

Not sure. But if you could would that not pose a possible data security risk?


I think you can place a reasonable level of trust in Truecrypt.
But if you are paranoid, why not read up about making a Truecrypt rescue disk.

---

### Post by leorolla on 2010-06-07
Well... just keep a copy of the truecrypt installation files and you will never depend on the trupcrypt project to access your own data. If truecrypt becomes outdated, you still can decrypt and migrate to another tool... Am I missing something?

I have a question, if you allow. I am also googling and trying to decide the best encryption method for external storing devices, from pendrives to external HD's.

I will try cryptosetup first and see which one goes better...
This tutorial makes it seem really seamless:
[http://www.youtube.com/watch?v=M4JYkZxnhJw](http://www.youtube.com/watch?v=M4JYkZxnhJw)

Ext4 support would be nice to have true backups (with permissions etc).

But being able to access from Windows may eventullay be important.

What's the best solution in this case?

---

### Post by Detonate on 2010-06-07
If you install Easycrypt,which is a GUI frontend for Truecrypt. from the repositories, and run it, the first time you run it, it will open the Truecrypt web page where you can download the Truecrypt tar file which contains an install script.  Doing things the easy way.

---

### Post by FuturePilot on 2010-06-07
> **leorolla said:**
> Well... just keep a copy of the truecrypt installation files and you will never depend on the trupcrypt project to access your own data. If truecrypt becomes outdated, you still can decrypt and migrate to another tool... Am I missing something?

I have a question, if you allow. I am also googling and trying to decide the best encryption method for external storing devices, from pendrives to external HD's.

I will try cryptosetup first and see which one goes better...
This tutorial makes it seem really seamless:
[http://www.youtube.com/watch?v=M4JYkZxnhJw](http://www.youtube.com/watch?v=M4JYkZxnhJw)

Ext4 support would be nice to have true backups (with permissions etc).

But being able to access from Windows may eventullay be important.

What's the best solution in this case?

I use a LUKS (cryptsetup) encrypted flash drive between Linux and Windows. You can access it in Windows using FreeOTFE. But you would have to use a file system that Windows can read. e.g. FAT32.

---

### Post by GrantStoner on 2010-06-13
> **dogdo said:**
> But hold on if the ubuntu gnome interface cant mount/unmount my external hard drive-that means the accessing of my data is completely dependent on truecrypt. So while truecrypt is free and open source if this program were to be discontinued or corrupted or for what ever reason unusable this means i could never ever access my data right? 

Is there a way to access data on a truecrypt aes protected external hard drive without using truecrypt?

Correct, your data is completely dependent on truecrypt, which is why your drive won't need to be mounted by the gnome interface. Truecrypt mounts it for you. Once you encrypt anything, you will need that program to unencrypt, as the gnome interface doesn't have an unencryption program. Truecrypt has become big enough that you won't need to worry about it going under and becoming obsolete or discontinued. If your installation of TC does get corrupted, you can always uninstall and then reinstall it. Also, I believe the rescue disk is only for booting with. Since TC is able to encrypt Windows boot manager, it has the option for the rescue disk in case the boot manager for TC (which replaces the windows one) gets corrupted - this way you can still boot your computer. The rescue disk serves no other purpose than getting you past the boot manager if it fails.

---

### Post by Perkins on 2010-06-14
There is, however, an option to save the encryption headers for any encrypted container.  This serves the same purpose as a rescue disk, it just doesn't make a bootable CD.

---

### Post by GrantStoner on 2010-06-14
> **Perkins said:**
> There is, however, an option to save the encryption headers for any encrypted container.  This serves the same purpose as a rescue disk, it just doesn't make a bootable CD.

If you would this help though if the TC boot manages gets messed up? Cause I was under the impression that TC only recognizes the CD when it boots, no other portables (i.e. flashdrives).

---

### Post by Perkins on 2010-06-14
Truecrypt sticks a header onto encrypted volumes.  This header uses the relatively short password you give it to encrypt a relatively large key for encrypting the rest of the volume.  For whole drive encryption, it has you create a rescue disk with the TrueCrypt bootloader, and the header from your drive.  This way, if something gets corrupted, you can still boot up your machine and fix it.  For non-boot volumes, there is no point to including the bootloader since it serves no purpose.  Instead, just use Backup Volume Header in the tools section to make a copy of the header and then store it someplace safe.  Then, if it gets corrupted, or you change your password and forget it, or anything like that, you can restore the header and (hopefully) recover your data.

---

