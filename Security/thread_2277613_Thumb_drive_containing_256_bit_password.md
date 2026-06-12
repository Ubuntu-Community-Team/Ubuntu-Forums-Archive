---
title: "Thumb drive containing 256 bit password?"
date: 2015-05-10
forum: Security
---

### Post by tom60 on 2015-05-10
My friend requires a thumb drive (flash drive, whatever) to be inserted in the computer before he can access his email, accounts, etc.  He said that the thumb drive has a 256 bit password on it.  Is this common technology?  Is it something that mortal, i.e. poor, people can use?

---

### Post by TheFu on 2015-05-10
Depends on the platform.
Ubikey is trying to make it easier. I have a Neo with NFC.  It is non-trivial to determine the best way to configure it.  Nothing is plug and play today - you have to setup PAM authentication for anything non-standard.  BTW - the best practice is to get 2 ubikey's, configure them identically and put one in a safe deposit box for when you misplace the other one on a trip.

[https://www.yubico.com/products/yubikey-hardware/yubikey-neo/](https://www.yubico.com/products/yubikey-hardware/yubikey-neo/)

Of course, you still want to enter some sort of password/phrase for access.  And don't forget that having whole drive encryption, not using suspend or hibernate and having excellent, encrypted backups is absolutely critical. There are attacks against whole drive encryption by replacing the boot image. Most people have the boot image on an external device - not on storage as part of the system. After all - if you care this much about security, don't waste time when the basics aren't handled.

Good OpSec is hard.  Getting it to the "bonehead process" level is hard.

---

