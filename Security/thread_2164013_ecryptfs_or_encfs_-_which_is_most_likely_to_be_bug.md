---
title: "ecryptfs or encfs - which is most likely to be bug free"
date: 2013-07-20
forum: Security
---

### Post by youWho on 2013-07-20
I have just created an encrypted directory with ecryptfs (not home, but a "Private" folder). But after doing it, looking around I see quite a few posts in various places suggesting that ecryptfs has some occasional *but serious* bugs that result in files being corrupted. After searching quite a lot to try to sort this out, my impression is that these bugs were fixed, but is that so? Or rather, if you happen to be pretty much of an expert in this, do you know if ecryptfs is now (ubuntu studio quantal) safe to use; that it won't someday corrupt files I've stored in the Private folder?? And a related question would be: what about encfs (and cryptkeeper, its GUI)? Is that reliably bug free??

Maybe both are fine these days, but the various posts around the interwebs seemed not to provide definitive answers.

Thanks in advance.

Oh and briefly editing this, while I'm at it: what about TrueCrypt? Any opinions re reliability over the long haul??

---

### Post by Dave_L on 2013-07-31
I've used ecryptfs for home directory encryption for 2-1/2 years, first with Ubuntu 10.04 and now 12.04, and have not encountered any file corruption issues.

But I also take the precaution of making daily backups of both the encrypted and unencrypted files.

I've also been using Truecrypt for several years, although not on a daily basis, and have never had a reliability issue with it.

---

### Post by markbl on 2013-08-01
A few years ago I looked at ecryptfs, encfs, and Truecrypt for maintaining a single "Private" directory like yourself. Truecrypt was awkward and ecryptfs had a number of issues, some straight out bugs. So I chose encfs and have used it frequently and happily over the years since. Some time ago, I even created a nice simple "gui" wrapper around encfs and published it at [https://github.com/bulletmark/encfsui](https://github.com/bulletmark/encfsui).

---

