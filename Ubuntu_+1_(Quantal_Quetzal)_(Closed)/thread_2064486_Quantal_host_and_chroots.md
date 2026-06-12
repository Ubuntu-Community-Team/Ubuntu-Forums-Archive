---
title: "Quantal host and chroots"
date: 2012-09-29
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by nerdopolis on 2012-09-29
Hi. It seems since I upgraded to Quantal, my chroot guests can no longer resolve domain names. 

I tried running dhclient inside the chroots, and many of my searches said something about /etc/resolv.conf, which seems fine.

I doubt it's the chroot guests, and I think it has something to do with the host.

Anyone have any idea what would actually cause this?

---

### Post by nerdopolis on 2012-09-30
Any ideas? I even tried a chroot off a quantal live cd, and I can't resolve domain names with a chroot guest. It doesn't seem to be just my system

---

### Post by nerdopolis on 2012-09-30
Never mind. it WAS /etc/resolv.conf . Kind of weird that this is the first time needing this after years of using chroot to build live cds...

---

### Post by kansasnoob on 2012-10-01
I don't quite understand this. I've been parsing my chroot script, the individual commands and results are shown here:

```
lance@lance-desktop:~$ sudo mount /dev/sda15 /mnt
[sudo] password for lance: 
lance@lance-desktop:~$ sudo mount --bind /dev /mnt/dev
lance@lance-desktop:~$ sudo mount --bind /proc /mnt/proc
lance@lance-desktop:~$ sudo mount --bind /sys /mnt/sys
lance@lance-desktop:~$ sudo mount --bind /dev/pts /mnt/dev/pts
lance@lance-desktop:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
cp: `/etc/resolv.conf' and `/mnt/etc/resolv.conf' are the same file

```

What am I not getting :confused:

---

### Post by nerdopolis on 2012-10-02
> **kansasnoob said:**
> I don't quite understand this. I've been parsing my chroot script, the individual commands and results are shown here:

```
lance@lance-desktop:~$ sudo mount /dev/sda15 /mnt
[sudo] password for lance: 
lance@lance-desktop:~$ sudo mount --bind /dev /mnt/dev
lance@lance-desktop:~$ sudo mount --bind /proc /mnt/proc
lance@lance-desktop:~$ sudo mount --bind /sys /mnt/sys
lance@lance-desktop:~$ sudo mount --bind /dev/pts /mnt/dev/pts
lance@lance-desktop:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
cp: `/etc/resolv.conf' and `/mnt/etc/resolv.conf' are the same file

```What am I not getting :confused:

THAT'S weird! Hmm... What's the results of 
```

df /etc
ls -ld /etc

df /mnt/etc
ls -ld /mnt/etc

```

---

