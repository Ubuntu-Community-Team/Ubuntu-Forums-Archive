---
title: "how to encrypt my data"
date: 2015-12-21
forum: Security
---

### Post by Tommy_Maersk on 2015-12-21
Hey

How can I encrypt my data on harddrives? I have a few external harddrives with some data on I would like encrypted, whats the best software for that? I want to be able to make a fresh install of ubuntu once in a while, and still be able to access my encrypted data on the external harddrives?

Whats the best solutions for encryption of terabytes of data in ubuntu/linux?

Thanks

---

### Post by SeijiSensei on 2015-12-21
[https://wiki.archlinux.org/index.php/Dm-crypt/Encrypting_a_non-root_file_system#Partition](https://wiki.archlinux.org/index.php/Dm-crypt/Encrypting_a_non-root_file_system#Partition)

The example shows how to encrypt /home.

---

### Post by kevdog on 2015-12-22
I honestly would refer to this wiki -- [https://wiki.archlinux.org/index.php/Disk_encryption](https://wiki.archlinux.org/index.php/Disk_encryption). It's a pretty good reference to all different types of encryption.  I realize its from the Arch Wiki however every single ones of these options could be implemented in Ubuntu

---

### Post by HermanAB on 2015-12-23
Basically, you need gparted to partition the disk and cryptsetup to encrypt it with LUKS.  There is a front end for cryptsetup called zulucrypt if you are command line challenged.  It should be in the repos.

---

