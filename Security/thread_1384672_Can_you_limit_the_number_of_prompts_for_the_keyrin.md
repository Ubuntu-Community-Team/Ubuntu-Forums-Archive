---
title: "Can you limit the number of prompts for the keyring password?"
date: 2010-01-18
forum: Security
---

### Post by joecape on 2010-01-18
I have a standard home set-up for my Ubuntu OS, and I would like to know whether its possible to cut out the repetitive prompts to enter the password, as when you connect to the internet or access files on a partition that's not home, or install new software. Thanks

---

### Post by cariboo on 2010-01-18
In order to install software, or access partitions, you need to be root, as your user doesn't have write permissions to anything but your home partition. 

To stop the keyring from asking for a password, just the current password in seahorse, Applications-->Accessories-->Passwords and Encryption Keys, and delete login, when it ask for a new password, just leave it blank.

I wuold suggest you have a look [here]("https://help.ubuntu.com/community/RootSudo") for why Ubuntu is setup the way it is.

---

