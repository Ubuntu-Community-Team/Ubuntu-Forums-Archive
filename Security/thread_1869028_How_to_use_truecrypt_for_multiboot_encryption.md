---
title: "How to use truecrypt for multiboot encryption"
date: 2011-10-25
forum: Security
---

### Post by shayno90 on 2011-10-25
Has anyone successfully encrypted a netbook/laptop with OS's MS W 7 and Ubuntu 10.10 using Truecrypt?

I would like to find out if it is possible otherwise is there another alternative?

I know there is an option for multiboot encryption on the Truecrypt program however before attempting this and corrupting the MBR, any feedback on this would be helpful.

---

### Post by pcarlos853 on 2011-10-25
To the best of my knowledge that is not possible yet.

---

### Post by shayno90 on 2011-11-22
Ended up doing the single boot encryption of the hard disk for Windows. Seems it is best to encrypt the home folders on Ubuntu during install and it should be possible to encrypt it post installation. 

I didn't attempt the multiboot encryption as I read that it isn't possible to get Truecrypt encrypt both even the option exists.

Interested to know if this has been attempted or is even possible to encrypt both.

---

### Post by jrr_wired on 2011-11-24
Use the same partition file across each OS.  TrueCrypt will still open the file when it's mounted.

---

### Post by shayno90 on 2012-04-12
After upgrading Ubuntu 10.10 to 11.10 as it is no longer supported, the upgrade changed the boot loader.

Hence, Truecrypt bootloader no longer boots by asking you for a password and Windows is not bootable as the boot sector has been corrupted.

Since Windows was only encrypted by Truecrypt and not Ubuntu, the change in GRUB2 by the new Ubuntu release messed up the Truecrypt bootloader.

Lesson here is do not upgrade Ubuntu as it will corrupt the Truecrypt bootloader and ideally get encryption software thats works for both Ubuntu and Windows!!

---

### Post by BenWhitey on 2013-02-05
The way to setup truecrypt with a dual boot computer is to have the MBR operated by truecrypt and linked to windows. Then when you want to boot into linux instead of typing in your password you push escape and then your computer will search for another boot partition and find the /boot for your linux and try to boot from that. That's how I set it up with 12.04 a few months ago and it worked perfectly. Then I got an SSD and tried to get 12.10 to work.

---

