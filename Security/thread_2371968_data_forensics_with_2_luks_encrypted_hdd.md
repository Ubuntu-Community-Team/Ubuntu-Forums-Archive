---
title: "data forensics with 2 luks encrypted hdd"
date: 2017-09-20
forum: Security
---

### Post by bold33 on 2017-09-20
I hope you understand what I mean:

A person I know formatted the wrong usb stick and important passphrases are now lost. My best bet to find the passphrases is data forensics with a SSD and a HDD

the SSD had a fully working xubuntu installation, but I wanted to install another OS (qubes), but failed, so I installed xubuntu again. The passphrase file may be still in the unit. It was a standard installation, there was a passphrase (I still know it) and a password (I also still know it) to access it. The question here is: should I decrypt and then make an image to try and recover data, or can I mount an encrypted unit with testdisk? I however dd 100% of it but encrypted.

the HDD: had also a fully xubuntu installation. I also know the passphrase to access this HDD. I wanted to encrypt this HDD with luks to use as an external hdd (I mean, wipe out the xubuntu installation), but I couldnt pass the first step and just left the unit alone. The passphrase file may also be in this unit, so I need to also decrypt and make an image to work with (or mount and decrypt with testdisk). This unit fails a bit (I hear that dreadful clack sometimes) and I was able to dd just 85% of it.

help very much appreciated.

---

### Post by HermanAB on 2017-09-28
All I can suggest is to read the cryptsetup man page.  LUKS is very good.  Recovering data from a LUKS partition without all the right keys is practically impossible.

---

