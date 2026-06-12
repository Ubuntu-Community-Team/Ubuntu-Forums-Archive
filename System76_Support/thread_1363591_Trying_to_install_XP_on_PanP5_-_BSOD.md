---
title: "Trying to install XP on PanP5 - BSOD"
date: 2009-12-24
forum: System76 Support
---

### Post by marshmallow1304 on 2009-12-24
I'm trying to install Windows XP Home on my Pangolin (PanP5, see sig).  Besides making me feel unclean, Windows does not seem to want to install.  It loads up all its drivers, then gives me a blue screen of death.

[QUOTE=BSOD]A problem has been detected and Windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this Stop error screen, restart your computer.  If this screen appears again, follow these steps:

Check for viruses on your computer [hehe], remove any newly installed hard drives or hard drive controllers, check your hard drive to make sure it is properly configured and terminated.  Run CHKDSK /F to check for hard drive corruption, and then restart your computer.

Technical information:

*** STOP: 0x0000007B (0xF78D663C, 0x00000034, 0x00000000, 0x00000000)[/QUOTE]

Research says this is "INACCESSIBLE_BOOT_DEVICE", but I have no idea how to fix it.  I know Windows is not supported, but perhaps someone else has experience with XP on the Pangolin.


Edit: Is the problem that I don't have a driver for the SATA II drive?

---

### Post by jdb on 2009-12-24
> **marshmallow1304 said:**
> I'm trying to install Windows XP Home on my Pangolin (PanP5, see sig).  Besides making me feel unclean, Windows does not seem to want to install.  It loads up all its drivers, then gives me a blue screen of death.



Research says this is "INACCESSIBLE_BOOT_DEVICE", but I have no idea how to fix it.  I know Windows is not supported, but perhaps someone else has experience with XP on the Pangolin.


Edit: Is the problem that I don't have a driver for the SATA II drive?

Just a stab in the dark, but you might see if the boot flag is set for that partition.

It will be listed in the flags column of gparted if it is.

The boot flag is required for windows but not used in Linux.

jdb

---

### Post by marshmallow1304 on 2009-12-24
Thank you, but I got it to work.  I changed a setting in the BIOS (I can't remember it now, but I will post the exact setting later.).  I changed it from AHCI to IDE, which allowed Windows to recognize the hard drive.  It is currently installing, so I will be able to play games on Christmas after all. :popcorn:

---

### Post by marshmallow1304 on 2009-12-24
Now, I'm trying to fix Grub, and I'm getting this.

```
root@ubuntu:/home/ubuntu# grub-install --root-directory=/media/root /dev/sda
grub-setup: warn: This msdos-style partition label has no post-MBR gap; embedding won't be possible!
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly

```

---

### Post by Eldera on 2009-12-24
I am quite inexperienced and have never used this, but there is an article on Grub in the 76 knowledge base 
[http://knowledge76.com/index.php/Restore_Grub](http://knowledge76.com/index.php/Restore_Grub)

Does that apply in this case?

---

### Post by jdb on 2009-12-24
> **marshmallow1304 said:**
> Now, I'm trying to fix Grub, and I'm getting this.

```
root@ubuntu:/home/ubuntu# grub-install --root-directory=/media/root /dev/sda
grub-setup: warn: This msdos-style partition label has no post-MBR gap; embedding won't be possible!
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly

```

I think core.img is in grub2 which I know nothing about.
I've been sticking with grub even in 9.10.
I should get with the times & change over, but just don't like all the added complexity.
Maybe I'll learn something about it when you get some replies to this :)

Merry Xmas all !!!!

jdb

---

### Post by marshmallow1304 on 2009-12-24
I ended up wiping my / partition and reinstalling Ubuntu, which would have been easier in the first place.  Now reinstalling all my programs.

---

### Post by Eldera on 2009-12-24
OOOOH, too bad. I guess we win a few and lose a few. Merry Christmas when you get the machine back together again.

---

### Post by marshmallow1304 on 2009-12-24
> **Eldera said:**
> OOOOH, too bad. I guess we win a few and lose a few. Merry Christmas when you get the machine back together again.

Yeah.  The machine is fine, it just needs a lot of updates and installs, in both Ubuntu and Windows.  Merry Christmas to you as well.

---

### Post by marshmallow1304 on 2009-12-25
Hopefully, this can be the last post.  To get XP running on the PanP5, in the BIOS, either set SATA Mode Selection to IDE or set Installed OS to WinXP, which I think does the first one anyway.  Ubuntu doesn't seem to care, but Windows is finicky.

---

