---
title: "Startup applications will not run"
date: 2016-08-18
forum: Ubuntu Development Version
---

### Post by P-I H on 2016-08-18
I enabled proposed to get the Linux 4.6 kernel. This created some problems
- applications in Startup Applications will not run
- I'm not able to unlock my user in User Accounts
- I have to do unlock keyring to use Chrome

Mybe it's related to this information **[https://lists.ubuntu.com/archives/ubuntu-devel/2016-July/039465.html](https://lists.ubuntu.com/archives/ubuntu-devel/2016-July/039465.html)**

---

### Post by fthx on 2016-08-19
I do not experience any of the 1-2 issues, using Ub Gnome and 4.6 kernel.

---

### Post by mc4man on 2016-08-19
If you upgraded the group of systemd packages from proposed then it's probable you'd see those issues. If still happening you could - 
Do a fresh install & be more carefulabout proposed
or
Edit the file as mentioned, should work if you haven't mucked around too much - 
```
sudo nano /etc/X11/Xsession.d/00upstart
```
```
replacing the line

    if [ "${1#*.target}" != "$1" ]; then

with

    if false && [ "${1#*.target}" != "$1" ]; then
```

---

### Post by P-I H on 2016-08-19
Thanks a lot. Your proposal fixed the problem. I hadn't made a lot of changes and was able to start the applications I wanted, Dropox, Psensor and System Load Indicator manually. This system is only used to follow the development of Yakkety.

---

### Post by jbicha on 2016-08-19
mc4man, do you have a bug for that issue and your suggested fix?

---

### Post by mc4man on 2016-08-19
> **jbicha said:**
> mc4man, do you have a bug for that issue and your suggested fix?
It was on the mailing list - [https://lists.ubuntu.com/archives/ubuntu-devel/2016-July/039465.html](https://lists.ubuntu.com/archives/ubuntu-devel/2016-July/039465.html)
It is 'somewhat'  said the issues with polkit & gnome-keyring were fixed in 16.10 but doesn't seem that way with what's available via -proposed.
So not sure if it's a bug yet, though certainly would be when those packages leave -proposed if still occurring.

Edit: seems to be on the current image & broken... systemd 231-4

---

### Post by Smask on 2016-08-20
> **P-I H said:**
> I enabled proposed to get the Linux 4.6 kernel.

4.6 got removed from proposed

---

