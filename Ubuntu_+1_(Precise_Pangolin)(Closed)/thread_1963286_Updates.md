---
title: "Updates"
date: 2012-04-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Johnny3 on 2012-04-22
How come sometimes went I get updates 12.04 asks for my password and sometimes not?
Thanks and God Bless Johnny3 65+++

---

### Post by r-senior on 2012-04-22
Sudo remembers your password for 15 minutes and won't prompt you if you issue another sudo command within that time.

---

### Post by MG&amp;TL on 2012-04-22
*sudo* remembers you for a while-to see this in action, run the following command twice-it will ask for a password the first time, then the second time (and subsequent times, up to a time limit) it will not:

```
sudo echo "blahblahblah"
```

[SIZE=1](echo doesn't actually do anything; chosen for its lack of damage-causing prospects)[/SIZE]

---

### Post by Johnny3 on 2012-04-22
> **r-senior said:**
> Sudo remembers your password for 15 minutes and won't prompt you if you issue another sudo command within that time.

I do update first thing in the morning and haven't used the sudo command or gksu nautilus command ether.
Thanks and God Bless Johnny3 65+++

---

### Post by cariboo on 2012-04-22
I don't use Update Manager, but apparently it won't ask for a password to update already installed packages. It will ask for a password if new/not installed packages need to be installed.

---

