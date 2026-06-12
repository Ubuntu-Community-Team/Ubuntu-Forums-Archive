---
title: "Good evidence to begin migrating from SHA1"
date: 2009-06-10
forum: Security
---

### Post by kevdog on 2009-06-10
I thought I would pass this along to anyone not keeping up with current recommendations regarding use of the SHA1 hash, and with 1024 DSA keys -- as in use with GPG and PGP.

Its a shame SHA3 isn't yet ready for prime time since once its declared I see another transition coming from the SHA2 family to SHA3.

[http://www.debian-administration.org/users/dkg/weblog/48](http://www.debian-administration.org/users/dkg/weblog/48)

---

### Post by rookcifer on 2009-06-10
The Gnupg developers have already switched the default key type to RSA (away from DSA/Elgamal).

---

### Post by kevdog on 2009-06-10
The choice to move from DSA/Elgamal to RSA is only peripherally related to the insecurities of the SHA1 hashing family.  In order to use SHA2 hashes, either an RSA signing key or DSA2 signing key needs to be used (this is a general rule which eliminates rounding or truncation of longer hash values  -- again this truncation is a FIPS mandate).  Because RSA keys are more widely supported than DSA2 implementations -- both which support the use of longer hash values, they chose to use RSA as the default signing key, rather than automatically enable DSA2 by default which would break older implementations.  

Also as a side note -- the Camellia cipher is now officially supported by the OpenGPG standard.  Congratulations to all those using this cipher, particularly those on the Eastern rim.

---

