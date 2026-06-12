---
title: "No sound on Vista"
date: 2009-12-04
forum: Virtualisation
---

### Post by satimis on 2009-12-04
Hi folks,

KVM
host OS - Debian 5.0
vm - Vista Ultimate

I succeeded installing Vista Ultimate on a VM with following commands;```

satimis@vm0:~$ sudo virt-install --connect qemu:///system -n vm26vista -r 1024 --vcpus=2 -f /home/satimis/VM/vm26vista.qcow2 -s 18 -c /dev/cdrom --vnc --noautoconsole --accelerate --network=bridge:br0 --hvm

```

Vista is running but without sound.  I have been googling a while without result.  Please advise.  TIA


B.R.
satimis

---

