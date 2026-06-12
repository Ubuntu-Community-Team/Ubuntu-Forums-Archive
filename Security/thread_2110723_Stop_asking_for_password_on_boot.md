---
title: "Stop asking for password on boot"
date: 2013-01-31
forum: Security
---

### Post by kr651129 on 2013-01-31
Is there a way to make Ubuntu not ask for a password on boot with an encrypted hard drive?

---

### Post by cariboo on 2013-01-31
> **kr651129 said:**
> Is there a way to make Ubuntu not ask for a password on boot with an encrypted hard drive?

You need the password to unlock your encrypted drive, or what's the sense in encrypting it.

---

### Post by bodhi.zazen on 2013-01-31
Yes, you can do this with a key file. The key file can be stored on the hard drive or more commonly a flash drive.

[http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile](http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile)

---

### Post by Stonecold1995 on 2013-02-05
> **bodhi.zazen said:**
> Yes, you can do this with a key file. The key file can be stored on the hard drive or more commonly a flash drive.
This.  But you have to remember, just because the drive is encrypted doesn't mean you should be careless with where you put the keyfile.  If it's on a flash drive, anyone with access to the flash drive will have access to your computer.

---

