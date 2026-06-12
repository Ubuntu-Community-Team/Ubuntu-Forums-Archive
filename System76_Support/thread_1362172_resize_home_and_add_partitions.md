---
title: "resize /home and add partitions"
date: 2009-12-22
forum: System76 Support
---

### Post by k3c176 on 2009-12-22
I have a new system76 laptop. Very nice, but before I load all my various partitions of data from the system being replaced, How do I resize /home and add new partitions? /home is way too large (most of my hda drive) and I would like a few smaller partitions for various applications.
 
I have loaded gparted and that runs well, but /home is "in use" and can't be resized. Any ideas?
 
Thanks,
k3c1

---

### Post by marshmallow1304 on 2009-12-22
You need to run GParted from a LiveCD, so the hard drive is not in use (running the system) while you're trying to partition it.

---

### Post by thomasaaron on 2009-12-23
Also, before Gparted from the live CD will allow you to modify the partitions, you will have to right-click the swap partition and select "swapoff" from the submenu.

---

### Post by k3c176 on 2009-12-23
Thanks,
 
I will do that (it may take me a while to get to it). Meanwhile I just won't load any of my old partitions except the /home one, and that will be no problem.
 
I have the [**Pangolin Performance**]("http://system76.com/product_info.php?cPath=28&products_id=96") running Ubuntu 9.10 (Karmic Koala) 64 Bit Linux.  It's a great laptop and software package. I really like the numeric keypad.
 
k3c176

---

### Post by k3c176 on 2009-12-24
Well, not quite so easy. I have a model panp6. Does anyone know how to get it to boot from cd?

thanks,
k3c176

---

### Post by k3c176 on 2009-12-24
I figured out the boot and partitioned the disk. Thanks so much for the help. Everything running fine.

Enjoy the holidays

k3c176

---

