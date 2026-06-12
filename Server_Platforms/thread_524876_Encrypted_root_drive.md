---
title: "Encrypted root drive"
date: 2007-08-13
forum: Server Platforms
---

### Post by alex.l on 2007-08-13
Hi all! I want to encrypt mi whole drive, is it possible following this guide

 [https://help.ubuntu.com/community/FeistyEncryptedRootWithInstaller?highlight=%28encrypted%29](https://help.ubuntu.com/community/FeistyEncryptedRootWithInstaller?highlight=%28encrypted%29)

to use plain keyfiles (not encrypted) on removable medias on ubuntu feisty? Since passphrase for luks is the weakest key in the chain i would like to use nonmnemonical-strong-possibly random keyfiles (stored on usb stick) to unlock my partitions ( root and swap)

Thank you. Alex

---

### Post by HermanAB on 2007-08-18
It is usually not a good idea to encrypt the whole drive, since it makes the whole system slower.  The Ubuntu Linux files are all FOSS, so there is nothing secret about them and therefore no point in ecrypting any of it.

To secure your data, you should encrypt /home, /swap and /tmp.  Encrypting anything else is just a waste really.

Cheers,

Herman

---

### Post by squarebug on 2007-08-19
alex.I,
while HermanAB is right about full disk encryption slowing down your system somewhat, it certainly can be done. There are several HowTos in the Ubuntu community docs (entitled  EncryptedFilesystemHowto1,2.. and so on, do a search), which cover almost any variant of file system encryption.
A general statement like 'Encrypting anything else is just a waste really.' is incorrect, it all depends on the level of security you're seeking, and the skills and efforts of the attacker. To find out what is right for you, search for general discussions on security.
Good luck.

---

