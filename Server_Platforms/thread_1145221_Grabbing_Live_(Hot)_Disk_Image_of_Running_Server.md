---
title: "Grabbing Live (Hot) Disk Image of Running Server"
date: 2009-05-01
forum: Server Platforms
---

### Post by MightyMartian on 2009-05-01
I'm consolidating four of my servers under one hood using KVM, and I need to start imaging them so that I can transfer them over to my new, big and fancy server.  The Windows machines aren't too much of a problem, with the VMWare converter, which allows me to make a VMDK image of the servers while they're running.  I was wondering if there's any way to do that with an Ubuntu server.  I know I might lose a few minutes of logs, but it would be nice to create a live image, transfer that to the virtualization host, with a minimum of down time.

---

### Post by i.r.id10t on 2009-05-01
Create new empty virtual disk whatever size you want/need, and rsync the data over.

---

