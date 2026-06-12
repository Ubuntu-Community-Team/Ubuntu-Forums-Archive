---
title: "Can not create VM using libvirt on KVM host"
date: 2014-02-16
forum: Virtualisation
---

### Post by AmbiguousOutlier on 2014-02-16
I've been following [this guide](https://help.ubuntu.com/community/KVM/Installation) to set up a virtual machines on my xeon (banana) to be run from my laptop (cherry);

here's my complete install process with the few errors I've been getting;
 
CPU can handle virtualisation;
```
rhys@banana:~$ egrep -c '(vmx|svm)' /proc/cpuinfo
8
```

```
rhys@banana:~$ cat /sys/hypervisor/properties/capabilities
cat: /sys/hypervisor/properties/capabilities: No such file or directory
```

the guide says;
[i]You must see hvm flags in the output.

Alternatively, you may execute:
kvm-ok [/i]

so I assume that missing sys/hypervisor/properties/capabilities does not matter. 

```
rhys@banana:~$ kvm-ok 
INFO: /dev/kvm exists
KVM acceleration can be used
```

```
rhys@banana:~$ egrep -c ' lm ' /proc/cpuinfo
8
```

```
rhys@banana:~$ uname -m
x86_64
```

everything for KVM is installed;
```
rhys@banana:~$ sudo apt-get install qemu-kvm libvirt-bin ubuntu-vm-builder bridge-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bridge-utils is already the newest version.
ubuntu-vm-builder is already the newest version.
libvirt-bin is already the newest version.
qemu-kvm is already the newest version.
```

```
rhys@banana:~$ sudo adduser `id -un` libvirtd
The user `rhys' is already a member of `libvirtd'.
```

according to this everything has been installed correctly.
```
rhys@banana:~$ virsh -c qemu:///system list
 Id    Name                           State
----------------------------------------------------

```

sock appears to have the correct permissions;
```
rhys@banana:~$ sudo ls -la /var/run/libvirt/libvirt-sock
srwxrwx--- 1 root libvirtd 0 Feb 16 11:59 /var/run/libvirt/libvirt-sock
```

/dev/kvm is now in the correct group. 
```
rhys@banana:~$ ls -l /dev/kvm
crw-rw---- 1 root kvm 10, 232 Feb 16 12:21 /dev/kvm
rhys@banana:~$ sudo chown root:libvirtd /dev/kvm
rhys@banana:~$ ls -l /dev/kvm
crw-rw---- 1 root libvirtd 10, 232 Feb 16 12:21 /dev/kvm
```

I had to run this with sudo;
```
rhys@banana:~$ sudo rmmod kvm
sudo modprobe -a kvm
```

I then switch to the client and install virt-manager;

```
rhys@cherry:~$ sudo apt-get install virt-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virt-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

I open the Virtual Machine Manager and add connection;
Hypervisor: QEMU/KVM
Connect to remote host
Method: SSH
Username: rhys
Hostname banana

Everything seems to connect, I then have; banana (QEMU) in the queue, which I right click and select New;

[i]Name: plum
Connection: banana(QEMU/KVM)

Choose how you would like to install the operating system[/i]

If I choose *Local install media* or *Network Install* and manually type in the location of 13.10 iso, I get;

*Error setting install media location.*

I've tried putting the iso on the client and the server and referenced them as if it's local. ie /home/rhys/13.10.iso. 


Can anyone see where I'm going wrong? 

Cheers

---

### Post by TheFu on 2014-02-19
The ISO must be in a managed, known-to-libvirt, storage location.
Set that up on the main virt-manager page.  The default storage locations for ISOs and VMs is under /var ... which sorta sucks. Make certain there is lots of storage in that area on the server.

Your userid on the KVM server needs to be in the libvirt group.
Also - it isn't clear that you've setup ssh access from the client to the server. Is that working outside the VM?

---

### Post by AmbiguousOutlier on 2014-02-19
> **TheFu said:**
> The ISO must be in a managed, known-to-libvirt, storage location.
Set that up on the main virt-manager page.  The default storage locations for ISOs and VMs is under /var

Yep that fixed it, and KVM is now working, thanks.

---

### Post by TheFu on 2014-02-19
Please mark thread as **solved** to help others.

---

