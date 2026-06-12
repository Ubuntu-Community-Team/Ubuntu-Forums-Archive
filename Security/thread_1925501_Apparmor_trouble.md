---
title: "Apparmor trouble"
date: 2012-02-14
forum: Security
---

### Post by 0011235813 on 2012-02-14
Hello forum, I have tried to enforce profiles in apparmor. Apparmor is installed, and the command
```
apparmor_status
```
works fine. However, when I try to actually enforce some of the profiles with:
```
aa-enforce <profile name>
```
I get the following error:
```
sudo: aa-enforce: command not found
```
Any ideas what might be wrong?

---

### Post by Porcini M. on 2012-02-14
You might need to install an "apparmor-utils" package or something - I vaguely recall there being a package of extra utilities related to apparmor.

---

### Post by Dangertux on 2012-02-14
Yes you news apparmor-utils

```

sudo apt-get install apparmor-utils

```

---

### Post by 0011235813 on 2012-02-15
> **Porcini M. said:**
> You might need to install an "apparmor-utils" package or something - I vaguely recall there being a package of extra utilities related to apparmor.

> **Dangertux said:**
> Yes you news apparmor-utils

```

sudo apt-get install apparmor-utils

```

I have installed *apparmor-utils* it works now, thanks. One question though; why didn't this come pre-installed?

---

