---
title: "W: Failed to fetch cdrom......."
date: 2010-08-04
forum: Ubuntu Studio
---

### Post by okrauss on 2010-08-04
Hi there. I wanted to install the network manager in Ubuntu Studio 10.04 with 
Synoptic Package Manager but I get the following for every package needed:

W: Failed to fetch cdrom:[Ubuntu-Studio 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/pool/main/n/network-manager/network-manager_0.8-0ubuntu3_i386.deb
  File not found

If I manually search this file on the cd, I see that it is there...located exactly in the directory above.

Why doesn't the package manager find it????

If I run a terminal and type: sudo apt-get install network-manager network-manager-gnome,
I also get errors!

Can anyone help me out of this???

---

### Post by cchhrriiss121212 on 2010-08-04
Just browse to the location and double click on the package, it will inform you of any possible dependencies it needs to run.

---

