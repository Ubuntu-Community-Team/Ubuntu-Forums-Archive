---
title: "System Encryption Help"
date: 2011-08-09
forum: Security
---

### Post by HalfEmptyHero on 2011-08-09
I'm trying to setup my laptop for encryption using [this]("https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto") as a reference, but with some tweaks. I have two hard drives in my laptop, and I am trying to get it so / is on the first hard drive, along with /boot and swap space, and then /home takes up the second hard drive. I've gotten it so that they are all encrypted, and they both mount at boot, but I have to type in the password twice (once for the first hard drive, and once for the second). I would like to only have to type in the password once, as it is very long.  Here's my current setup:

/dev/sda
sda1 = 200MB /boot
sda5 = extended partition with logical volume containing / and swap

/dev/sdb
sdb5 = extended partition with logical volume containing /home

What do I need to do to get what I want? I don't have anything important on there right now, so if my setup is the problem I have no problem changing it. All help is much appreciated.

---

### Post by haqking on 2011-08-09
> **HalfEmptyHero said:**
> I'm trying to setup my laptop for encryption using this as a reference, but with some tweaks. I have two hard drives in my laptop, and I am trying to get it so / is on the first hard drive, along with /boot and swap space, and then /home takes up the second hard drive. I've gotten it so that they are all encrypted, and they both mount at boot, but I have to type in the password twice (once for the first hard drive, and once for the second). Here's my current setup:

/dev/sda
sda1 = 200MB /boot
sda5 = extended partition with logical volume containing / and swap

/dev/sdb
sdb5 = extended partition with logical volume containing /home

What do I need to do to get what I want? I don't have anything important on there right now, so if my setup is the problem I have no problem changing it. All help is much appreciated.


So what is it you want ?

You have shown your current setup and it is what you described ?

You either missed writing what you wanted or i cant read at this time of night ;-)

---

### Post by HalfEmptyHero on 2011-08-09
Woops, fixed it. I want to only have to type in one password to mount both drives.

---

### Post by haqking on 2011-08-09
> **HalfEmptyHero said:**
> Woops, fixed it. I want to only have to type in one password to mount both drives.
 
how have you encrypted the drives ? truecrypt ?

---

### Post by HalfEmptyHero on 2011-08-09
I used luks with this command

**cryptsetup -y --cipher aes-xts-plain --key-size 512 luksFormat /dev/sda5**

---

