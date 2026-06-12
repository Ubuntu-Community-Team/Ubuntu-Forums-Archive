---
title: "bypass user passwd"
date: 2008-01-11
forum: Virtualisation
---

### Post by Angel_Linus on 2008-01-11
I installed on vmware  ubuntu 7.1. Start making the system I request the user name and password that I don't remember. How can users and reset passwords or bypass and access to the system to set new user and password? Can you help me?

Thanks

---

### Post by SeanHodges on 2008-01-11
Press escape when Grub appears during boot (it should instruct you to do this), then select the option with "recovery mode" in it.

You should end up at a command prompt as root, from here you can change the password using:

```
passwd username
```

---

### Post by Angel_Linus on 2008-01-11
> **SeanHodges said:**
> Press escape when Grub appears during boot (it should instruct you to do this), then select the option with "recovery mode" in it.

You should end up at a command prompt as root, from here you can change the password using:

```
passwd username
```
Sean tks, now it's ok.

tks 100000

Angel

---

### Post by SeanHodges on 2008-01-11
Excellent, don't forget to mark this thread as solved (Thread Tools->Mark as solved), so others in the same position can find this solution easily.

Cheers,

Sean

---

