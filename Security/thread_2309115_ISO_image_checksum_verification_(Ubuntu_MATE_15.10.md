---
title: "ISO image checksum verification (Ubuntu MATE 15.10)"
date: 2016-01-07
forum: Security
---

### Post by cogset on 2016-01-07
When verifying the signature ( SHA256SUMS.gpg) for Ubuntu MATE 15.10 checksums I'm getting this :

```
gpg: Signature made Thu 12 Nov 2015 01:51:17 AM CET using DSA key ID FBB75451
gpg: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
(skip)
Primary key fingerprint: C598 6B4F 1257 FFA8 6632  CBA7 4618 1433 FBB7 5451
gpg: Signature made Thu 12 Nov 2015 01:51:17 AM CET using RSA key ID EFE21092
gpg: Can't check signature: public key not found

```

is this file signed with two different keys?

I think it's the first time that I see this two keys thing.

---

### Post by zephyr2 on 2016-02-10
I noticed the same thing a few weeks ago. Indeed, [two keys]("https://help.ubuntu.com/community/VerifyIsoHowto#Find_out_what_key_was_used_to_issue_the_signature"):
> 
The key IDs are 0xFBB75451 (generated in 2004, deprecated) and 0xEFE21092 (generated in 2012, current).

Seems you didn't (successfully) request the current key, EFE21092.  I ran into this problem as well and ended up retrieving them from another keyserver (maybe hkp://pgp.mit.edu).

---

