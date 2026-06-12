---
title: "dazuko apparmor incompatibility."
date: 2008-07-24
forum: Security
---

### Post by melrokz on 2008-07-24
Hi! I'm Melvin from India.
I installed AVG for linux workstation recently and compiled dazuko kernel module for real time file scanning in ubuntu 7.10.As root, i gave this code.
```

./configure 
make
make test
insmod dazuko.ko
make install
```
The error was that the module could not be inserted.
Then, i gave this code:
```

sudo rmmod apparmor
sudo insmod dazuko.ko
```
and the dazuko module works, but the apparmor module can't be reloaded.
How important is apparmor, what does it do and how to get it back working with dazuko?

---

