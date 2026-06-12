---
title: "Problem with vdekvm under Ubuntu Karmic"
date: 2010-03-23
forum: Virtualisation
---

### Post by k3Rn on 2010-03-23
Hello,

I am using VDE networking for my kvm-VMs. The kvm versions from the Ubuntu repositories still don't support VDE nativly. So i am forced to use the vdeq/vdekvm wrapper to start my VMs. 

Since I now upgraded my Ubuntu system from Jaunty to Karmic I have a weird problem. When launching a VM, two vdekvm processes get started. One with the vde configuration and one with a 'dummy' tap interface, that i don't want. I have no clue why this second process gets started.

Have a look at the bash output:
-------------------------------------------------------------------------
markus@kvm-host:/kvm/images$ vdekvm -hda win7.img -net nic,macaddr=00:31:5e:ef:e8:be,model=virtio -net vde,sock=/home/markus/vde_network/switches/sw-data.ctl -snapshot &
[1] 3662
markus@kvm-host:/kvm/images$ arg ,sock=/home/markus/vde_network/switches/sw-data.ctl
TUNGETIFF ioctl() failed: Invalid argument
TUNSETOFFLOAD ioctl() failed: Bad address

markus@kvm-host:/kvm/images$ ps aux | grep vdekvm

markus    3662  0.0  0.0  19052   836 pts/1    S    02:09   0:00 vdekvm -hda win7.img -net nic,macaddr=00:31:5e:ef:e8:be,model=virtio -net vde,sock=/home/markus/vde_network/switches/sw-data.ctl -snapshot

markus    3668 71.3  1.6 304260 137592 pts/1   Sl   02:09   0:07 vdekvm -hda win7.img -net nic,macaddr=00:31:5e:ef:e8:be,model=virtio -net tap,vlan=0,fd=3 -snapshot

markus    3680  0.0  0.0   7336   892 pts/1    S+   02:10   0:00 grep vdekvm

markus@kvm-host:/kvm/images$ 
-------------------------------------------------------------------------

I am used to the TUNGETIFF error. This should be a bug in vdeq - the vde-network is working properly.

I am more concerned about that second process with the default tap device.

I am considering to update kvm manually to the newest version (0.12.3 if i am right). I hope both the TUNGETIFF as the error with the second process may disappear. Do you think i should try that / what might be the problem? May someone help me briefly on how to update kvm to the newest version with native vde support under Ubuntu, to get rid of the wrapper scripts?

Any help appreciated!

Greets,
Markus

---

### Post by k3Rn on 2010-03-24
Seems like i got it working now.

I downloaded qemu-kvm-0.12.3 and compiled it with ./configure --enable-vde --prefix=/usr .

Now i can use kvm with native vde support enabled. The TUNGETIFF errors from vdeq are also gone.

---

