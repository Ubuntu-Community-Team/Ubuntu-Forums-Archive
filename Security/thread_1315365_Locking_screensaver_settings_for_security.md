---
title: "Locking screensaver settings for security"
date: 2009-11-05
forum: Security
---

### Post by Spin84 on 2009-11-05
Hi

We have started using Ubuntu on several company laptops. I have set the screensaver to come on after 5 minutes and that it requires a password to unlock it. However employees often turn the password protection off which isn't acceptable as it is a company laptop with company data.

Is there an easy way to stop employees from changing the screensaver settings? We are now using Ubuntu 9.10.

Regards
Spin

---

### Post by scaine on 2009-11-06
Never used it, but there's a tool called "Pessulus" that sounds like it might fit your criteria :
[http://www.linux.com/archive/feature/62060](http://www.linux.com/archive/feature/62060)

Good luck.

---

### Post by Jive Turkey on 2009-11-06
there is a command to make a file immutable so that it cant even be changed with sudo.  The command is chattr.

So... find the config file where the protect screensaver option is stored

then do sudo chattr +i file.conf

they will not have permission to change the setting even with sudo or as root, unless they run sudo chattr -i file.conf

---

### Post by Agent ME on 2009-11-06
You should be able to force that setting with gconf-editor.

---

