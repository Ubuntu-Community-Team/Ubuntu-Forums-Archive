---
title: "LUKS and Luksformat"
date: 2007-02-18
forum: Server Platforms
---

### Post by Vallee on 2007-02-18
Hi

I try to format hda3 with luksformat. I get 

Command failed: Invalid argument

and 

Could not create LUKS device /dev/hda3 at /sbin/luksformat line 53.

Anyone how can help me?

I'm running Ubuntu 6.10......

BR M

---

### Post by jtc on 2007-02-18
Perhaps you could supply the entire command you used?

---

### Post by Vallee on 2007-02-19
Sorry, miss that

I try 

luksformat -t xfs /dev/hda3

and

luksformat -t ext3 /dev/hda3

.

I got the same problem then i try cryptsetup. Got same problem.

Anyone?

---

### Post by jtc on 2007-02-19
Now I see your problem :-) LuksFormat is merely for creating the cryptofilsystem. The actually filesystem (ext3 etc) is the created on top, or perhaps inside, it.

```
cryptsetup luksFormat /dev/hda3
cryptsetup luksOpen /dev/hda3 loopbackname
mkfs.ext3 /dev/mapper/loopbackname
```

Note that this is merely the basic principle. If you haven't already looked at these tutorials I can defiantly recommend them.

[https://help.ubuntu.com/community/Security#head-067b52f485b8a37bf67b9df8c1c9d6fd167dea6a](https://help.ubuntu.com/community/Security#head-067b52f485b8a37bf67b9df8c1c9d6fd167dea6a)

---

### Post by Vallee on 2007-02-19
Thank for your answer.

I have test that command and get this error:

Command failed.root

BR V

---

### Post by jtc on 2007-02-19
I have a few guesses what it could be.

Please paste the entire response you got as well as any eventual questons you've been prompted for and answered.

You know, if we are going to be able to help you, you really need to give us some information :-)

---

### Post by pgf111000 on 2007-02-20
I am running into some troubles with xfs and LUKS; when I attempt to mkfs.xfs on partitions larger than 2-3gb, I receive the following error:

"mkfs.xfs: libxfs_device_zero write failed: Input/output error"

....while mkfs.xfs is executing I notice that the io wait on my opteron is high. When I format partions below 2-3gb, there is no problem whatsoever.   I can format LUKS partitions larger than 2-3gb using mkfs.ext3 without any errors.  I can format blank partitions larger than 2-3gb using mkfs.xfs without a problem.  The problem seems to be between LUKS and XFS.  Any suggestions?


I have posted this question (erroneously) in other seemingly inactive ubuntu forums... for that I apologize.

my setup:

-opteron
-8gb RAM
-multi-terabyte hardware raid6 array
-lvm2
-luks
-xfs
-fc6 host for a lfs build

---

### Post by pgf111000 on 2007-02-20
answer: You must specify the size of the LUKS partition with the command "cryptsetup resize /dev/mapper/whateverpationyouhavemappedto xxxgb" where "xxx" is the size of the desired xfs partition.  This is required for mkfs.xfs to work properly on a LUKS partition (greater than 2gb).  Hopefully this will save some people some time....

---

### Post by posterberg on 2007-02-21
I've been trying
'cryptsetup -c aes-cbc-essiv:sha256 luksFormat /dev/hdb1'
and
'cryptsetup -c aes-cbc-essiv:sha256 luksFormat /dev/hdb'

This is the exact output i get from both tries
--snip--
WARNING!
========
This will overwrite data on /dev/hdb irrevocably.

Are you sure? (Type uppercase yes): yes
Command failed.root@mythtv:/usr/src/linux-headers-2.6.17-11#
--snip--

I don't get anymore even if I try to use --verbose

modules; aes, dm_mod and dm_crypt are loaded.

I am ofc running this as root.

This is my output from '/sbin/modinfo /lib/modules/`uname -r`/kernel/crypto/* |grep description'
--snip--
description:    Rijndael (AES) Cipher Algorithm
description:    Anubis Cryptographic Algorithm
description:    ARC4 Cipher Algorithm
description:    Blowfish Cipher Algorithm
description:    Cast5 Cipher Algorithm
description:    Cast6 Cipher Algorithm
description:    CRC32c (Castagnoli) calculations wrapper for lib/crc32c
description:    Null Cryptographic Algorithms
description:    Deflate Compression Algorithm for IPCOMP
description:    DES & Triple DES EDE Cipher Algorithms
description:    Khazad Cryptographic Algorithm
description:    MD4 Message Digest Algorithm
description:    Michael MIC
description:    Serpent and tnepres (kerneli compatible serpent reversed) Cipher Algorithm
description:    SHA1 Secure Hash Algorithm
description:    SHA256 Secure Hash Algorithm
description:    SHA-512 and SHA-384 Secure Hash Algorithms
description:    Quick & dirty crypto testing module
description:    TEA, XTEA & XETA Cryptographic Algorithms
description:    Tiger Message Digest Algorithm
description:    Twofish Cipher Algorithm
description:    Whirlpool Message Digest Algorithm
--snip--

It just seems likte it shoud work...


Extra info...
cat /proc/version
Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)


Thanks!

---

### Post by jtc on 2007-02-21
> **posterberg said:**
> 
Are you sure? (Type uppercase yes): yes

Take a closer look at that line.

---

### Post by posterberg on 2007-02-22
Damn, that was too simple... :lolflag: 

Thanks mate!!

---

