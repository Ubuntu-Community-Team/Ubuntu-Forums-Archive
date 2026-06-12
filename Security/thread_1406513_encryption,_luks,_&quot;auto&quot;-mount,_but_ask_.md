---
title: "encryption, luks, &quot;auto&quot;-mount, but ask for password"
date: 2010-02-14
forum: Security
---

### Post by notinuse on 2010-02-14
I know how to mount it manually. I've seen a howto on how to mount it automatically by loging in with the user, you type your username and password and it mounts your encrypted partition. But that's not what I want. My idea is to call cryptsetup and mount on boot, AND ask me for passphrase like when its loading the system, then if I don't type the right password it shouldn't mount /home, even though i type the correct USER password later when the system is loaded(and then I'd have an empty /home since my home partition wasn't mounted due to wrong passphrase).

This is what I tried: I added the commands to rc.local and I don't even feel like it was executed, no passphrase was asked. As a test if commands there were being executed, I tried simple commands lile mkdir /test and it worked. So commands there are executed, yet, no passphrase was asked to me, I looked on dmesg for crypt and found nothing, I pressed alt+ctrl+F1 desiring to find a passprhase-ask and again, nothing.

---

### Post by bodhi.zazen on 2010-02-14
How did you set up your crypt ?

Basically you need to add an entry to fstab:

[http://www.debuntu.org/how-to-encrypted-partitions-over-lvm-with-luks-page-3-install-and-config](http://www.debuntu.org/how-to-encrypted-partitions-over-lvm-with-luks-page-3-install-and-config)

Assuming your initrd is working, if not you will need to add the modules to initrd.

[https://help.ubuntu.com/community/EncryptedFilesystemHowto3](https://help.ubuntu.com/community/EncryptedFilesystemHowto3)

---

### Post by bodhi.zazen on 2010-02-28
> **notinuse said:**
> I know how to mount it manually. I've seen a howto on how to mount it automatically by loging in with the user, you type your username and password and it mounts your encrypted partition. But that's not what I want. My idea is to call cryptsetup and mount on boot, AND ask me for passphrase like when its loading the system, then if I don't type the right password it shouldn't mount /home, even though i type the correct USER password later when the system is loaded(and then I'd have an empty /home since my home partition wasn't mounted due to wrong passphrase).

This is what I tried: I added the commands to rc.local and I don't even feel like it was executed, no passphrase was asked. As a test if commands there were being executed, I tried simple commands lile mkdir /test and it worked. So commands there are executed, yet, no passphrase was asked to me, I looked on dmesg for crypt and found nothing, I pressed alt+ctrl+F1 desiring to find a passprhase-ask and again, nothing.


Lots of questions on LUKS lately, so this is an over view of how it is done :

[http://ubuntuforums.org/showpost.php?p=8893525&postcount=5](http://ubuntuforums.org/showpost.php?p=8893525&postcount=5)

Works here as expected, I am asked for the password as I boot.

---

