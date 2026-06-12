---
title: "how secure is md5?"
date: 2007-05-16
forum: The Cafe
---

### Post by proalan on 2007-05-16
just how secure is md5?

I've not touched upon the subject since my university days in 2002 but even at that time there were already discussions about replicating MD5 hashes, bruteforce attacks.

MD5 is widely used to verify downloads including ubuntu cds, packages, programs, email and this forums authentication system amongst many things.

Rainbow tables are just a google search away, and cracking can take as little as 30 mins. 

for more information [http://en.wikipedia.org/wiki/MD5](http://en.wikipedia.org/wiki/MD5)

Is it time to standardize another encryption method e.g. bring sha-1 to common usage?

---

### Post by samjh on 2007-05-16
Both MD5 and SHA-1 are broken.  But they are secure enough for most things, including download verification, and non-sensitive message authentication.

But there are more secure hashes avaiable, such as Whirlpool, RIPEMD-128 and higher, and SHA-256 and higher.  All those are standardised under ISO/IEC 10118-3.

---

### Post by saulgoode on 2007-05-16
So far as providing signature authenticity or protection against decryption, I would agree with your concern. However, I have always considered MD5 to be more of a protection against undetected transmission errors in downloading a file; a purpose it fulfills quite nicely.

---

