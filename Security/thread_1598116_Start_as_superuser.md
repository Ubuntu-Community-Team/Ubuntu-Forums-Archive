---
title: "Start as superuser"
date: 2010-10-16
forum: Security
---

### Post by mabarian on 2010-10-16
Hi people, 

I'm sick as hell of having to write my user password every time I want to do anything. I DO know I'm doing something risky for the system, that's why I have Linux. Is there a way to avoid to rewrite the password again and again, like start with superuser permissions?

Thanks!

---

### Post by CharlesA on 2010-10-16
Read [this]("https://help.ubuntu.com/community/RootSudo") first.

---

### Post by Rocket2DMn on 2010-10-16
Although it puts your system at higher risk, I would suggest that you disable the need to enter a password for sudo commands.  While this isn't good to do, it is still better than enabling the root account, which violates Ubuntu's security policy.

For disabling the need to enter a password, you can actually use a more fine grained control over which commands you don't want to have to enter a password for (e.g. updating the system). This is preferable to simply allowing all sudo commands to be run without a password.

---

