---
title: "Ubuntu Full Disk Encryption + GRUB2"
date: 2010-10-24
forum: Security
---

### Post by DreamShardDev on 2010-10-24
I have read that with alternate CD there is a full disk encryption option available. What exactly does it use is it LUKS or dm-crypt or true crypt. What are the vulnerabilities to full disk encryption. From the information that I have gathered, if they (hacker - assuming that they are well resourced) have physical access to your computer all bets are off. What advantages/disadvantages in comparison to using true crypt. 

Also there is a lot of information out there in regards to hardening up the GRUB boot-loader to protect against particular attacks e.g[ http://www.scribd.com/doc/14933/Securing-Linux-by-Hardening-the-Grub-Boot-Loader]("http://www.scribd.com/doc/14933/Securing-Linux-by-Hardening-the-Grub-Boot-Loader") are the same issues still there in GRUB2 and are there any real good guides to dealing with them.

---

### Post by DreamShardDev on 2010-10-25
bump Cmon somebody has got to know something about this?

---

### Post by TheAlien on 2010-10-25
Hi, that's what I'm using! :)

When I set it up, it says dm_crypt (device mapper). It's not TrueCrypt. Though, as in TrueCrypt, you can choose between AES, Serpent and Twofish algorithms.

It's easy to setup and makes your computer so much safer when it's turned off. No hacker can brake into an encrypted system with AES, Serpent, etc, unless you have a very easy password to guess. But an encrypted system can't protect you when it's decrypted as when you're logged in and using it.

I'm not sure about your hardening of GRUB, except for that if your system is encrypted, it's no point in hardening GRUB at all. If you don't have the right password, you'll simply just not get inside your OS.

I don't think you can use TrueCrypt to encrypt a Linux OS.

Let me know if you want a walk trough to encrypt your Ubuntu OS! :)

---

### Post by tornadof3 on 2010-10-26
I use full disk encryption using this method and have been pretty impressed. Just remember no system is 100% secure. For example the only part of your hard drive not encrypted is the /boot partition. So it would be possible for someone very clever with physical access to your machine to modify GRUB and to somehow store/transmit your password when you type it in on boot and then use that to gain access at a later date.. but this is paranoid mode.

In terms of your laptop being stolen and someone gaining access then this method is about as secure as you're likely to get, assuming you use a strong password. Plus it's fun to play around with encryption and such things. I just like the extra peace of mind that it offers.

---

### Post by zhaotianwu on 2010-11-10
> **TheAlien said:**
> Hi, that's what I'm using! :)

When I set it up, it says dm_crypt (device mapper). It's not TrueCrypt. Though, as in TrueCrypt, you can choose between AES, Serpent and Twofish algorithms.

It's easy to setup and makes your computer so much safer when it's turned off. No hacker can brake into an encrypted system with AES, Serpent, etc, unless you have a very easy password to guess. But an encrypted system can't protect you when it's decrypted as when you're logged in and using it.

I'm not sure about your hardening of GRUB, except for that if your system is encrypted, it's no point in hardening GRUB at all. If you don't have the right password, you'll simply just not get inside your OS.

I don't think you can use TrueCrypt to encrypt a Linux OS.

Let me know if you want a walk trough to encrypt your Ubuntu OS! :)

Hi [TheAlien]("http://ubuntuforums.org/member.php?u=985201"), I'm new to Ubuntu and I am preparing for my first time Ubuntu 10.04 installation for my netbook. I've downloaded ubuntu-10.04.1-desktop-i386.iso along with Universal-USB-Installer-1.8.1.0. How can I implement Full Disk Encryption + GRUB2? Can you walk me through? Do I also need to download so called "alternate CD"? Many thanks.

---

### Post by tornadof3 on 2010-11-10
Whilst it is possible to do it without the alternate CD, I think if you are a new comber to ubuntu/linux in general you will really struggle.

I would recommend downloading the "alternate" CD (current version is 10.10 btw not 10.04) and using the "install to encrypted LVM" option, which basically does a very good job of sorting all of the options for you.

---

### Post by azcrumpty on 2010-11-10
From [wikipedia]("http://http://en.wikipedia.org/wiki/Full_Disk_Encryption") "Full disk encryption does not replace file or directory encryption in all situations. Disk encryption is sometimes used in conjunction with filesystem-level encryption with the intention of providing a more secure implementation...". You should use both. I have done so in the past with an encrypted home partition and encfs. Back then, it wasn't so well automated and I manually mounted the encfs volume. The alternate disk allows both.  Select full encryption for the initial install and home directory encryption at user creation.

---

### Post by funnyelephant on 2010-11-14
Can one of you guys (who uses encrypted LVM)  please paste his /etc/default/grub and /boot/grub/grub.cfg ??

I've killed my system and need these files :(

---

### Post by cyrxi on 2010-12-08
> **funnyelephant said:**
> Can one of you guys (who uses encrypted LVM)  please paste his /etc/default/grub and /boot/grub/grub.cfg ??

I've killed my system and need these files :(

Same deal here - another install hijacked my grub and I can't figure out how to access my encrypted Ubuntu install at all.  I'm usually a pretty knowledgeable guy, but I'm in a pinch this time.

---

### Post by croix on 2010-12-11
I attached my **/etc/default/grub** and **/boot/grub/grub.cfg** from Ubuntu 10.10 64bit. I had to add ".txt" to the file names in order to pass the forum's file upload filter.

This blog post demonstrates how to **mount a LUKS encrypted LVM via LiveCD** and** install grub into the MBR** after it was overwritten: 
[http://pzolee.blogs.balabit.com/en/2010/07/grub-helyreallitas-titkositott-es-lvm-particiok-eseten/](http://pzolee.blogs.balabit.com/en/2010/07/grub-helyreallitas-titkositott-es-lvm-particiok-eseten/)

Good luck!

---

### Post by cyrxi on 2010-12-12
> **croix said:**
> I attached my **/etc/default/grub** and **/boot/grub/grub.cfg** from Ubuntu 10.10 64bit. I had to add ".txt" to the file names in order to pass the forum's file upload filter.

This blog post demonstrates how to **mount a LUKS encrypted LVM via LiveCD** and** install grub into the MBR** after it was overwritten: 
[http://pzolee.blogs.balabit.com/en/2010/07/grub-helyreallitas-titkositott-es-lvm-particiok-eseten/](http://pzolee.blogs.balabit.com/en/2010/07/grub-helyreallitas-titkositott-es-lvm-particiok-eseten/)

Good luck!

Thanks man, I had given up for now.  I'll give it another try later today!

---

