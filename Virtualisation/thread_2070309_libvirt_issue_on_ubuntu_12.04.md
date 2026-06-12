---
title: "libvirt issue on ubuntu 12.04"
date: 2012-10-12
forum: Virtualisation
---

### Post by dubi on 2012-10-12
Hi

My system:  Ubuntu 12.04.1  , kerenl = 3.2.0-25-generic . libvirt and virsh version:  0.9.8
where libvirt came from the ubuntu standard install.

_[U]**PROBLEM**_[/U]:   I get from time to time the following error message :

"libvirtError: Failed to connect socket to '/var/run/libvirt/libvirt-sock': No such file or directory"

this happens after : Connecting to libvirt: qemu:///system from (pid=1363)

The libvirt-sock  is a  _**local domain socket **_(ls -l gives:
srwxrwx--- 1 root libvirtd 0 Sep  3 13:56 /var/run/libvirt/libvirt-sock ) 

NOTE the libvirtd is up  before and after the above error  message as shown by 'ps' output :
root      1574     1  0 16:23 ?        00:00:00 /usr/sbin/libvirtd -d -l


**On a similar system **with a slightly prior kernal version: 3.2.0-20-generic , there is no such problem .  ANY IDEA WHAT TO DO ?

---

### Post by fireoptic on 2012-10-14
> **dubi said:**
> Hi

My system:  Ubuntu 12.04.1  , kerenl = 3.2.0-25-generic . libvirt and virsh version:  0.9.8
where libvirt came from the ubuntu standard install.

_[U]**PROBLEM**_[/U]:   I get from time to time the following error message :

"libvirtError: Failed to connect socket to '/var/run/libvirt/libvirt-sock': No such file or directory"

this happens after : Connecting to libvirt: qemu:///system from (pid=1363)

The libvirt-sock  is a  _**local domain socket **_(ls -l gives:
srwxrwx--- 1 root libvirtd 0 Sep  3 13:56 /var/run/libvirt/libvirt-sock ) 

NOTE the libvirtd is up  before and after the above error  message as shown by 'ps' output :
root      1574     1  0 16:23 ?        00:00:00 /usr/sbin/libvirtd -d -l


**On a similar system **with a slightly prior kernal version: 3.2.0-20-generic , there is no such problem .  ANY IDEA WHAT TO DO ?


Had a similar issue with my install a few days ago try,

```
sudo apt-get install libvirt-bin
```That worked for me.

---

