---
title: "Password Authorization Very Annoying"
date: 2010-01-14
forum: Security
---

### Post by LysolPionex on 2010-01-14
One of the things I hated about Windows Vista was the annoying implementation of User Account Control, which required me to authorize every little thing that happened.  I've been using Ubuntu for about a year now and I cannot take it anymore; it's the exact same type of annoyance!  Change a setting: enter your password, sudo: enter your password etc.

Is there any way I can lower the security level on everything?  Honestly, I care nothing about the security, if something takes over a vital part, I'll just wipe and reinstall.  But I cannot stand this constant need to authorize every little thing.

Also, I'd love it if there were a way to do the same thing with permissions.

Any help is loved and appreciated.

---

### Post by running_rabbit07 on 2010-01-14
Without having to enter passwords, your system will be insecure. That said, you need to find a HowTo on setting up a Keyring to do your bidding.

---

### Post by nerdy_kid on 2010-01-14
the authorizations section allows you to customize this to an extent....but no password = horribly insecure system.

---

### Post by Rob_H on 2010-01-14
The "easiest" way to never be bothered for a password is to log into your desktop session as the root user. Some distros support this. Ubuntu does not.

Without going to that extreme, there are some less drastic steps you can take. For example, if there are certain programs you frequently want to run as root, you can edit your **/etc/sudoers** file to permit you to do this without a password by using the NOPASSWD tag spec. See the man page for sudoers for information and examples.

And for certain desktop actions that require privilege escalation, you can set whether or not you're challenged for a password on a case-by-case basis. On KDE, you do this by going to System Settings > Advanced > PolicyKit Authorization. I am not sure what the equivalent is for GNOME.

---

### Post by running_rabbit07 on 2010-01-14
Check out this link to see why you may or may not be getting the results you want from this thread. [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by cariboo on 2010-01-14
Have a look [here]("https://help.ubuntu.com/community/RootSudo"), it will help you accomplish what you want. Be sure to read the whole page, and not just concentrate on the parts that you think will help you.

---

### Post by slushee on 2010-01-15
> **cariboo907 said:**
> Have a look [here]("https://help.ubuntu.com/community/RootSudo"), it will help you accomplish what you want. Be sure to read the whole page, and not just concentrate on the parts that you think will help you.

after reading that link, it seems like removing the password is a *really bad* idea. there were a ton of warnings and disclaimers on that page. my opinion--which is worth 5 beans, less than two cents--is that you just deal with the password prompts; you'll be saving yourself a lot of hassle in the future by occasionally typing in a word that's probably already become second nature to your fingers.

---

### Post by running_rabbit07 on 2010-01-15
> **slushee said:**
> after reading that link, it seems like removing the password is a *really bad* idea. there were a ton of warnings and disclaimers on that page. my opinion--which is worth 5 beans, less than two cents--is that you just deal with the password prompts; you'll be saving yourself a lot of hassle in the future by occasionally typing in a word that's probably already become second nature to your fingers.

Very true.

---

### Post by cariboo on 2010-01-15
I can create a link to that page, for every one of these types of threads, but the big problem is, that a lot of former Windows users that change to Ubuntu because of UAC, never read the whole page, and rarely pay attention to the warnings. Maybe I should put a disclaimer in every post:


[COLOR="Red"][SIZE="5"]If you follow the instruction on the linked page **you** could make your system unusable[/SIZE][/COLOR]  :)

---

