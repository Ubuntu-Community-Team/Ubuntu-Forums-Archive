---
title: "nautilus fails to open Home?"
date: 2011-12-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by scradock on 2011-12-19
I have just installed Precise from the alpha1, and updated/upgraded to date. The "Home" launcher does not open the folder as expected, soi I tried entering "nautilus" in a terminal. The response was:

```
sc@scP4:~$ nautilus
Could not register the application: Method `DescribeAll' returned type `(a(savbav))', but expected `(a{s(bgav)})'
sc@scP4:~$
``` 

Anyone know what is going on? I have tried 

"sudo apt-get install --reinstall nautilus"

but it made no difference.

---

### Post by mc4man on 2011-12-19
See here - read comment 5
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/904239](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/904239)

---

### Post by scradock on 2011-12-19
> **mc4man said:**
> See here - read comment 5
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/904239](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/904239)
Thanks

---

