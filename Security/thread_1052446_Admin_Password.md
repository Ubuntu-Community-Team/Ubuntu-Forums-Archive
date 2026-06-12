---
title: "Admin Password"
date: 2009-01-27
forum: Security
---

### Post by Taadaa on 2009-01-27
A friend installed Ubuntu 8.04 on my spare computer for me to play with back in November or even earlier.  Just starting to get to play with it now and installing printers & such.  Neither he or I have any idea what the admin password is.  Is there any way to find out, reset it, or do I need to reinstall Ubuntu from scratch to reset?

Thanks

Carolyn

---

### Post by jerome1232 on 2009-01-27
You can reset it using single user mode, just boot the computer up and hit esc when grub start's loading up. Select the highest kernel up that says recovery.

You should end up at a blue screen with a few recovery options, select "drop to a root shell" You'll be landed at a bash prompt.

To change the users password, of course change "username" to the real username of the first user.

```
passwd username
```

---

