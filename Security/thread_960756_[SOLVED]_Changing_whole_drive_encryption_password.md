---
title: "[SOLVED] Changing whole drive encryption password"
date: 2008-10-27
forum: Security
---

### Post by ragtag on 2008-10-27
I set up Ubuntu 8.04 using the alternate cd and used whole drive encryption. This worked flawlessly and I'm very happy with it. I'm just wondering if there is a way I can change the password for the drive encryption (I know the current password, of course)?

Also, how secure is whole drive encryption (if I remember correctly I set it up with 256-bit encryption and a 20+ random character password)? Is it as good as for instance TrueCrypt?

---

### Post by hyper_ch on 2008-10-28
(1) add another password (or keyfile) to it... you can have up to 10 I think... or 8... something like that
(2) delete and old one...

Have a look here: [http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile](http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile)

There you'll find how to add a keyfile... don't specify a keyfile and you will then be prompted to add another password.

Use then "luksDelKey" (I think, check the man page) to remove an existing slot.

As of now, the new key will be slot #1 and the existing key will be slot #0.

---

