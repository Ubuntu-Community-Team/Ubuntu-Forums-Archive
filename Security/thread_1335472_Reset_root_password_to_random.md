---
title: "Reset root password to random"
date: 2009-11-23
forum: Security
---

### Post by NeatO7364 on 2009-11-23
Hi all,

I just finished installing a program that required me to set the root password so that I could su to perform the installation. Now that it's finished, I'd like to reset the root password via random generator. Is this possible?

Thanks!

---

### Post by snowpine on 2009-11-23
Hi NeatO, this tutorial will tell you everything you need to know, including "Re-disabling your root account":

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

In the future, you should *never* need to enable root login. You can install software by using "sudo" (and if you need a root terminal for sake of following a non-Ubuntu tutorial, "sudo -i").

---

### Post by KIAaze on 2009-11-23
There are a lot of password generators available online.
For offline use, you can use "pwgen" for example:
```
sudo apt-get install pwgen
```

---

### Post by cdenley on 2009-11-23
Ubuntu sets the password hash to an impossible value, which is safer than a random password.
```

sudo usermod -p ! root

```

---

