---
title: "Does anyone have a winning formula for deploying 10.04 with vmbuilder?"
date: 2010-08-03
forum: Virtualisation
---

### Post by samosamo on 2010-08-03
I am trying to develop a workflow for deploying Ubuntu 10.04 Server virtual machines on ESXi using vmbuilder.  I want to automate as much as possible.  Things like installing openssh-server, open-vm-tools, vmxnet3 network, paravirtual disk controller, etc etc.  I just thought I'd ask here first before I reinvent the wheel.

openssh-server was easy.  open-vm-tools and open-vm-dkms install, but not successfully, as I must use dpkg-reconfigure when the machine boots for it to work.  I have not yet figured out if hardware manipulation is possible to configure a vmxnet3 NIC and Paravirtual SCSI controller.

Post your configs!!

```
[DEFAULT]
arch = amd64
#part = vmbuilder.partition # haven't gotten this to work yet
user = vmtest 
name = vmtest
pass = vmtest
hostname = vmtest
tmpfs = -

[ubuntu]
mirror = http://10.0.0.116:9999/ubuntu
security-mirror = http://10.0.0.116:9999/ubuntu
suite = lucid
flavour = virtual
components = main, restricted, universe, multiverse
addpkg = snmpd
timezone = EST
ssh_user_key = .ssh/authorized_keys2
execscript = /home/admin/execscript.sh
```

```

#!/bin/bash

chroot $1 apt-get update
chroot $1 apt-get dist-upgrade
chroot $1 apt-get install -qqy --force-yes openssh-server
chroot $1 apt-get install -qqy --force-yes --no-install-recommends linux-headers-virtual open-vm-dkms open-vm-tools # this is not working yet
```

---

### Post by samosamo on 2010-08-04
I figured out how to define the hardware I want.  Specifically vmxnet3 NIC and Paravirtual SCSI controller.  However, they will not work immediately unless I first figure out how to correctly install VMWareTools or open-vm-tools first.

Either use the --templates option or edit the vmx template in /etc/vmbuilder/vmware like so:

```
#ethernet0.virtualDev = "e1000" # Comment out this line
ethernet0.virtualDev = "vmxnet3" # Add this line

```
```
#scsi0.virtualDev = "lsilogic" # Comment out this line
scsi0.virtualDev = "pvscsi" # Add this line

```

---

### Post by samosamo on 2010-08-06
ttt

---

### Post by buniti on 2010-11-28
Samosamo,

No winning formula from me, sorry. 
I did not used the complete config file method but straight command  using the --part=vmbuilder.partition to call the config file for  diskpart. It seems you can't create more than 4 partitions, since  vmbuilder is creating primary ext2 partitions.
I recall reading somewhere, no source:-(, that this calling of  '.partition' files is not working. (This might be based on your issue..)

Energy, buniti

---

