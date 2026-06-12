---
title: "virt-manager help (why does it want to install KVM?)"
date: 2009-07-17
forum: Virtualisation
---

### Post by champi0n on 2009-07-17
I want to install virt-manager to manage my Xen Host. BUT its trying to install a bunch of KVM garbage.

```

champi0n@xen-box:~$ sudo apt-get install virt-manager
[sudo] password for champi0n: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  kvm libvirt-bin libvirt0 lvm2 netcat-openbsd python-gtk-vnc python-libvirt
  python-urlgrabber python-virtinst watershed
Suggested packages:
  ubuntu-vm-builder vde2 samba kvm-source kvm-pxe virt-viewer qemu
The following NEW packages will be installed:
  kvm libvirt-bin libvirt0 lvm2 netcat-openbsd python-gtk-vnc python-libvirt
  python-urlgrabber python-virtinst virt-manager watershed
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 3078kB of archives.
After this operation, 12.6MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

Any suggestions? I don't want to use KVM. I already installed ubuntu-xen-server.

---

### Post by bodhi.zazen on 2009-07-17
Well Xen dom0 is not supported beyond Ubuntu 8.04 9? LTS only ?) so naturally kvm is going to be a dependency.

I would install from source (as Ubuntu's version of virt-manager is, IMO, outdated) and/or file a bug report asking to remove kvm as a dependency (unlikely).

---

### Post by champi0n on 2009-07-17
Who makes the decisions to integrate KVM? They should be fired.

---

### Post by juancarlospaco on 2009-07-17
**[Use Convirt, its nicer than virt-manager]("http://www.tecnicoslinux.com.ar/livecd/auto-repo-cnvrt_1_all.deb")**

---

