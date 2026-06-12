---
title: "trixbox install in virtual box"
date: 2010-09-03
forum: Server Platforms
---

### Post by mrakash on 2010-09-03
I have ubuntu 2.6.32-24-generic in my virtual box  and i want to install tirxbox in it.
I have iso of trixbox and i want to install it. Can anybody help me the way to install it.
thanksx

---

### Post by BkkBonanza on 2010-09-03
I haven't done this with trixbox but it is built on Centos and should work the same. 

First, create a new VM selecting Linux, Centos and then the characteristics you want.
Once it shows up in the list of machines select it and choose Settings. Select Storage and then the CD-ROM drive and use the file/image selection option to mount an ISO file.

When you start the VM it should boot from the ISO and you can install to the hard disk image you created with the VM.

Whether there are problems or not with Trixbox I can't say. This is just the regular way to create and install a new VM from an ISO file.

---

### Post by spynappels on 2010-09-03
That will work, I have created VMs of Asterisk PBXs on both Virtualbox and VMWare hosts. Just be aware that some features will be much more difficult to implement on a VM, such as PSTN lines into the PBX. However, using a SIP provider works very well.

Just make sure to allocate plenty of RAM to the VM, it needs quite a lot to run well.

---

### Post by nnamdi on 2010-09-03
hello it is quite straight forward just make sure you a proper configuration on your virtual box the run the normal installation,  most especially configure your NIC on virtual box so you be able to call up the ip address from your host system or any system on your network

---

