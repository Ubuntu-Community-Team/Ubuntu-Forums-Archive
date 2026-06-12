---
title: "Default AES key size for Gutsy Alternate CD encrypted-LVM installer?"
date: 2008-03-14
forum: Security Discussions
---

### Post by izzydahedgehog on 2008-03-14
I'm running Ubuntu Gutsy on my laptop, with the "encrypted LVM" option from the alternate-install CD.  Recently I started reading up on dm-crypt, LUKS, and so forth, and began poking around.  Executing "cat /proc/crypto" gives me the following output:

name         : sha256
driver       : sha256-generic
module       : sha256
priority     : 0
refcnt       : 1
type         : digest
blocksize    : 64
digestsize   : 32

name         : cbc(aes)
driver       : cbc(aes-i586)
module       : cbc
priority     : 200
refcnt       : 2
type         : blkcipher
blocksize    : 16
min keysize  : 16
max keysize  : 32
ivsize       : 16

name         : aes
driver       : aes-i586
module       : aes_i586
priority     : 200
refcnt       : 3
type         : cipher
blocksize    : 16
min keysize  : 16
max keysize  : 32

name         : md5
driver       : md5-generic
module       : kernel
priority     : 0
refcnt       : 1
type         : digest
blocksize    : 64
digestsize   : 16


I don't know a lot about the implementation (I've only been able to find sparse documentation through Google), but the way I'm reading this is that the AES module it's using only allows keys from 16 to 32 bits!

If I'm wrong, how should these data be read?  If I'm right, is there a way to change the key length without reinstalling everything?  Has anyone who has tried a longer key (since I'm a paranoid SOB, I'd like to shoot for 128 bits or so) experienced unacceptable degradation of performance?

---

### Post by AusIV4 on 2008-04-11
I realize this is a few weeks late, and I'm not sure how that's supposed to be read (I'm trying to find that out myself).

However, running:
```
sudo cryptsetup luksDump /dev/sda2
```
Yields:
```
Version:        1
Cipher name:    aes
Cipher mode:    cbc-essiv:sha256
Hash spec:      sha1
Payload offset: 2056
MK bits:        256
[...]
```
I'm pretty sure the last line there stands for Master Key bits, and is 256 bits, which is what I thought the master key was going to be.

Perhaps someone else can tell us what /proc/crypto is referring to?

---

