---
title: "Are there alternatives to sha1sum and md5sum?"
date: 2009-06-03
forum: Security
---

### Post by learningcurb on 2009-06-03
I recently heard that SHA1 has been broken.  Is there an alternative program that can conveniently generate and compare checksum lists?

---

### Post by oldsoundguy on 2009-06-03
HashCalc shows that there are  currently 13 check sum type programs.

---

### Post by sonofusion82 on 2009-06-03
sha256sum or sha512 for 256-bit or 512-bit hashes

but it really depends on what you want to protect, for most general purpose checksum usage, md5 and sha1 are good enough.

if you really want secure hashes, then you will need signed type like gnupg message signatures that requires public/private key pair.

---

### Post by yogg on 2009-06-03
> **sonofusion82 said:**
> 
if you really want secure hashes, then you will need signed type like gnupg message signatures that requires public/private key pair.

Signatures will not increase the security of hashes (like MD5 or SH1). If someone can break the hash algorithms then he can create messages with the same hash value (collisions). The receiver calculates the hash of the message and tests if the signature is valid. -> No problem because the hash value is the same.

All parts of the chain have to be strong, else the chain will break.

---

### Post by fenix849 on 2009-06-03
The thing that requires understanding regarding hashing algorithms, is that so long as the hash output value is shorter than the content your hashing, there will be the possibility of conflicts.

The bigger the disparity between hash size and file size the more frequent collisions become (we're talking .000N% here), this doesn't necessarily mean you should stop using them, most of the collisions that have been found have been where the source is a document, and the collision is just random garbage that happens to set off that collision. Hardly useful to an attacker.

Knowing that MD5 has a collision vulnerability is one thing, being able to find a collision that's useful is a whole other ballgame.

---

### Post by kevdog on 2009-06-04
It depends how sensitive you think your data is?  For most people sha1 and md5 are good enough.  The chance of a planned collision -- not a random one -- is essentially nil.  The sha family -- sha1, sha 192, sha256, sha512 is essentially the same algorithm with increasing bits.  One hashing algorithm that I like is whirlpool.  Its one of the finalist for the sha3 competition, among other algorithms.  Check it out!

---

### Post by Agent ME on 2009-06-04
SHA isn't broken, and unless you're trying to shoot yourself in the foot, MD5 isn't broken either.
(It's possible to purposely create a file that has the same MD5 as another. As long as you aren't doing this purposely, MD5 is acceptable.)

---

### Post by learningcurb on 2009-06-05
I'm mainly curious about what best practices for hashing are.  I don't mind spending a bit of extra processing time checking hashes for the extra peace of mind.  Also, according to [Wikipedia]("http://en.wikipedia.org/wiki/SHA1"), Debian uses SHA256 to authenticate their packages.  So maybe it's better to use SHA256 for hashing.

For checksumming data is being stored locally to make sure it's not corrupted or that there are no flipped bits, maybe MD5 or SHA1, or simply putting it on a FreeNAS running ZFS is sufficient.  But perhaps SHA256 is a better choice for signing files sent over the internet if Debian has accepted it as a standard?

Thanks for the tip about Whirlpool by the way.  It looks interesting.  I wonder why Debian doesn't use Whirlpool instead since it sounds reliable and patent free.

---

### Post by kevdog on 2009-06-07
This entire discussion is a mute point.  A new hashing standard known as sha3 -- in no way related to sha1 or sha256 other than in name only, is slated to be named in 2010.  This is in much the same way as rajindael is known as the AES (Advanced Encryption Standard).  Likely everyone will change over to sha3 when the final winner is named.

---

### Post by brallan on 2009-06-25
> **kevdog said:**
> Likely everyone will change over to sha3 when the final winner is named.

It seems that fedora already has chosen "sha256" for their fedora 11 liveCD. I just downloaded it (I need full-disk encryption and the 9.04 alternate CD is not working for me) and have no idea how to go about checking it, since there's nothing in the ubuntu repos that i can find.

I imagine there is some kind of app within the liveCD (have not yet tried it) to do this, but I fail to see how it could possibly be secure. A malicious disk image could simply confirm itself, could it not?

how do I check sha checksums from within ubuntu?

---

### Post by ibutho on 2009-06-25
For sha256, just do 
```
sha256sum somefile.iso
```

---

### Post by brallan on 2009-06-26
> **ibutho said:**
> For sha256, just do 
```
sha256sum somefile.iso
```

thanks, ibutho! I didn't even know i had it installed.

---

### Post by ibutho on 2009-06-26
> **brallan said:**
> thanks, ibutho! I didn't even know i had it installed.

You are welcome. I was baffled by the same problem a few years back only to realise it was a similar process to checking md5sums. :)

---

