---
title: "Change my password for my encrypted /home partition"
date: 2012-05-22
forum: Security
---

### Post by Welly Wu on 2012-05-22
Hi. I have an ASUS N61JV-X2 notebook PC with 8 GB of dual-channel DDR3 PC-8500 SDRAM and an Intel 2nd Generation MLC NAND FLASH X25-M 160 GB Sold State Drive. I installed Ubuntu 12.04 64 bit Long Term Support using the Alternative Install on a CD-R disc. I am using LUKS/LVM with the Serpent cipher in CBC ESSIV SHA-256 mode at 256 bits cipher strength and SHA-512 hash algorithm. I created three separate partitions: 1. encrypted 8 GB swap partition, 2. encrypted 52 GB root partition, 3. encrypted 98 GB home partition.

After I installed Ubuntu 12.04 64 bit LTS, a pop-up window asked me to encrypt my home partition. I put in my old password. Now, I want to change my password used to encrypt my home partition, but I don't know how to re-launch that same pop-up window to make the change.

I looked at Bodhi Zazen's ecryptfs-setup-private with the --force option, but it tells me that my home partition is already mounted.

I installed Cryptkeeper, but I do not see the window at all to make any changes. I keep launching it and nothing happens. I see the Cryptkeeper process in my system monitor, but I can not see the Cryptkeeper window to use the software package.

How do I make a simple change in my password used to encrypt my home partition? Please help with step-by-step instructions. Thank you.

---

### Post by Welly Wu on 2012-05-22
I finally got Cryptkeeper to work. Now, I am trying to learn how to use it. One of the options is to import a ~/.crypt folder. I tried that option, but I can not see my ~/.crypt folder to import it in Cryptkeeper. How do I do this? How does Cryptkeeper work?

---

### Post by Welly Wu on 2012-05-22
This is very important to me. If someone can please help me out so that I can change my password for my /home partition soon, then I would be eternally grateful. I do not want to re-install Ubuntu 12.04 64 bit Long Term Support GNU/Linux from scratch again.

---

### Post by Welly Wu on 2012-05-26
[http://ubuntuforums.org/showthread.php?t=1985276](http://ubuntuforums.org/showthread.php?t=1985276)

---

