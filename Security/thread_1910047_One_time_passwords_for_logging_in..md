---
title: "One time passwords for logging in."
date: 2012-01-16
forum: Security
---

### Post by solid.aqua on 2012-01-16
Suppose I am not home and I absolutely need to grant access to my machine to someone around. I mean real access, installing packages and other elevated actions. Is there a way to let them in without revealing my password? Like many users, I use the same passwords in lots of different services(I know...) so changing the password afterwards is not an option.

---

### Post by snowpine on 2012-01-16
Yes, you can create a new user for your guest, make sure they are in the "admin" group so they can use sudo. Obviously this guestadmin account will have a different password than your user account (but keep in mind they will have the power to *change* your password, or basically do anything they want). When they are done either delete the user or demote their status from admin to restricted user.

I suppose in a true emergency you could instruct them to boot to recovery mode, this is not something I would recommend as a "best practice" however. [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by CharlesA on 2012-01-16
> **snowpine said:**
> Yes, you can create a new user for your guest, make sure they are in the "admin" group so they can use sudo. Obviously this guestadmin account will have a different password than your user account (but keep in mind they will have the power to *change* your password, or basically do anything they want). When they are done either delete the user or demote their status from admin to restricted user.

I suppose in a true emergency you could instruct them to boot to recovery mode, this is not something I would recommend as a "best practice" however. [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
That sounds like the best way to do it, but I would not recommend it, personally.

Then again physical access = root access anyhow.

---

### Post by saneearth on 2012-01-16
IMHO just creating a guest account is the way to go. Lock it down tigjht.

---

### Post by lswb on 2012-01-16
If this is a one-time emergency type scenario, you can talk them through booting into recovery mode and changing your password on the command line with passwd. They will then be able to log in to your account with the new password that they have set. When you have access to the system again you can change it back the same way.

---

### Post by solid.aqua on 2012-01-16
Thanks to all of you! I will check out user groups:D

---

