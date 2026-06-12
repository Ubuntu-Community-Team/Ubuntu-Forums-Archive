---
title: "VMWare Server Host Recommendations"
date: 2008-03-06
forum: Virtualisation
---

### Post by BigDogMU on 2008-03-06
I am looking at building an Ubuntu VMWare server using a pretty beefy desktop, with 16GB of RAM and 2x Quad Core processors. So my questions are what are the recommendations 64bit or 32bit Ubuntu Server? Secondly does anyone know if VMWare server 2 and Ubuntu 7.10 utilize this system, meaning all the processor cores and RAM?

---

### Post by fjgaude on 2008-03-06
I run 64-bit Ubuntu host with whatever the VMware Server is from their site: vmware.com. It works great!

But, and there always seems to be one of these "buts", you can only use one core effectively. You can go with more then the issue becomes one of waiting for all to be free before vmware can use one. So only one core runs fine, especially if you have a fast box, like I do. I understand the next free release will have this fixed, but it's not a issue with me. Notice my signature. <smile>

Disk I/O becomes the bottleneck with modern computers with fast CPU and memory. And raid with many disks helps there.

I'm a graphic designer and my setup works for me, using raid5 to speed disk I/O.

What will you use your box for?

---

### Post by BigDogMU on 2008-03-06
fjgaude, thanks for the reply.  What version of VMWare server are you using 1.x or 2 beta?  Currently I have 2 older computers each with a 3Ghz P4 and 3GB RAM running Ubuntu 7.04 and VMWare Server 2 to kind of pilot this setup (older computers pulled from the closet).  I am looking at taking this setup to "prime time" for a development environment at our office.  So that is why I am looking at some new hardware.  By the way very good point about the disk IO and using raid 5, I had not thought about that.

---

### Post by fjgaude on 2008-03-06
I'm using version 1.0.4 of the server, the one from vmware.com's site.

---

