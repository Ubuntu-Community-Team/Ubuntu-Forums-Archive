---
title: "Am I able to exceed what I have in physical storage when using Virtualization?"
date: 2016-10-17
forum: Virtualisation
---

### Post by Aphexlog on 2016-10-17
I am just wondering if when creating a virtual server environment if I am restraint by how much disk space that my system has in the same way that I am unable to exceed the amount of physical RAM?

For example: if my local system has 100gb am I able to virtualize 1TB?

Thanks!

---

### Post by QIII on 2016-10-17
Hello!

Alas.  You have only 100GB to assign to a virtual machine -- less the space necessary for your host OS.  No more.

This may be a bit disappointing, but consider my disappointment as a Mathematician:  I can do the Math to describe a tesseract, but try as I might I cannot jam one into three dimensions.

:)

---

### Post by howefield on 2016-10-18
Thread moved to the "*Virtualisation*" forum.

---

### Post by KillerKelvUK on 2016-10-18
Dumb confession prolly but I had to google "tesseract"...still made me giggle.

Not disagreeing with QIII's reply, committed/stored data can never exceed your physical storage capacity...but per chance were you thinking about something like Thin Provisioning?  It is possible to create virtual machines where the logical guest storage capacity is described as much greater than the physical host capacity...provided the sum committed/storage data of all thin provisioned guests never actually needs to consume the same or greater than the physical host capacity.

Example using qcow2 disk image, thin provision by default, the below shows me creating a 5Gb image but the commit data on disk directly after creating it is only 193K.

```

qemu-img create -f qcow2 test 5G
Formatting 'test', fmt=qcow2 size=5368709120 encryption=off cluster_size=65536 lazy_refcounts=off refcount_bits=16

ls -lh test
-rw-r--r-- 1 kelvin kelvin 193K Oct 18 14:39 test

```

---

