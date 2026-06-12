---
title: "Auto Mount Encrypted Drive"
date: 2009-12-26
forum: Security
---

### Post by RMOP on 2009-12-26
I managed to encrypt the internal drive on my eeePC for use as a data-only partition (Ubuntu 9.10 boots from a 16gb SDHC Class 6 SD Card).

I used [http://www.linuxconfig.org/Partition_Encryption](http://www.linuxconfig.org/Partition_Encryption) as the guide to setup my encrypted partition. When I login, the encrypted drive is not mounted. If I open it from Nautilus, I'm first prompted for the encryption passphrase, and then for authentication with my user login. The drive is then mounted.

The associated name of the mounted partition is, well, less-than-attractive: **3485b5cd-00ff-4f24-84db-176742963f38**. There's no option to rename this to something more usefully descriptive.

I'd like to have this drive mounted w/o having to open Nautilus and with a label which I have specified. I do NOT mind manually entering the encryption passphrase and the authentication PW.

I'm not sure what entries to add to fstab and/or /etc/security/pam_mount.conf to effect the desired result.

Help, please? Thanks.

---

