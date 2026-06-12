---
title: "PXE install troubles"
date: 2010-05-03
forum: Server Platforms
---

### Post by Slonda828 on 2010-05-03
Hi all,

 I have to use my Ubuntu 9.10 netbook at work as an installation server, in order to install SUSE on remote machines via PXE. 

I currently have my Dhcp3-server up and running, my atftpd up and running, and syslinux installed. Netstat -uap lists that dhcp and atftpd are active.

I have syslinux installed, and I have mounted the SUSE dvd and copied its contents into the directory from which I plan on installing it. 

I boot up the client machine and hit F12 for PXE boot. The machine gets an IP address from the DHCP server right away, and then tries to get the kernel. It gives me a "could not find kernel" error and then gives me the finger.

Any ideas? I am open to posting logs and such if you need them.

---

