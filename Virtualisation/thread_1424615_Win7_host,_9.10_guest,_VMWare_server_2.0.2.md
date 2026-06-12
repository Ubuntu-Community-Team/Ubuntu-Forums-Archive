---
title: "Win7 host, 9.10 guest, VMWare server 2.0.2"
date: 2010-03-08
forum: Virtualisation
---

### Post by james000222 on 2010-03-08
My first post here - hopefully not too much of a noob.

Windows 7 Professional 64 bit (host)
Ubuntu 9.10 64bit generic (guest)
kernel: 2.6.31-19-generic

The good news:
vmware-tools installed after many issues. Using a modification of the combined open source vmware tools integrated into the vmware-tools-distrib install package. 

The mod involved:
VMwareTools-7.7.6-203138
open-vm-tools-2010.02.23-236320

step 1: get open-vm-tools to compile. I had a shared/static library issue with a library that drove me crazy until I manually compiled/installed the library. 

step 2: completely ignore instructions in other threads about copying tar files from open-source to the VMwareTools distro. That no longer works. Here's what does work:

step 3: generate a binary distro subdirectory in the /lib/modules/binary/ directory of the vmware-tools-distrib. I called mine
bld-2.6.31-19-x86_64generic-Ubuntu9.10

step 4: hack the properties file: 

UtsRelease 2.6.31-19-generic
UtsVersion #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010
UtsMachine x86_64
ModVersion yes
SMP yes
PageOffset FFFF810000000000
Comment Ubuntu9.10, 2.6.31-19, amd64, generic


Note: I have no idea what the PageOffset does. It varies across the various directories. I left it alone, copied/edited this one from the closes ubuntu dist.

step 5: copy the compiled module files from the open-source compile (I think they are under modules/linux in the open-vm-tools) to the binary directory under bld-2.6.31-19-x86_64generic-Ubuntu9.10. So you should have /lib/modules/binary/bld-2.6.31-19-x86_64generic-Ubuntu9.10/ and under that one file (properties) and one directory (objects) with the compiled module (o files). Just look at the structure of the other distro directories...they are all the same.

step 6: delete the rest of the binary-distro directories. They don't work anyway. 

step 7: run the install script. I got everything to install, except vmci.

The BAD news: 
james@ubuntu:~$ sudo mount -t vmhgfs .host://share_ubuntu /mnt/hgfs
Error: cannot mount filesystem: Input/output error

The other BAD news:
Despite multiple variations of settings in xorg.conf, my logitech gamer mouse wheel will NOT roll up. Instead, that jumps down at a rate about 5x the down rate of a backwards roll of the wheel.

Any help with these latter two issues would be greatly appreciated. It's been mostly a labor of "I CAN do this"...I expect samba will work fine for filesharing. :)  The mouse, however, is annoying. :(

Cheers, J

---

