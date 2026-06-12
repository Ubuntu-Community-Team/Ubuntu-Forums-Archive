---
title: "Wired networking suddenly stops working Ubuntu 15.10 beta"
date: 2015-09-03
forum: Ubuntu Development Version
---

### Post by cigtoxdoc on 2015-09-03
Has anyone had problems with wired networking suddenly stop working?  Have three PC hard-wired to the router provided Cox Cable.  One pc is a Dell Vostro 3500 laptop.  Wired networking works correctly on this PC.  The other two PCs are home-build desktop PCs based on Intel i7-4770K processors and MSI CSM-B85M-P32 motherboards each with 8 GB RAM.  Wired networking will randomly stop working on both of these, but not at the same time.  When websites (Firefox) or evolution stop working "Connection Information" shows connections to be working.  However everything using the Internet stops, including streaming Internet radio using VLC player.  Before having Ubuntu 15.10 beta as the OS, both PCs had the earlier Ubuntu Gnome 15.10.  Problem did not occur when the systems had the Ubuntu Gnome OS or with Ubuntu 15.04 before that.  Since the laptop does not have that problem with Ubuntu 15.10 beta, I am beginning to suspect that the problem is an interactions between the Ubuntu 15.10 beta and the Intel chipsets and Intel processor.  I realize that I am using beta software.  However, it is only way to get the latest version of evolution e-mail and calendering (very important for my business).  If anyone needs more information, please let me what diagnostics I should run.

John

---

### Post by Rustan on 2015-09-03
if installed NetworkManager 1.0.4, issue in him
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1489154](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1489154)

---

### Post by cigtoxdoc on 2015-09-03
Thank you for your reply.  Network-manger on all three PCs is 0.9.10.0-4ubuntu23 .

John

---

