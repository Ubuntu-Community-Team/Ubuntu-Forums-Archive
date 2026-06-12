---
title: "I'm looking the kernel installer files for ubuntu 20.10 for armhf / raspberry 4"
date: 2021-04-10
forum: Virtualisation
---

### Post by marietto2008 on 2021-04-10
Hello.

I would like to virtualize ubuntu 20.10 for armhf / raspberry pi 4 on my jetson nano. Previously I've virtualized debian buster for armhf using this tutorial :

[https://translatedcode.wordpress.com/2016/11/03/installing-debian-on-qemus-32-bit-arm-virt-board/](https://translatedcode.wordpress.com/2016/11/03/installing-debian-on-qemus-32-bit-arm-virt-board/)

he used two files to install the os on the qcow2 image file. They are called "initrd.gz and vmlinuz" and they are located here :

[http://http.us.debian.org/debian/dists/buster/main/installer-armhf/current/images/netboot/](http://http.us.debian.org/debian/dists/buster/main/installer-armhf/current/images/netboot/)

I would like to find the same files,but for ubuntu 20.10 for armhf that can emulate ubuntu for raspberry 4 on my jetson nano. I've found similar files,but for ubuntu 18.04,gotten from here :

[http://ports.ubuntu.com/ubuntu-ports/dists/bionic-updates/main/installer-armhf/current/images/generic-lpae/netboot/](http://ports.ubuntu.com/ubuntu-ports/dists/bionic-updates/main/installer-armhf/current/images/generic-lpae/netboot/)

unfortunately they aren't able to satisfy my needs,for two reasons :

    ubuntu 18.04 is old (and the same files for ubuntu 20.04 or 20.10 don't exist. When I click on the "Ubuntu 20.04 LTS (Focal Fossa) netboot images",I'm invited to "Try the New Ubuntu Server Installer",but that's not what I need.

    they are not tailored for the raspberry pi 4.

In any case, if the kernel installer files for raspberry do not exist, those for ubuntu 20.10 would also be fine. Can you provide the working links for finding these files ? thanks.

---

