---
title: "install Kernel source offiline?"
date: 2004-12-13
forum: Repositories &amp; Backports
---

### Post by mrbenway on 2004-12-13
Hi, 

I just got the cd's sent from Ubuntu - i got 10, will give them to people for Xmas presents!

I am trying to get my USB ADSL modem working, it should be easy as i've got it working in Mandrake 10.1 , Fedora core 3, Yoper 2.1.

I need the kernel source installed, what files do i need to install and how do i install them, i haven't had much experience with aDebian system before, I can't install from the internet (thats why i'm trying to get the modem working) but i can download from another OS and copy the files to the Ubuntu partition.

Any help would be great!

Cheers.

---

### Post by az on 2004-12-13
You need the linux-source-2.6 or the linux-headers-2.6

You should be able to get by with just the kernel-headers.  They are on your cd.

If you are using the default kernel, it will be named 
linux-headers-2.6-386

Just install that along with build-essential.

---

### Post by mrbenway on 2004-12-13
Thanks for a quick response.

I have actually upgraded my kernel to 2.6.9 which means i can't do that command (i'm not on the net)

I have the following :-

kernel-image-2.6.9-1-k7_2.6.9-3_i386.deb  (i have an athlon XP )
kernel-headers-2.6.9-1-k7_2.6.9-3_i386.deb
kernel-source-2.6.9_2.6.9-3_all.deb

- i installed the kernel using

dpkg - i kernel-image-2.6.9-1-k7_2.6.9-3_i386.deb

- after changing my grub - menu.1st file i was able to boot into the new kernel.
- I can't install the kernel-headers-2.6.9-1-k7_2.6.9-3_i386.deb
-- it gives me dependency errors.

I need to install gcc also but can't due to missing kernel headers.

Any ideas what to do ? (remember i can download files from my windows/other linux to copy to the ubuntu partition)

Would it be more sensible to use the I686 version of the kernel instead of K7?

---

### Post by az on 2004-12-13
Linux-kernel-headers and linux-headers are different packages (I am not in front of an ubuntu computer right now, so gimme a break if I am wrong.)

Where did you get the kernel-image-2.6.9-1-k7_2.6.9-3_i386.deb?  It does not seem to be an Ubunt package.  It would be linux-image-2.6.9.....

Install build-essential to get gcc.

---

