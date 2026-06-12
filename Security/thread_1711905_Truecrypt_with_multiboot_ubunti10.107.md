---
title: "Truecrypt with multiboot ubunti10.10/7"
date: 2011-03-21
forum: Security
---

### Post by Greshapa on 2011-03-21
Hello, 

I work for a all-in-one IT company, basically businesses hire us and we  will fix all their problems from servers to pencil sharpeners.

I want to get some background with UNIX so i wanted to multiboot linux  on my laptop and use it for a few weeks. After a few hours of trial and  error i managed to install it! 

So to the point: i used Truecrypt to encrypt my laptop and it used a  special boot loader that made me input the password just after the post.

**My question is, can i use Truecrypt with a multiboot 7/ubuntu?**  After it took me hours to install this , running into and trouble  shooting various problems that were probably just my ignorance, but  Linux feels very fragile and i do not want to screw it up.

Thanks!

---

### Post by MarkJM on 2011-03-22
Hi.
I had a big play around for a few months last year doing this for myself.  I used to use Truecrypt for full disk encryption running just Windows 7 but then installed Ubuntu (Lucid) using WUBI to see if I liked it.  This worked fine and didn't disrupt the boot loader, but when I decided to install Lucid as a dual boot I hit problems booting up.

Truecrypt does do multiboot - but not for mixes of different type of OS.  They do have a good help page - either online or with the tool itself.  I keep my files separate from both OSs anyway in their own partition and decided the simplest way was to set up several large truecrypt containers in this partition to keep my stuff in.  The Windows 7 partition is not encrypted, but my Ubuntu partition is through its own encryption.  I can access my containers from either OS.

If you go down this path, make sure you always create the containers while in Windows - otherwise you may end up with a container that only Ubuntu will recognise.  But as first point hinted - if you just want to test out Ubuntu do it through WUBI.

Cheers:popcorn:

---

### Post by bodhi.zazen on 2011-03-22
With Linux you can not use Truecrypt to encrypt your installation.

Your options are to:

1. Use the "desktop" CD -> Encrypt /home this uses ecryuptfs

2. Use the alternate CD and encrypt the entire system. This uses LUKS. With this options you can not encrypt /boot, so you need a separate /boot partition.

---

### Post by rookcifer on 2011-03-23
> **Greshapa said:**
> **My question is, can i use Truecrypt with a multiboot 7/ubuntu?** 
Thanks!

Probably not.  Truecrypt for Windows requires access to the MBR and this would interfere with GRUB.  You can go to the Truecrypt forums and read there -- I am pretty sure other people have asked this question before.  However, I don't remember if anyone found a way to dual boot Windows and Linux with both fully encrypted.  There may or may not be work arounds.

---

### Post by EJeanmaire on 2011-03-24
You can use TrueCrypt to encrypt Windows, and use the TrueCrypt bootloader, and it gives you the option to boot from other harddrives outside of truecrypt/windows.  From there you can boot in to Linux (and encrypt that using luks).

---

