---
title: "Installing VMWare on 10.04 server"
date: 2012-05-22
forum: Virtualisation
---

### Post by mpessanha on 2012-05-22
Hello Guys !!

I am a newbie on this and while trying to install the Vmware on Ubuntu 10.04 server I got the below. can anyone help me on this.


FIRST TRY:

padmin@PMS2000x:~/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce$ sudo chmod +x vmware-server-2.0.x-kernel-2.6.3x-install.sh
[sudo] password for padmin:
padmin@PMS2000x:~/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce$ sudo ./vmware-server-2.0.x-kernel-2.6.3x-install.sh
You have VMware Server archive:
        VMware-server-2.0.2-203138.i386.tar.gz
Checking for needed packages on Ubuntu
You do have the linux-headers-2.6.32-41-generic-pae package...
Installing build-essential package...
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.4 liblzma1 libstdc++6-4.4-dev xz-utils
Suggested packages:
  debian-keyring debian-maintainers g++-multilib g++-4.4-multilib gcc-4.4-doc libstdc++6-4.4-dbg libstdc++6-4.4-doc
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.4 liblzma1 libstdc++6-4.4-dev xz-utils
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,601kB of archives.
After this operation, 24.7MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main libstdc++6-4.4-dev 4.4.3-4ubuntu5.1 [1,491kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main g++-4.4 4.4.3-4ubuntu5.1 [4,950kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main g++ 4:4.4.3-1ubuntu1 [1,442B]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main liblzma1 4.999.9beta+20091116-1 [152kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main xz-utils 4.999.9beta+20091116-1 [228kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main dpkg-dev 1.15.5.6ubuntu4.5 [654kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main build-essential 11.4build1 [7,278B]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main fakeroot 1.14.4-1ubuntu1 [118kB]
Fetched 7,601kB in 30s (247kB/s)
Selecting previously deselected package libstdc++6-4.4-dev.
(Reading database ... 69317 files and directories currently installed.)
Unpacking libstdc++6-4.4-dev (from .../libstdc++6-4.4-dev_4.4.3-4ubuntu5.1_i386.deb) ...
Selecting previously deselected package g++-4.4.
Unpacking g++-4.4 (from .../g++-4.4_4.4.3-4ubuntu5.1_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.4.3-1ubuntu1_i386.deb) ...
Selecting previously deselected package liblzma1.
Unpacking liblzma1 (from .../liblzma1_4.999.9beta+20091116-1_i386.deb) ...
Selecting previously deselected package xz-utils.
Unpacking xz-utils (from .../xz-utils_4.999.9beta+20091116-1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.15.5.6ubuntu4.5_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4build1_i386.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up liblzma1 (4.999.9beta+20091116-1) ...

Setting up xz-utils (4.999.9beta+20091116-1) ...
Setting up dpkg-dev (1.15.5.6ubuntu4.5) ...
Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up libstdc++6-4.4-dev (4.4.3-4ubuntu5.1) ...
Setting up g++-4.4 (4.4.3-4ubuntu5.1) ...
Setting up g++ (4:4.4.3-1ubuntu1) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.

Setting up build-essential (11.4build1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
You do have the patch package...
Extracting the contents of VMware-server-2.0.2-203138.i386.tar.gz
Found .tar file for vmnet module
Found .tar file for vsock module
Found .tar file for vmci module
Found .tar file for vmmon module
Extracting .tar files in order to apply the patch...
Untarring /home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet.tar
Untarring /home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vsock.tar
Untarring /home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmci.tar
Untarring /home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon.tar
Testing patch...
Creating some simlinks for the newer kernels...
ln: creating symbolic link `/usr/src/linux-headers-2.6.32-41-generic-pae/include/linux/autoconf.h': File exists
ln: creating symbolic link `/usr/src/linux-headers-2.6.32-41-generic-pae/include/linux/utsrelease.h': File exists
Applying patch...
Preparing new tar file for vmnet module
Preparing new tar file for vsock module
Preparing new tar file for vmci module
Preparing new tar file for vmmon module
Checking that the compiling will succeed...
Trying to compile vmnet module to see if it works
Performing make in /home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only
Using 2.6.x kernel build system.
/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: data definition has no type or storage class
/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: type defaults to âintâ in declaration of âDEFINE_SEMAPHOREâ
/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: parameter names (without types) in function declaration
/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:82: warning: type defaults to âintâ in declaration of âDEFINE_SEMAPHOREâ
/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:82: warning: parameter names (without types) in function declaration
/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c: In function âVNetFilter_HandleUserCallâ:
/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: âfilterIoctlSemâ undeclared (first use in this function)
/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: (Each undeclared identifier is reported only once
/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: for each function it appears in.)
make[2]: *** [/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.o] Error 1
make[1]: *** [_module_/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only] Error 2
make: *** [vmnet.ko] Error 2
There is a problem compiling the vmnet module after it was patched. :(
padmin@PMS2000x:~/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce$ 




SECOND TRY:  


padmin@PMS2000x:~/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce$ sudo ./vmware-server-2.0.x-kernel-2.6.3x-install.sh
You have VMware Server archive:
        VMware-server-2.0.2-203138.i386.tar.gz
Checking for needed packages on Ubuntu
You do have the linux-headers-2.6.32-41-generic-pae package...
You do have the build-essential package...
You do have the patch package...
Found .tar file for vmnet module
Found .tar file for vsock module
Found .tar file for vmci-temp module
Found .tar file for vmci module
Found .tar file for vsock-temp module
Found .tar file for vmnet-temp module
Found .tar file for vmmon-temp module
Found .tar file for vmmon module
Extracting .tar files in order to apply the patch...
Untarring /home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet.tar
Untarring /home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vsock.tar
Untarring /home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmci-temp.tar
vmci-temp.tar tarball failed to extract in the directory vmci-temp-only. :(
padmin@PMS2000x:~/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce$




THIRD attempted I guess with update 4 from /radu.cotescu.com

padmin@PMS2000x:~/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce2$ ls
LICENSE  README  start-VMware-console.sh  vmware-config.patch  VMware-server-2.0.2-203138.i386.tar.gz  vmware-server-2.0.2-203138-update.patch  vmware-server-2.0.x-kernel-2.6.3x-install.sh
padmin@PMS2000x:~/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce2$ chmod +x vmware-server-2.0.x-kernel-2.6.3x-install.sh
padmin@PMS2000x:~/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce2$ sudo ./vmware-server-2.0.x-kernel-2.6.3x-install.sh
[sudo] password for padmin:
You have VMware Server archive:
        VMware-server-2.0.2-203138.i386.tar.gz
Checking for needed packages on Ubuntu
You do have the linux-headers-2.6.32-41-generic-pae package...
You do have the build-essential package...
You do have the patch package...
Extracting the contents of VMware-server-2.0.2-203138.i386.tar.gz
Found .tar file for vmnet module
Found .tar file for vsock module
Found .tar file for vmci module
Found .tar file for vmmon module
Extracting .tar files in order to apply the patch...
Untarring /home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce2/vmware-server-distrib/lib/modules/source/vmnet.tar
Untarring /home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce2/vmware-server-distrib/lib/modules/source/vsock.tar
Untarring /home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce2/vmware-server-distrib/lib/modules/source/vmci.tar
Untarring /home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce2/vmware-server-distrib/lib/modules/source/vmmon.tar
Testing patch...
Creating some simlinks for the newer kernels...
ln: creating symbolic link `/usr/src/linux-headers-2.6.32-41-generic-pae/include/linux/autoconf.h': File exists
ln: creating symbolic link `/usr/src/linux-headers-2.6.32-41-generic-pae/include/linux/utsrelease.h': File exists
Applying patch...
Preparing new tar file for vmnet module
Preparing new tar file for vsock module
Preparing new tar file for vmci module
Preparing new tar file for vmmon module
Checking that the compiling will succeed...
Trying to compile vmnet module to see if it works
Performing make in /home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce2/vmware-server-distrib/lib/modules/source/vmnet-only
Using 2.6.x kernel build system.
/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce2/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: data definition has no type or storage class
/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce2/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: type defaults to âintâ in declaration of âDEFINE_SEMAPHOREâ
/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce2/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: parameter names (without types) in function declaration
/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce2/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:82: warning: type defaults to âintâ in declaration of âDEFINE_SEMAPHOREâ
/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce2/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:82: warning: parameter names (without types) in function declaration
/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce2/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c: In function âVNetFilter_HandleUserCallâ:
/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce2/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: âfilterIoctlSemâ undeclared (first use in this function)
/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce2/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: (Each undeclared identifier is reported only once
/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce2/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: for each function it appears in.)
make[2]: *** [/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce2/vmware-server-distrib/lib/modules/source/vmnet-only/filter.o] Error 1
make[1]: *** [_module_/home/padmin/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce2/vmware-server-distrib/lib/modules/source/vmnet-only] Error 2
make: *** [vmnet.ko] Error 2
There is a problem compiling the vmnet module after it was patched. :(

---

