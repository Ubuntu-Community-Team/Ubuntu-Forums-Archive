---
title: "Streamlined kernel/initrd.gz for Netboot clients"
date: 2009-04-16
forum: Server Platforms
---

### Post by xris_xcess on 2009-04-16
Hi:

I have a server set up for pxe-netbooting and serveral clients. The system works well and the administration couldn't be simpler.

Lately I have been reading up on enhancing the performance and speed of my machines.

[http://wiki.debian.org/BootProcessSpeedup?highlight=%28readahead%29#Analyzingthebootprocess](http://wiki.debian.org/BootProcessSpeedup?highlight=%28readahead%29#Analyzingthebootprocess)
[https://www.debian-administration.org/articles/620](https://www.debian-administration.org/articles/620)

From building a custom kernel, custom initrd.gz with extra modules built-in, tcp/ip tweaking, NFS tweaking, readahead, prelink, preload, to reordering the scripts rcS.d

I would like some suggestions/pointers in maybe building a minimal kernel with all the necesary modules for clients (fortunatelly It's a lab with rather similar harware across the board and no special/awkward peripherals).

I "Booting Debian in 14 Seconds" ( [https://www.debian-administration.org/articles/620](https://www.debian-administration.org/articles/620) ) it outlines the building of a kernel will all necessary (for you HW) modules built-in (network, disks, fs, nfs, usb, etc) and getting rid of the initrd.gz altogether.

Would this get me extra performace/boot speed/responsiveness out of netbooting clients? Or will it just be a tedious experiment?

I was also thinking about a load into ram netbooting. A custom live image but with storage on the server.

Has anyone had any experience with this?

Thanks.

---

### Post by xris_xcess on 2009-04-22
Err... Can someone at least tell me if this all sounds like a good/worth-while idea?

---

