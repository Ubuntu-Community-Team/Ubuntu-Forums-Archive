---
title: "VirtualBox: error NS_ERROR_FAILURE (0x80004005) when starting a newly created VM"
date: 2015-04-27
forum: Virtualisation
---

### Post by Ron_Barak on 2015-04-27
I'm trying to create a new VirtualBox, but am getting NS_ERROR_FAILURE (0x80004005).

Googling suggested it's because of changes in the VM, or of certain ISOs.
However - this is first time I install, so no changes, and - same error occurs with a different ISO (ubuntu-14.04.2-server-amd64.iso).

```
openstack@ubuntu:~$ VBoxManage createvm --name openstack101 --ostype Ubuntu_64 --register
Virtual machine 'openstack101' is created and registered.
UUID: 5ed09907-a379-447c-bdec-005e64a8534f
Settings file: '/home/openstack/VirtualBox VMs/openstack101/openstack101.vbox'
openstack@ubuntu:~$ VBoxManage modifyvm openstack101 --memory 2048 --nic1 nat --nic2 hostonly --hostonlyadapter2 vboxnet0 --nic3 hostonly --hostonlyadapter3 vboxnet1
openstack@ubuntu:~$ VBoxManage storagectl openstack101 --name "IDE Controller" --add ide --controller PIIX4 --hostiocache on --bootable on
openstack@ubuntu:~$ VBoxManage storageattach openstack101 --storagectl "IDE Controller" --type dvddrive --port 0 --device 0 --medium ~/shared/images/ubuntu-12.04.5-server-amd64.iso
openstack@ubuntu:~$ VBoxManage storagectl openstack101 --name "SATA Controller" --add sata --controller IntelAHCI --hostiocache on --bootable on
openstack@ubuntu:~$ VBoxManage createhd --filename openstack101.vdi --size 204800%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
Disk image created. UUID: af5ea0ef-9189-42d9-b0e0-0c9e25af464a
openstack@ubuntu:~$ VBoxManage storageattach openstack101 --storagectl "SATA Controller" --port 0 --device 0 --type hdd --medium openstack101.vdi
openstack@ubuntu:~$
openstack@ubuntu:~$ VBoxManage startvm openstack101 --type gui
Waiting for VM "openstack101" to power on...
VBoxManage: error: The virtual machine 'openstack101' has terminated unexpectedly during startup with exit code 0
VBoxManage: error: Details: code NS_ERROR_FAILURE (0x80004005), component Machine, interface IMachine, callee
openstack@ubuntu:~$
```

Any ideas?

Note that trying to start the same VM as headless gives no problem:

openstack@ubuntu:~$ VBoxManage startvm openstack101 --type headless
Waiting for VM "openstack101" to power on...
VM "openstack101" has been successfully started.
openstack@ubuntu:~$

[HR][/HR]Environment:

[LIST]
[*]VBoxManage version 4.1.12_Ubuntur77245
[*]Host OS: Windows 7
[*]Guest OS: Linux ubuntu 3.13.0-32-generic #57~precise1-Ubuntu SMP Tue Jul 15 03:51:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
[/LIST]
[HR][/HR]Installation procedure above is following the book: Jackson, Kevin. OpenStack Cloud Computing Cookbook. Birmingham: Packt Publishing, 2013.

---

### Post by erikeze on 2015-04-30
Do you have qt4 installed? Because it is required for gui frontend.

---

### Post by Ron_Barak on 2015-04-30
> **erikeze said:**
> Do you have qt4 installed? Because it is required for gui frontend.
Thanks, that seems a reasonable suggestion. 
Alas:
```
openstack@ubuntu:~$ sudo apt-get install libqt4-core libqt4-gui --upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
libqt4-gui is already the newest version.
libqt4-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
openstack@ubuntu:~$ VBoxManage startvm UbuntuTest --type gui
Waiting for VM "UbuntuTest" to power on...
VBoxManage: error: The virtual machine 'UbuntuTest' has terminated unexpectedly during startup with exit code 0
VBoxManage: error: Details: code NS_ERROR_FAILURE (0x80004005), component Machine, interface IMachine, callee
openstack@ubuntu:~$

```

---

### Post by pravinbravi on 2015-10-20
this fixed my problems Ubuntu 15.10 AMD64

sudo /sbin/rcvboxdrv setup

---

### Post by bvidinli on 2015-10-21
Thank you pravinbravi, that solved my issue too, 

sudo /sbin/rcvboxdrv setup

---

