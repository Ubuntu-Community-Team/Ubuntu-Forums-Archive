---
title: "Password protecting files and folders...."
date: 2009-07-17
forum: Security
---

### Post by DoubleMcLovin on 2009-07-17
So here's the scenario:
I have about 1Tb of files that I would like to have secured through an extremely erroneous password I have, but would like to maintain daily access to them by confirming the password.
I understand I can create an archive of these files and encrypt the archive, but then I don't really have continuous access to them (not to mention this would be a disastrously long and impossible feat due to storage requirements).
Can anyone recommend a creative (or possibly just feasible) way to accomplish a secured directory like this that cannot be read without the password?

---

### Post by brettg on 2009-07-17
Take a look at TrueCrypt

[http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by scorp123 on 2009-07-17
> **DoubleMcLovin said:**
> So here's the scenario:
I have about 1Tb of files that I would like to have secured through an extremely erroneous password I have, but would like to maintain daily access to them by confirming the password.  You might want to look into **encfs** or **ecryptfs** .... Both lock down and encrypt directories.

EncFS:
[http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600)

eCryptFS:
[http://tombuntu.com/index.php/2008/08/07/create-an-encrypted-private-directory-with-ecryptfs/](http://tombuntu.com/index.php/2008/08/07/create-an-encrypted-private-directory-with-ecryptfs/)

---

