---
title: "Just received my aquaris tablet with ubuntu, and would like to connect to NAS"
date: 2016-04-20
forum: Ubuntu Phone and Tablet
---

### Post by eaz2 on 2016-04-20
Very happy with the ubuntu tablet, it is fairly quick and smooth!

Not yet succeeded in connecting to the NAS. 
On my desktop/laptop I would create mnt\mounts and put cifs lines in fstab for auto mounting.

As the phablet seems to be read only, the above method does not work.

Any idea's? how to R/W the tablet? will it work?

---

### Post by mikeyphi2 on 2016-04-21
I installed File Manager, it enabled me to access all the devices connected to my Router.

---

### Post by John_Harris on 2016-04-21
I've connected a bluetooth keyboard which makes a big difference. I might look in a drawer for a bluetooth mouse soon. I failed to mount my SD card so far but there's surely a way to do it. I think it/s /dev/mmcblk1 and fdisk -l shows it.

Some bits of the device file tree are rw and sudo gives permissions without a password. I used wget to bring source into ~/Downloads but hit a snag with "no acceptable C compiler found" so that's what I need next. I can't see any compiler in the Ubuntu Store. I can't yet find a developer discussion to get me started.

The usual /usr/bin utilities are all there, tar xz awk sed wc uniq sort and such.

---

### Post by eaz2 on 2016-04-21
I also installed file manager, but it does not allow for entering a userid/pw for the NAS.
Any other hints?

---

### Post by eaz2 on 2016-04-21
for regular setup I need /mnt and /etc in RW ..

---

### Post by eaz2 on 2016-04-26
File manager will connect to a windows computer: it asks for a username/password, this does  not happen when I want to connect to my NAS..
Anybody?

---

### Post by eaz2 on 2016-06-22
From answers.launchpad.net I received a good answer:

by enabling guest account on the synology, SMB can connect. 
Next the popup for userid/pw appear!

I just do not like the guest account, but I have taken away all access rights for guest.
At least my docs are available now!

---

