---
title: "Can not install VMware in 8.10"
date: 2009-02-06
forum: Virtualisation
---

### Post by jamelb on 2009-02-06
None of the pre-built vsock modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vsock module for 
your system (you need to have a C compiler installed on your system)

---

### Post by Shazaam on 2009-02-07
Do you have build-essential and the header files for your kernel installed? Find/install build-essential in Synaptic and then run this in terminal...
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by jamelb on 2009-02-07
thank you so much bro

---

