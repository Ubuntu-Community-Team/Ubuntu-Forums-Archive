---
title: "update QEMU"
date: 2016-03-15
forum: Virtualisation
---

### Post by p0wershell on 2016-03-15
hello!
canot update QEMU

virsh -c qemu:///system version --daemon


Compiled against library: libvirt 1.3.2
Using library: libvirt 1.3.2
Using API: QEMU 1.3.2
Running hypervisor: QEMU 2.0.0
Running against daemon: 1.3.2

from tarball 

cd ~
wget [http://wiki.qemu-project.org/download/qemu-2.5.0.tar.bz2](http://wiki.qemu-project.org/download/qemu-2.5.0.tar.bz2)


bzip2 -d qemu-2.5.0.tar.bz2 
tar xvf qemu-2.5.0.tar
cd qemu-2.5.0


mkdir build
cd build
../configure
make && make install

from git

cd ~
git clone git://git.qemu-project.org/qemu.git


cd qemu
mkdir -p bin/debug/native
cd bin/debug/native
../../../configure --enable-debug
make install
cd ../../..
cd ..

QEMU 2.0.0 all time....

what i can do?

---

### Post by p0wershell on 2016-03-15
kvm --version
QEMU emulator version 2.5.0, Copyright (c) 2003-2008 Fabrice Bellard

but

virsh -c qemu:///system version --daemon
Compiled against library: libvirt 1.3.2
Using library: libvirt 1.3.2
Using API: QEMU 1.3.2
**Running hypervisor: QEMU 2.0.0**
Running against daemon: 1.3.2

---

### Post by MAFoElffen on 2016-03-16
Just thinking out loud... if you look at the QEMU wiki pages on installing Qemu from source... it explicitly says that if you are using Ubuntu, and if you installed the QEMU package from the Ubuntu repo's, to remove the package before installing from source. (Then gives the commands for that.) 

With htat in mind ... I have to ask if you removed the previous version first?

---

