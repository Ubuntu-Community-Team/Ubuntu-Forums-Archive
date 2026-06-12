---
title: "Encrypted LVM"
date: 2011-06-06
forum: Security
---

### Post by kurci2 on 2011-06-06
hi!
I wanted to install ubuntu 11.04 with encrypted lvm, using ubntu alternate installer.
I have chosen to use entire hdd with encrypted lvm. But when i was creating user profile installer asked me if i want to encrypt my home folder...

I just want to ask if my home folder is already encrypted also if a dont choose that home encryption??

Thans!

---

### Post by bodhi.zazen on 2011-06-06
It is not clear what you are asking.

If you use LVM/LUKS on the alternate installer, everything except /boot

In addition to LUKS, you are given the option to encrypt your home directory. This option uses ecryptfs.

As to if you need both, it depends, probably using both is overkill. If you have multiple users, and each use requires an encrypted home directory, then yes use both.

---

### Post by kurci2 on 2011-06-06
thanks. You have told me everything i was asking about.

---

