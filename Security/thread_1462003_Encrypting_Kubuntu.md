---
title: "Encrypting Kubuntu"
date: 2010-04-25
forum: Security
---

### Post by audiocanine on 2010-04-25
I would like to encrypt my Kubuntu partition and have it require a USB key to boot. I have looked around but cannot seem to find anything on this subject and was wondering if the nice people of the Ubuntu community would be able to help me.   :)

---

### Post by rookcifer on 2010-04-25
> **audiocanine said:**
> I would like to encrypt my Kubuntu partition and have it require a USB key to boot. I have looked around but cannot seem to find anything on this subject and was wondering if the nice people of the Ubuntu community would be able to help me.   :)

First, understand you must wipe the drive and reinstall in order to encrypt it.  Second, you will need the Kubuntu "alternate install" CD.  Once that is done, follow the directions [here.]("http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/")  This tutorial is for 8.04, but it should still work the same.

---

### Post by audiocanine on 2010-04-26
Ok, I have downloaded the alternate install CD and have gone through the installer menu to set up an encrypted partition. When I get to the point where it allows me to configure the partitions before writing the file structure and operating system to them, it doesn't seem to want to let me set my Kubuntu partition as both encrypted and the bootable partition.

---

### Post by bodhi.zazen on 2010-04-27
Your boot partition can not be encrypted.

---

### Post by max-power2717 on 2010-04-28
It is possible to encrypt your entire disk, and use the USB key to initially boot the system. This technique is more technically involved than the useful disk encryption option offered on the alternate CD. 

This [How-To]("http://tldp.org/HOWTO/Disk-Encryption-HOWTO/") explains how it can be done. The document is a bit old, and mainly focuses on the 2.4 kernel, however I'm led to believe that this technique is possible with 2.6 kernels in the same way. 

It may not be worth all of the extra effort using this technique rather than just setting up a small unencrypted boot partition on your disk and using the technique offered by the alternate CD. However, [read this]("http://mareichelt.de/pub/texts.cryptoloop.php") document for an explanation of why this method of disk encryption may not be entirely safe (I say *may* not be, I really don't know how the alternate CD implements disk encryption - can anyone enlighten this thread?). You may want to think about how sensitive your data is and what pains you're willing to go to in order to secure it.

---

### Post by Bob P on 2010-05-02
last weekend as an experiment i built a "totally encrypted" LUKS server using popular distros.  i honestly can't remember if i did it on ubuntu or centos or both.  i used a 256-bit RSA key, and believe me ... it was a royal PITA to key in that 256-bit passphrase at bootup.  making matters worse, i had to do it twice because i had two encrypted drives in the system.  naturally, it made sense to store the passphrase on a USB key that could be inserted prior to boot and removed immediately thereafter.

much to my chagrin, it seems that there are no current distributions that offer a default setups that will read the RSA key from a USB drive at bootup.  to enable this kind of functionality it looks like you have to write your own scripts to modify the boot sequence to perform this task.

life would sure be a lot simpler if any of the distros that "support" full disk/OS encryption also supported reading the RSA key from a USB drive at boot. that would be a KILLER APP and a feather in the hat for the first distribution that supports the feature in a default configuration.   IMO expecting the user to type a long RSA passphrase info into the console at every boot cycle amounts to poor planning and half-baked "support" of encrypted file systems.

---

### Post by audiocanine on 2010-05-03
So then the final verdict is that it is *not* possible for me to encrypt my Kubuntu partition and decrypt it with a USB key if it is selected from the boot menu?

---

### Post by bodhi.zazen on 2010-05-04
> **audiocanine said:**
> So then the final verdict is that it is *not* possible for me to encrypt my Kubuntu partition and decrypt it with a USB key if it is selected from the boot menu?

What ever gave you that idea ?

When booting you need a few files (grub, the kernel, and the initrd). These files can not be encrypted and are thus on a /boot partition.

You can put the entire /boot partition on a US B if you like, that is simple. Without the USB flash drive the system can not boot.

You can also unlock the LUKS partitoin with a key file that is kept on a USB drive.

See:

[http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile](http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile)

---

### Post by rookcifer on 2010-05-04
> **max-power2717 said:**
> 
However, [read this]("http://mareichelt.de/pub/texts.cryptoloop.php") document for an explanation of why this method of disk encryption may not be entirely safe (I say *may* not be, I really don't know how the alternate CD implements disk encryption - can anyone enlighten this thread?). You may want to think about how sensitive your data is and what pains you're willing to go to in order to secure it.

That article is old.  The Linux kernel doesn't even use Cryptoloop anymore (to my knowledge).  I do know for certain that no modern distro uses it.  They all use dm-crypt/LUKS (aka cryptsetup).

> **Bob P said:**
> last weekend as an experiment i built a "totally encrypted" LUKS server using popular distros.  i honestly can't remember if i did it on ubuntu or centos or both.  I used a 256-bit RSA key, and believe me ... it was a royal PITA to key in that 256-bit passphrase at bootup.  making matters worse, i had to do it twice because i had two encrypted drives in the system.  naturally, it made sense to store the passphrase on a USB key that could be inserted prior to boot and removed immediately thereafter.

256 bit is overkill.  If the fastest CPU (or GPU) on earth were a grain of sand and all grains of sand on earth were used to brute force a 256 bit key, it wouldn't be done before the sun burned out.   The algorithm itself is likely to be successfully cryptanalyzed (broken) by mathematical means way before your 256 bit key is in trouble from computational attacks.  Therefore, 128 bit is more than enough for the foreseeable future (as it is effectively unbreakable by brute-force as well).  Any cryptologist will tell you key sizes don't matter anymore -- 128 bit is so big as to be irrelevant to cryptanalysis.    It's the last of their concerns when analyzing a cipher.

---

### Post by audiocanine on 2010-05-07
Ok. Could you guide me through setting up my computer so that my /boot partition is on a USB key and my Kubuntu partition is encrypted?

---

### Post by bodhi.zazen on 2010-05-07
> **audiocanine said:**
> Ok. Could you guide me through setting up my computer so that my /boot partition is on a USB key and my Kubuntu partition is encrypted?

Use the alternate CD and manual partitioning, put /boot on the USB.

[http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml)

It says 8.04 , but it has not changed significantly with 10.04 (the alternate installer that is essentially still the same process).

---

