---
title: "kvm with virtio network from command line"
date: 2012-01-16
forum: Virtualisation
---

### Post by jabbadoo on 2012-01-16
Right now I have a script which calls kvm. It looks something like this:
```
...
model=ne2k_pci
...
kvm -net nic,vlan=0,macaddr=$ranmac,model=$model -net tap,vlan=0,ifname=$iface,script=no .......
```The network stops after some load, and the solution could be virtio. In [the guide]("https://help.ubuntu.com/community/KVM/Networking#virtio") for virtio with KVM I should "add" this to the command:
```
-net nic,model=virtio -net user
```Should I just *add* this to the existing script or is there something I have to change in the existing script? Do I need to merge them somehow?

---

### Post by imachavel on 2012-01-16
I have no clue what so ever, I'm guessing you are WAY past this:

[http://www.ibm.com/developerworks/linux/library/os-python-kvm-scripting1/index.html?ca=drs-](http://www.ibm.com/developerworks/linux/library/os-python-kvm-scripting1/index.html?ca=drs-)

---

