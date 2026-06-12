---
title: "extend logical volume using KVPM to second hard drive"
date: 2014-07-02
forum: Server Platforms
---

### Post by matt_fussell2 on 2014-07-02
I've successfully extended a logical volume on Ubuntu server 14.04 from the initial setup volume (1 TB hard drive) to include the other SSD in the server (120 GB). KVPM says that the logical volume includes both physical volumes, but that the new SSD physical volume is inactive.

How do I activate it?

---

### Post by nerdtron on 2014-07-02
Please provide outputs of the following from the terminal:
sudo pvscan
sudo vgscan
sudo lvscan

---

### Post by matt_fussell2 on 2014-07-07
> **nerdtron said:**
> Please provide outputs of the following from the terminal:
sudo pvscan
sudo vgscan
sudo lvscan

I was out of the office today - I'll get these posted when I get back there tomorrow morning.

---

### Post by matt_fussell2 on 2014-07-08
lvscan output:

```
  ACTIVE            '/dev/vhost1-vg/root' [899.27 GiB] inherit
  ACTIVE            '/dev/vhost1-vg/swap_1' [31.96 GiB] inherit
```

vgscan output:

```
  Reading all physical volumes.  This may take a while...
  Found volume group "vhost1-vg" using metadata type lvm2
```

pvscan output:

```
  PV /dev/sda5   VG vhost1-vg   lvm2 [931.27 GiB / 44.00 MiB free]
  PV /dev/sdb1   VG vhost1-vg   lvm2 [111.79 GiB / 111.79 GiB free]
  Total: 2 [1.02 TiB] / in use: 2 [1.02 TiB] / in no VG: 0 [0   ]
```

---

### Post by matt_fussell2 on 2014-07-10
Any thoughts?

---

### Post by nerdtron on 2014-07-10
Sorry, no. I don't see anything wrong. Just bump this thread and hope others can respond.

---

### Post by matt_fussell2 on 2014-07-14
> **nerdtron said:**
> Sorry, no. I don't see anything wrong. Just bump this thread and hope others can respond.

Thanks for your effort - hopefully having that info up will speed a solution from others.

---

