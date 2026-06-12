---
title: "Ubuntu Server 16.04.2 LTS - SCST Problem"
date: 2017-03-11
forum: Server Platforms
---

### Post by alexankius on 2017-03-11
Hi all,

Disclaimer: I am unfortunately a noob.

I had an Openfiler setup with SCST and a Qlogic 2460 working perfectly, but recently decided to move to Ubuntu, just to see if this would work faster.

I did not manage to patch the kernel (4.4.0-66.generic) so instead I've installed SCST "standalone". I am at the stage where I have installed SCST but when I try to start the service I get:

modprobe: FATAL: Module iscsi-scst not found in directory /lib/modules/4.4.0-66-generic

Any ideas much appreciated!!

By the way these are the step I used thus far:

1. Sudo apt-get update
2. Sudo apt-get upgrade
3. sudo apt-get install fakeroot kernel-wedge build-essential makedumpfile kernel-package libncurses5 libncurses5-dev subversion 
4. sudo apt-get upgrade
5. Shutdown -r now
6. sudo sed -i -- 's/#deb-src/deb-src/g' /etc/apt/sources.list && sudo sed -i -- 's/# deb-src/deb-src/g' /etc/apt/sources.list
7. sudo apt-get update
8. sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)
9. make 2release
10. make scst scst_install iscsi iscsi_install scstadm scstadm_install

everything fine up to this point. the problem is using scst..

---

### Post by alexankius on 2017-03-14
Anyone?

---

### Post by gstanden on 2017-07-08
UPDATE 2017-08-05

I now have a method for building SCST DKMS modules for Ubuntu Linux 15.04-17.04+ from SCST source code.  This is the recommended best method imho because DKMS means that module rebuilds across kernel updates are taken care of for you automatically.  Thanks to DKMS you won't have to rebuild SCST modules each time you upgrade your kernel.  Even better, I've automated the whole process.  Instructions are here:

[https://sites.google.com/site/nandydandyoracle/scst/scst-debian-dkms-package-build-from-source-ubuntu-17-04](https://sites.google.com/site/nandydandyoracle/scst/scst-debian-dkms-package-build-from-source-ubuntu-17-04)

If for some reason you can't/don't want to use DKMS you can use my checkinstall method here (but I highly recommend the DKMS preferred method above).

Checkinstall SCST method for Ubuntu:

[https://sites.google.com/site/nandydandyoracle/scst/scst-package-build-and-install-ubuntu-17-04---14-04](https://sites.google.com/site/nandydandyoracle/scst/scst-package-build-and-install-ubuntu-17-04---14-04)

I also have a debuild SCST blog page for SCST on Ubuntu here:

[https://sites.google.com/site/nandydandyoracle/scst/scst-debian-package-build-from-source-ubuntu-17-04](https://sites.google.com/site/nandydandyoracle/scst/scst-debian-package-build-from-source-ubuntu-17-04)

Note that the debuild SCST work revealed that you will probably need to do the additional SCST post-package install steps that are on the debuild method for the checkinstall method also.

---

