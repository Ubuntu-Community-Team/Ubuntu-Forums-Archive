---
title: "Default disk encryption"
date: 2010-07-16
forum: Security
---

### Post by ooVoh9em on 2010-07-16
Can someone please point me to information regarding the exact implementation of Ubuntu's disk encryption using the alternative CD? I realize it is simply using DM-Crypt and LUKS. However, this leads me to the following question:

- The default cipher used for a LUKS mapped device seems to be aes-cbc-essiv:sha256. Is this the what Ubuntu's alternative CD uses for disk encryption?

What I am hoping is that by default it uses an open-source implementation of the Advanced Encryption Standard, using a 256-bit key, a secure initialization vector, hashed with the Secure Hashing Algorithm-2 (I.E; SHA256 or SHA512). This seems to be the most secure option using the NSA's B-suite of cryptographic functions.

If this is not the default behavior of the alternative installer - can it be changed through the installer before encrypting the entire disk?

---

### Post by FuturePilot on 2010-07-16
> Is this the what Ubuntu's alternative CD uses for disk encryption?
Yes. There are also other options that you can pick from during the install.

---

### Post by rookcifer on 2010-07-16
> **troopa said:**
> What I am hoping is that by default it uses an open-source implementation of the Advanced Encryption Standard, using a 256-bit key, a secure initialization vector, hashed with the Secure Hashing Algorithm-2 (I.E; SHA256 or SHA512). This seems to be the most secure option using the NSA's B-suite of cryptographic functions.

You can use a 256 bit key if you want, but I think it's pointless to do so.  Like I heard someone say on Bruce Schneier's blog: "Which is harder, swimming across the Atlantic or the Pacific?"  That's an apt analogy because cracking 128 bit encryption is like swimming the Atlantic.  Even though it might be easier than swimming the Pacific, no human being can do either.  If we used every computer on earth to attempt to crack a single 128 bit key, the sun would burn out before we were successful.

It's true that the NSA has said 128 bit encryption is good enough only for SECRET information (they require 192 or 256 for TOP SECRET), but you have to remember TOP SECRET info usually needs to be secret for many decades or a century or more.  Even though 128 bit is not brute-forceable, it is possible that we will see attacks that make breaking it much much easier than 2^128 operations (2^128 = brute force).  Therefore, they use 256 bit keys because of the extra rounds.  Besides, AES 192 and 256 have attacks against them that do not work against the 128 bit version.

> If this is not the default behavior of the alternative installer - can it be changed through the installer before encrypting the entire disk?

Yes, you can choose between AES, Twofish and Serpent (and possibly others, I can't remember).  You can choose CBC or XTS as well as the key and hash size. I suggest AES or Twofish (128 bit) as they are both much faster than Serpent.  Serpent is good for encrypting individual files, but there's no way I would encrypt an entire system with it.  It's simply too slow.

And, yes, all of this stuff is open-source.  This is Linux, remember?  No secrets here.

---

