---
title: "Big News in Crypto"
date: 2012-10-03
forum: Security
---

### Post by rookcifer on 2012-10-03
SHA-3 winner has been announced.  Schneier's entry of Skein did not win. :(  Instead [Keccak won.]("http://news.slashdot.org/story/12/10/02/220203/sha-3-winner-announced")  This is the second time a Schneier entry has made the finals and lost (the other was with Twofish who got beat out by Rijndael to become AES).

For those who don't know, SHA-3 will become the new hashing algorithm standard soon.

---

### Post by Stonecold1995 on 2012-10-03
Cool!  When do you think applications like TrueCrypt will adopt this?

Sadly I don't see SSL-"secured" sites using this any time soon.  So many sites still use horribly weak hash algorithms, even worse than SHA-1 most of the time (as far as I know, correct me if I'm wrong).

---

### Post by rookcifer on 2012-10-03
> **Stonecold1995 said:**
> Cool!  When do you think applications like TrueCrypt will adopt this?

NIST will have to finalize everything first, and then release specifications, etc.  I mean the design is already known and open, but they will have to release docs and implementation info, etc.  I would say it will take most software close to a year to start implementing it, though maybe a little sooner.

> Sadly I don't see SSL-"secured" sites using this any time soon.  So many sites still use horribly weak hash algorithms, even worse than SHA-1 most of the time (as far as I know, correct me if I'm wrong).

Well, MD5 is what you need to avoid.  It is utterly broken.  SHA-1 is still thought to be secure, but has chinks in its armor.  SHA-2 is still very secure by all accounts.

---

### Post by Lars Noodén on 2012-10-03
Doesn't Ubuntu still sign the packages with MD5?

---

### Post by Stonecold1995 on 2012-10-03
> **Lars Noodén said:**
> Doesn't Ubuntu still sign the packages with MD5?

Yes.

---

### Post by zombifier25 on 2012-10-04
I thought they also use SHA-2.

---

