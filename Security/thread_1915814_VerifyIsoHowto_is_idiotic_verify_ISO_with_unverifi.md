---
title: "VerifyIsoHowto is idiotic: verify ISO with unverified PGP key ID?"
date: 2012-01-27
forum: Security
---

### Post by throwaway123 on 2012-01-27
I was looking at [https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto) and it seems that the provided solution to verify an unverified data file is to ... download an unverified data file!

Yes. To verify an ISO, one must:

1. download the *unverified* ISO file
2. verifify the *unverified* ISO by downloading an *unverified* SHA256SUMS file
3. verify the *unverified* SHA256SUMS to verifify the *unverified* ISO by downloading an *unverified* PGP key using an *unverified* key ID from an *unverified* website (a wiki no less)

Would it not make more sense to, oh I don't know, INCLUDE THE &quot;Ubuntu CD Image Automatic Signing Key&quot; ON A PREVIOUS RELEASE and tell previous users howto use that?

I'm just saying. This is just idiotic.

---

### Post by CharlesA on 2012-01-27
It looks like they are telling you to verify the MD5SUMS and SHA1SUMS file with PGP to make sure it's not been tampered with.

I don't do that and just grab the file from [http://releases.ubuntu.com](http://releases.ubuntu.com) and verify the sha1sum is the same as the ISO I downloaded.

EDIT: Keep in mind that the last time that wiki page was updated was in 2009.

---

### Post by ottosykora on 2012-01-27
well the only thing which has to be verified as you cal it, is the public key itself. This is done by the distributed trust principe of pgp/gpg.
Once you have a public key signed by some other key and you can get all signing keys from keyserves as well, then the rest of veryfication is pointless as all does verify by itself on the base of a signature atached to the public key itself.
You do not verify the iso, the hash or the website by that, th iso is veryfied automaticaly via the combination of the iso file - hash file- sig on public key as all those are one single item in fact.

---

