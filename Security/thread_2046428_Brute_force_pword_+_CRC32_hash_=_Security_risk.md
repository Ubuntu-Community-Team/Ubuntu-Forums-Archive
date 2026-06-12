---
title: "Brute force pword + CRC32 hash = Security risk?"
date: 2012-08-22
forum: Security
---

### Post by dishbert on 2012-08-22
I'm looking into the security protocols for a large piece of corporate software.  Files arrive containing sensitive data bearing a CRC32 hash total that was run on the data alone.  They also contain second CRC32 hash that was run on the first hash string plus the password of the person who assembled the data.  

My concern is that both hash totals are available to the public and I believe it would be relatively easy to brute force passwords, combine the output with the known value of the first hash, run the second hash and compare the output with the known second value until a match occurs.  At that point the password of the originator would be revealed.

Is this an accurate analysis?  If so I'd like to test the hypothesis.  What brute force algorithm would be appropriate?  I have access the single specific CRC32 C code that is run in both instances.

---

### Post by Stonecold1995 on 2012-08-23
I don't know what you mean by "brute-force algorithm", but if you're asking about a method to brute force it I'd go with HashCat.  It's a program that can either use the CPU or GPU (AMD GPUs are preferable in this case) to attempt to crack a very wide variety of hashes.

As for whether it's secure, I'd say not at all.  The CRC32 algorithm is a [cyclic redundancy check]("https://en.wikipedia.org/wiki/Cyclic_redundancy_check"), not a [cryptographically secure hash algorithm]("https://en.wikipedia.org/wiki/Cryptographic_hash_function").  CRC32 is used to make sure that any change in a file is rapidly detected, because a slight change in a file would result in a big change in the CRC32 hash.  The difference between that and a secure hash function like MD5 (technically considered secure but quite weak now days), SHA1, Whirlpool, Tiger, etc is that the latter are designed to be very difficult to reverse.  If the passwords need to be secure I'd go with something like SHA256.  CRC32 is really quite easy to break I'd assume.

---

### Post by dishbert on 2012-08-23
Thanks for the reply Stonecold.  

I agree that the CRC32 hash is not secure, and one of my recommendations will be to replace it.  In the meantime I'm concerned that passwords have already been compromised and want to test for that possibility.

I just had a look at the HashCat site and I don't see CRC32 listed as a supported algorithm, probably because it's so ancient.

---

