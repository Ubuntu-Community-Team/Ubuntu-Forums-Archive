---
title: "cpu0 unhandled rdmsr"
date: 2011-05-25
forum: Virtualisation
---

### Post by bigmonmulgrew on 2011-05-25
Hi
I've just created my first vm (successful) on ubuntu 11.04 server
When starting the vm I get the error 

```
 my_vm [ 1517.404543] kvm: 18929: cpu0 unhandled rdmsr@ 0xc0010001
```

I've googled but cant find this error.
Anyone know what causes it or how to fix it.

Tips would also be appreciated

appologies for any ignorance but I have very little experience with ubuntu server and linux VMs. I guess I'm going to get requests for more info now. 

I used the following to create the VM 

```

sudo ubuntu-vm-builder kvm natty \
--flavour virtual \
--domain my_vm \
--dest my_vm \
--arch amd64 \
-o \
--hostname my_vm \
--mem 256 \
--rootsize 20480 \
--swapsize 2048 \
--name 'bigmonmulgrew' \
--user username \
--pass password \
--bridge br0 \
--ip 192.168.0.202 \
--mask 255.255.255.0 \
--net 192.168.0.0 \
--bcast 192.168.0.255 \
--gw 192.168.0.10 \
--dns 192.168.0.10 \
--components main,universe \
--addpkg acpid \
--addpkg vim \
--addpkg openssh-server \
--addpkg avahi-daemon \
--libvirt qemu:///system ;


```

---

