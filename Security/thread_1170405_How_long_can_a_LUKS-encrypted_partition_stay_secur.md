---
title: "How long can a LUKS-encrypted partition stay secure?"
date: 2009-05-26
forum: Security
---

### Post by unutbu on 2009-05-26
I recently read this essay
[http://www.schneier.com/blog/archives/2005/02/cryptanalysis_o.html](http://www.schneier.com/blog/archives/2005/02/cryptanalysis_o.html) regarding
breaking SHA-1 hash functions. Since LUKS uses SHA-1 hash keys, the essay led me
to wonder how long would a LUK-encrypted partion stay secure?

The essay is really about finding collisions in SHA-1 hash functions. Is finding
a collision tantamount to cracking a LUKS-encrypted partition?

If so, the following seems to imply a LUKS-encrypted partition will be crackable
by common hardware with less than a day of computation by 2037.


Assumptions:
[list=1]
[*] Moore's Law ([http://en.wikipedia.org/wiki/Moore's_law](http://en.wikipedia.org/wiki/Moore's_law)) -- Computing
performance per unit cost doubles every 24 months
[*] 2^56 calculations can be computed in 56 hours on a $50K machine in 1999.
(See [http://www.schneier.com/blog/archives/2005/02/cryptanalysis_o.html](http://www.schneier.com/blog/archives/2005/02/cryptanalysis_o.html))
[*] 2^69 calculations are required to find a collision in SHA-1.
[*] SHA-1 is used by LUKS encrypted partitions. From the cryptsetup man page:
"LUKS will always use SHA1 in HMAC mode, and no other mode is supported at the moment."
[*] Finding a collision in SHA-1 is equivalent to cracking a LUKS encrypted partition.
[/list]

Let us define a tuple (W,X,Y,Z) where
```
W=the date (in units of years)
X=number of calculations
Y=cost (in dollars)
Z=time required to perform calculations (in hours)
```

Let's say (W,X,Y,Z) is computable if in the year W, X calculations can be
performed in Z hours on hardware costing Y dollars.

So according to [http://www.schneier.com/blog/archives/2005/02/cryptanalysis_o.html](http://www.schneier.com/blog/archives/2005/02/cryptanalysis_o.html),
```
(1999,2^56,50,56) is computable. And by Moore's Law,
(1999+2*13,2^69,50,56)     = (2025,2^69,50,56)  is computable.
(2025+2*4,2^69,50/2^4,56)  = (2033,2^69,3.1,56) is computable.
(2033+2*2,2^69,3.1,56/2^2) = (2037,2^69,3.1,14) is computable.
```

So given the assumptions, a LUKS encrypted partition will be crackable, in 2037, on hardware costing ~$3K in 14 hours.

What do you think? And in particular, is my fourth assumption correct? Is finding a collision in SHA-1 equivalent to cracking a LUKS-encrypted partition?

---

### Post by rookcifer on 2009-05-26
> **unutbu said:**
> I recently read this essay
[http://www.schneier.com/blog/archives/2005/02/cryptanalysis_o.html](http://www.schneier.com/blog/archives/2005/02/cryptanalysis_o.html) regarding
breaking SHA-1 hash functions. Since LUKS uses SHA-1 hash keys, the essay led me
to wonder how long would a LUK-encrypted partion stay secure?

LUKS doesn't have to use SHA-1.  For instance, when setting up LUKS, you can do the following:
```

cryptsetup -y --cipher aes-cbc-essiv:sha256 --key-size 256 luksFormat /dev/hda1
```

This will force the hash used to be sha256 (which is uncrackable right now and will be for a long while).  You can also force it to use other hashes such as RIPEMD, Tiger, Whirlpool, etc..

I checked on the HMAC/SHA1 limitation that you mentioned, and came [across this]("cryptsetup.googlecode.com/svn-history/r42/wiki/LUKS-standard/on-disk-format.pdf"):

> LUKS needs to process password from entropy-weak sources like keyboard input. PKCS #5’s password based key derive function 2 (PBKDF2) has been defined for the purpose to enhance the security properties of entropy-weak password, see [Kal97]. Therefore, LUKS depends on a working implementation of PBKDF2. LUKS uses SHA1 per default as the pseudorandom function (PRF) **but any other hash function can be put in place by setting the hash-spec field.**


So, it seems indeed that SHA1 can be replaced.

---

### Post by unutbu on 2009-05-27
Thank you for the information rookcifer!
There is a lot a don't understand about encryption technology/terminology, including the difference between the HMAC hash which is required to be SHA-1 and other hash which you show how to change to sha256 (or other hashes). 

If anyone can recommend a link explaining how LUKS works, or an answer to the above basic question, I'd appreciate it very much.

By the way, while trying to google for answers, I came across this:
[http://www.schneier.com/blog/archives/2005/02/sha1_broken.html](http://www.schneier.com/blog/archives/2005/02/sha1_broken.html)

This seems to state pretty plainly that my 5th assumption is wrong: Finding a collision in SHA-1 is apparently irrelevant to cracking a LUKS encrypted partition.

---

