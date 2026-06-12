---
title: "How to change root's login name"
date: 2008-08-13
forum: Security
---

### Post by gkaragoulis on 2008-08-13
Earlier today I got the urge to change root's login name on one of my old Ubuntu boxes.  I did "sudo usermod -l stan root", to change root's name to 'stan' (you know, it's more personal that way) But then when I try to 'sudo' anything (in a DIFFERENT shell...of course I leave my root shell open and keep a backup of the important files when I do stuff like this!), sudo complains that there's no entry for root in the passwd file.  Is there a way to change sudo to look for stan's entry instead of root?

Perhaps my question could be widened: Is there a way to change root's name and not have it affect my system very much?

---

### Post by solar george on 2008-08-13
You can't change the login name for root and shouldn't try.

You certainly shouldn't be running as root often  enough to feel the need to personalize it

---

### Post by conundrumx on 2008-08-13
> **solar george said:**
> You can't change the login name for root and shouldn't try.

You certainly shouldn't be running as root often  enough to feel the need to personalize it

This.  Running as root isn't like being an Administrator on Windows, it's much, much more dangerous.  Being in the sudoers file is plenty power for 9/10 situations a home user will run into.

---

### Post by dperfors on 2008-08-14
> **solar george said:**
> You can't change the login name for root and shouldn't try.The reason for this is that a lot of important programs on your system (like sudo) need to have a root account, this is hardcoded since this doesn't change that much.
So when you change the name a lot of programs simply don't work anymore and you probably get problems when rebooting the system...

---

### Post by hyper_ch on 2008-08-14
you could however create an alias. Add a new user and then change its UID to match the root one.

---

### Post by gkaragoulis on 2008-08-14
> **hyper_ch said:**
> you could however create an alias. Add a new user and then change its UID to match the root one.

That's a great idea, I think I'll try that.

BTW, I only do this because at work I administer at least 10 different linux Virtual computers, and I can make and break them without consequence because we have such redundant backups of them.  I literally created a linux computer just so I could change root's name to Satan.

(...don't tell my boss...)

---

### Post by todb on 2008-08-14
> 
Add a new user and then change its UID to match the root one.


This is the typical way to accomplish what you want. It will also get you jeered by security dorks when they catch you running as root for doing normal non-root things (personal experience).

---

