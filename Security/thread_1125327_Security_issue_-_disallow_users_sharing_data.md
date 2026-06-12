---
title: "Security issue - disallow users sharing data"
date: 2009-04-14
forum: Security
---

### Post by satimis on 2009-04-14
Hi folks,


Ubuntu 8.04 workstation

3 users share this PC, each having its login and password.  How to stop user reading the home directory of another user.  TIA

B.R.
satimis

---

### Post by bodhi.zazen on 2009-04-14
change the permissions of your home directory.

chmod 770 $HOME

---

### Post by The Cog on 2009-04-14
I would do it this way:
> sudo chmod 750 /home/*
which sets **all** user home directories to be unreadable by the other users.

---

### Post by satimis on 2009-04-15
bodhi.zazen and The Cog,

Thanks for your advice.

Can the user changes the permission back by itself?

TIA


B.R.
satimis

---

### Post by bodhi.zazen on 2009-04-15
users can change permissions on any file or directory they own.

If you wanted to lock down the home directory you would need to make it owned by root.user with permissions of 770

---

