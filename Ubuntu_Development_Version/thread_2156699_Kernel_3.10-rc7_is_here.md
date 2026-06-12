---
title: "Kernel 3.10-rc7 is here"
date: 2013-06-22
forum: Ubuntu Development Version
---

### Post by paul_in_london on 2013-06-22
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-rc7-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-rc7-saucy/)

```
tu-64:~$ uname -a
Linux lubuntu-64 3.10.0-031000rc7-generic #201306221735 SMP Sat Jun 22 21:35:55 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
paul@lubuntu-64:~$
```

---

### Post by VinDSL on 2013-06-22
Thanks, Paul!  Working great!  ;)

---

### Post by QDR06VV9 on 2013-06-22
All systems go! With nvidia-319

---

### Post by jfernyhough on 2013-06-22
I wonder how many hamsters were verbally abused for this rc... :D

---

### Post by QDR06VV9 on 2013-06-22
> **jfernyhough said:**
> I wonder how many hamsters were verbally abused for this rc... :D

SSSHHH!!
I think we have some PETA members here..LOL

---

### Post by IanW on 2013-06-24
rc7 + nividia-319 working fine for me too! :D

---

### Post by JMB74 on 2013-06-24
The first 3.10 based (RC7) kernel for the main ubuntu repositories is now building.

[https://launchpad.net/ubuntu/saucy/+source/linux/3.10.0-0.6](https://launchpad.net/ubuntu/saucy/+source/linux/3.10.0-0.6)

---

### Post by VinDSL on 2013-06-24
> **JMB74 said:**
> The first 3.10 based (RC7) kernel for the main ubuntu repositories is now building.

[https://launchpad.net/ubuntu/saucy/+source/linux/3.10.0-0.6](https://launchpad.net/ubuntu/saucy/+source/linux/3.10.0-0.6)

Be interested to see how it works, for others.

I dunno...

I've haven't analyzed the situation, but it *seems* like mainline kernels always work the best in my rig.

---

### Post by jerrylamos on 2013-06-24
Today's apt-get update, dist-upgrade brought in rc7 on amd64 netbook and notebook without incident.  What's it supposed to do?

---

### Post by zika on 2013-06-25
> **jerrylamos said:**
> Today's apt-get update, dist-upgrade brought in rc7 on amd64 netbook and notebook without incident.  What's it supposed to do?Is that 3.9 or 3.10? Proposed?
At my place that was 3.9...

---

### Post by IanW on 2013-06-25
According to [https://launchpad.net/ubuntu/+source/linux]("https://launchpad.net/ubuntu/+source/linux"):-

Main is at 3.9.0-7.15 (based on 3.9.7)
Proposed is at 3.10.0-0.7 (based on 3.10-rc7)

---

### Post by zika on 2013-06-25
> **IanW said:**
> According to [https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux):-

Main is at 3.9.0-7.15 (based on 3.9.7)
Proposed is at 3.10.0-0.7 (based on 3.10-rc7)
My point exactly...

---

### Post by zika on 2013-06-27
> **zika said:**
> My point exactly...
You made me do it...
Now my install is 3.9-free...
All kernels are 3.10... ;)
```
Found linux image: /boot/vmlinuz-3.10.0-031000rc7-generic
Found initrd image: /boot/initrd.img-3.10.0-031000rc7-generic
Found linux image: /boot/vmlinuz-3.10.0-999-generic
Found initrd image: /boot/initrd.img-3.10.0-999-generic
Found linux image: /boot/vmlinuz-3.10.0-996-generic
Found initrd image: /boot/initrd.img-3.10.0-996-generic
Found linux image: /boot/vmlinuz-3.10.0-0-generic
Found initrd image: /boot/initrd.img-3.10.0-0-generic
Found memtest86+ image: /boot/memtest86+.bin
```

---

