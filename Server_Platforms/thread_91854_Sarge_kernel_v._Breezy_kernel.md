---
title: "Sarge kernel v. Breezy kernel"
date: 2005-11-18
forum: Server Platforms
---

### Post by steffen on 2005-11-18
I dist-upgraded a server from Sarge to Breezy. However 'uname -r' returns '2.4.27-2-686', so the kernel has not been upgraded.

I only run a limited number of apps on this server - Apache, MySQL, bind, php, etc. I don't mind running the 2.4 kernel. However, can I run into compatibility issues by running the 2.4 kernel?

---

### Post by GTvulse on 2005-11-18
If you are using LVM2 or EVMS you probably will.

---

### Post by ubuntu_demon on 2005-11-18
ensure that everything is installed by :

$sudo apt-get update 
$sudo apt-get install ubuntu-base ubuntu-desktop
$sudo apt-get dist-upgrade

Take a look at the postupgrade instructions here :
[https://wiki.ubuntu.com/BreezyUpgrade](https://wiki.ubuntu.com/BreezyUpgrade)
[https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)

Regarding the kernel if you have a 686 processor just type :
$sudo apt-get install linux-686

And during boot make sure you boot the 686 kernel (press esc to get into grub if necessary)

---

