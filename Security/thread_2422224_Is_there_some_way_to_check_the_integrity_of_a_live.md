---
title: "Is there some way to check the integrity of a live CD?"
date: 2019-07-03
forum: Security
---

### Post by linux-user-0987 on 2019-07-03
I know it possible to check the MD5 and SHA256 sums of an iso file but what about a live CD thats been installed on a usb or CD?

Is this method applicable to the current version? [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

Since ubuntu iso's can be easily modified, wouldn't it make this method useless? Someone could modify it to say that all packages are original.

---

### Post by CatKiller on 2019-07-04
The website also says what the checksums should be; you don't need to rely solely on the internal check.

The torrent will do it as you go, too.

---

### Post by VMC on 2019-07-04
> **linux-user-0987 said:**
> ...
Since ubuntu iso's can be easily modified, wouldn't it make this method useless? Someone could modify it to say that all packages are original.
Modifying the ISO would change the md5sum.

---

### Post by DuckHook on 2019-07-06
Most Linux distros use MD5 only as a rough indicator to double check that the download is accurate and complete. MD5 has been broken and is a poor tool to check OS/package integrity. To check OS/package integrity itself, distro builders make use of a far more robust method involving certificates.

In order for "someone [to] modify it to say that all packages are original", that someone would have to hack the certificate belonging to Canonical that is used to sign each of the packages making up the OS. This is extremely difficult to do.

Of course, if you insist on downloading your LiveUSB image from i-pwn-you.com, then all bets are off. But if the download or torrent link is straight from Canonical's site, then you are reasonably safe.

---

### Post by VMC on 2019-07-06
Doesn't matter at all. Change 1 bit on any ISO and md5sum changes. Its a good way of telling if ISO has not been not tampered with, as I was replying to **linux-user-0987**

---

### Post by DuckHook on 2019-07-06
> **VMC said:**
> …I was replying to **linux-user-0987**
I too was replying to OP (trying to put mind at ease). Sorry, I should have made that clearer.

---

