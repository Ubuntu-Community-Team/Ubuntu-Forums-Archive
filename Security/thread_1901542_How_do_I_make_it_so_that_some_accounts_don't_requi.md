---
title: "How do I make it so that some accounts don't require a password."
date: 2011-12-28
forum: Security
---

### Post by ferulebezel on 2011-12-28
For reasons too boring to explain here I have several users who I'd like to set their accounts no not require passwords to log in.  In earlier versions of ubuntu it was trivial, just a checkbox.  Now that checkbox is missing.

How do I do it?

---

### Post by cariboo on 2011-12-29
If you are using Oneiric (11.10), go to System Settings->User Accounts, to set auto login.

---

### Post by sisco311 on 2011-12-29
> **ferulebezel said:**
> For reasons too boring to explain here I have several users who I'd like to set their accounts no not require passwords to log in.  In earlier versions of ubuntu it was trivial, just a checkbox.  Now that checkbox is missing.

How do I do it?

If memory serves, the option is still there in users-admin (from gnome-system-tools) . But if you can't do it via users-admin, then all you have to do is to add the user(s) to the **nopasswdlogin** group:

```
sudo gpasswd -a **USERNAME** nopasswdlogin
``` 

Where **USERNAME** is the login name of the user.

---

### Post by HermanAB on 2011-12-29
Hmm, if you don't want to bother people with logging in, how about giving them a USB memory stick as a login key token?

[http://ubuntuforums.org/showthread.php?t=17571](http://ubuntuforums.org/showthread.php?t=17571)

---

### Post by ferulebezel on 2012-01-01
> **cariboo907 said:**
> If you are using Oneiric (11.10), go to System Settings->User Accounts, to set auto login.

That's not what I'm asking.  I don't want to log in to a certain account by default.  I want some accounts to nor require a password.

---

### Post by ferulebezel on 2012-01-01
> **sisco311 said:**
> If memory serves, the option is still there in users-admin (from gnome-system-tools)

Thanks, that worked.

---

### Post by fdrake on 2012-01-01
to apply sisco311's suggestion of the command "sudo gpasswd -a USERNAME nopasswdlogin" you need to add this line to your pam conf (/etc/pam.conf) "gdm auth  sufficient  pam_succeed_if.so  USERNAME ingroup nopasswdlogin"

also you can bypass the password by deleting the second entry (password hash) of the users filed.

or in a more elegant way with aysiu's method  :[http://ubuntuforums.org/showthread.php?t=513820](http://ubuntuforums.org/showthread.php?t=513820)

---

