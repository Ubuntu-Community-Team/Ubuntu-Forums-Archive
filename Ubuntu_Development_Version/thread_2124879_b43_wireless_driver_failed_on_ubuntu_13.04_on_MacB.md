---
title: "b43 wireless driver failed on ubuntu 13.04 on MacBook Pro 9.2"
date: 2013-03-12
forum: Ubuntu Development Version
---

### Post by Crossle Song on 2013-03-12
1.  Install wireless driver  reference [https://help.ubuntu.com/community/MacBookPro9-2/Quantal#Wireless](https://help.ubuntu.com/community/MacBookPro9-2/Quantal#Wireless)

    $ sudo modprobe b43
    ERROR: could not insert 'b43': Unknown symbol in module, or unknown parameter (see dmesg)
    $dmesg
     [ 1757.465422] bcma: Unknown symbol compat_dependency_symbol (err 0)     [ 2811.568591] bcma: Unknown symbol compat_dependency_symbol (err 0)
     [ 3492.933886] bcma: Unknown symbol compat_dependency_symbol (err 0)

2. linux-kernel 3.8.0-11-generic ubuntu 13.04

3. How i to resolve?

---

### Post by dino99 on 2013-03-12
you should install the vanilla 3.9-rc2 kernel

---

### Post by Crossle Song on 2013-03-12
Today I updated 3.8.0-12-generic connect ok ,but can't on internet.

---

### Post by cariboo on 2013-03-12
It sounds like you may have a dns problem, can you ping Google?

```
ping www.google.com
```

if not can you ping:

```
ping 74.125.141.106
```

---

### Post by Crossle Song on 2013-03-13
It'ok from update 3.8.0-12-generic.
waiting for ubuntu 13.04 release....

e.g. I  run  sudo apt-get install linux-firmware linux-firmware-nonfree. have no idea about it ?

---

