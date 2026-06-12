---
title: "clamav issue with encrypted files after update"
date: 2009-11-15
forum: Security
---

### Post by Lance1968 on 2009-11-15
After running ubuntu 9.04 and it's updates i ran clamAV virus scanner. Before the update there where no issues but after updating these 4 files I get alot of encrypted.zip files warnings.

clamav
clamav-base
clamav-freshclam
libclamav6

Are these false positives?
Is there an issue with clamav6?
Should this be investigated further?

Any help would be great.

cheers

---

### Post by shad0w_crash on 2009-11-15
The best way is using md5sum or shasum on the libs go to the website and check if they're the same, if not something is wrong (be sure you check all the versions else you're panicing for nothing).

---

