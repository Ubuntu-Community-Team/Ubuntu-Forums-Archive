---
title: "GNU C++ compiler - which packages?"
date: 2008-06-06
forum: Repositories &amp; Backports
---

### Post by Silvestro Fantacci on 2008-06-06
Hi,

My first post here :)

I am new to Linux/Ubuntu and I have just managed to correctly install the Hardy Heron desktop version.

I am now trying to install the GNU C++ compiler and the Synaptic Package Manager shows 3 packages:

g++ (version 4:4.2.3-1ubuntu5)
g++-4.2 (version 4.2.3-2ubuntu7)
g++-4.2-multilib (version 4.2.3-2ubuntu7)

Which packages should I have installed? In particular, what's the difference between the g++ and g++-4.2 packages?

Thanks in advance,
Silvestro

---

### Post by amingv on 2008-06-06
They're g++, just different versions (or including other libraries).

Don't install it like that, however, use:
```
sudo apt-get install build-essential
```

---

