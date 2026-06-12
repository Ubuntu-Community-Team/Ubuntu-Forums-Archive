---
title: "apt-get upgrade security updates only"
date: 2010-04-21
forum: Security
---

### Post by dlublink on 2010-04-21
Hey,

When doing updates on my Ubuntu 8.04 server, how can I :

1. See change logs or release notes for upgraded packages ?
2. Prevent kernel from being upgraded ?

Is this command the correct way to install security updates only ?

aptitude safe-upgrade --target-release hardy-security -o Aptitude::Delete-Unused=false

The result is the same as apt-get upgrade. Is it possible



Thanks,

David

---

### Post by cariboo on 2010-04-21
Why would you not want to upgrade the kernel? In Hardy, the only reason you get a kernel update is for security reasons.

---

### Post by borsood on 2010-04-23
I have been using this lately. It is correct most of the time, but sometimes also brings some other updates.
Kernel updates are almost allways security updates.
```
sudo aptitude update && sudo aptitude install '?and(~U,~Asecurity)'
```

---

### Post by dlublink on 2010-05-10
The trouble with a kernel update, is one of my machines has a Sangoma card in it and I have to compile the drivers against the kernel, so I think an update would break the drivers.

---

### Post by CharlesA on 2010-05-10
> **dlublink said:**
> The trouble with a kernel update, is one of my machines has a Sangoma card in it and I have to compile the drivers against the kernel, so I think an update would break the drivers.

I have to recompile the drivers for my RAID controller every time there is a kernel update. It isn't a game-breaking problem.

Just compile the drivers and add them to the kernel.

Download the source, make && make install. Done.

---

