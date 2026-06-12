---
title: "How do I add packages to source list?"
date: 2008-12-11
forum: Server Platforms
---

### Post by hardysummer on 2008-12-11
I got the Server version installed, but would like to install some packages from other Ubuntu distributions.  I have added the distribution with "sudo apt-cdrom add" and it shows up in my /etc/apt/source.list.

However, when I try to install some packages that are in the CD, apt is not locating it.

---

### Post by albinootje on 2008-12-11
Perhaps you forgot to do : sudo apt-get update

---

### Post by hardysummer on 2008-12-12
I did that and it still tells me that there is "no such package but referred to by another" and "no installation candidate" or something like that.

---

### Post by albinootje on 2008-12-12
Can you show us the output of :
sudo apt-get install mc

The error-message you've just posted look like error-messages about packages that don't exist on the cdrom.

---

### Post by hardysummer on 2008-12-12
```
Reading package lists...
Building dependency tree...
Reading state information...
E: Couldn't find package mc
```

---

