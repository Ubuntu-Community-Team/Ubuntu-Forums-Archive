---
title: "Elementary OS, Wireless not working. Lenevo T60."
date: 2015-03-05
forum: Ubuntu/Debian BASED
---

### Post by Magnezone150 on 2015-03-05
Hi,

On my Lenevo T60 Laptop I recently installed Elementary OS Luna 0.2.1 (32 Bit) built on Ubuntu 12.04.
My T60 used to run Windows 7 and it´s internal wireless was working.
Elementary OS support wasn´t too helpful or up to date. anyone here have an idea or can help me figure out what´s wrong with it.
Any Help/Reminders would be a great help.

Thanks,

AJN

---

### Post by Rob Sayer on 2015-03-07
I wouldn't expect much specific help here, but you will need to know what your wireless card actually is.  The make/model is useless.

Paste into terminal:

```
sudo lshw -C network
```

and you'll find the actual wifi adapter and driver used.

With some adapters (eg. broadcom) there may actually be more than 1 adapter with the same model name.  You'll also therefore need the PCI ID if the adapter too.  Use this in term:

```
lspci -nn -d 14e4:
```

and then search "ubuntu 12.04 <whatever>".

This is how I've done pretty much all config stuff in linux mint, whose support isn't nearly as good as ubuntu's but miles ahead elemtary OS.  it's very handy with ubuntu based OSes but you have to learn what to look for.

---

