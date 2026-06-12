---
title: "'ubuntu-vm-builder kvm hardy [...]' installs lucid"
date: 2011-07-11
forum: Server Platforms
---

### Post by addihetja on 2011-07-11
I've followed the instructions given at [https://help.ubuntu.com/community/KVM/CreateGuests](https://help.ubuntu.com/community/KVM/CreateGuests) and created VMs. Everything is working fine except that the command I'm using to create the VMs installs lucid, but not hardy

The command I'm using is:
```
sudo ubuntu-vm-builder kvm hardy --arch 'i386'  --mem '1024'  --rootsize '256000'  --swapsize '1024'  --kernel-flavour 'generic'  --hostname 'ubuntu804'  --mirror 'http://de.archive.ubuntu.com/ubuntu'  --components 'main,universe'  --addpkg 'openssh-server'  --name 'example'  --user 'ubuntu'  --pass 'ubuntu'  --ip '192.168.80.7'  --mask '255.255.255.0'  --net '192.168.80.0'  --bcast '192.168.80.255'  --gw '192.168.80.254'  --dns '192.168.80.3' 
```

The host is running 64bit natty which leads me to believe that ubuntu-vm-builder is not getting the erroneous setup from the hosts /etc/apt/sources.list. What am I doing wrong? Is this a bug?

The application I'm installing requires 32bit hardy

---

### Post by addihetja on 2011-07-12
I found a workaround for this issue.

```
vmbuilder kvm ubuntu --suite hardy --arch i386  --mem 1024  --rootsize 256G  --swapsize 1024  --kernel-flavour server  --hostname 'ubuntu804'  --mirror 'http://de.archive.ubuntu.com/ubuntu'  --components 'main,universe'  --addpkg 'openssh-server'  --name 'Exampe'  --user 'ubuntu'  --pass 'ubuntu'  --ip '192.168.80.7'  --mask '255.255.255.0'  --net '192.168.80.0'  --bcast '192.168.80.255'  --gw '192.168.80.254'  --dns '192.168.80.3'--libvirt qemu:///system
```

It appears that the ubuntu-vm-builder wrapper around vmbuilder is not handling all releases of ubuntu correctly. The workaround is calling vmbuilder directly and using the "--suite hardy" parameter.

---

