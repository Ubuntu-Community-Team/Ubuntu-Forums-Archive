---
title: "Installing Open Stack with TripleO"
date: 2015-02-28
forum: Server Platforms
---

### Post by john-vanommen on 2015-02-28
I've been working with Open Stack for a few years, but I've never done a deployment using Triple O. I thought I'd start a thread documenting the installation process, in case some other users might benefit from it.

First step is to install Ubuntu 14.04. Once that's done, install qemu, openvswitch, libvirt, python-libvirt, openssh-server and qemu-kvm.

The download is massive, nearly seven gigabytes. In order to facilitate the transfer from my laptop to the server hardware, I sliced up the download into 25mb chunks using 7zip. I also created parity archives using quickpar, in the event that any of the pieces aren't 100% valid.

---

### Post by john-vanommen on 2015-03-01
I spent some time getting ntp configured properly. Here's some things to look out for:

1) Have a reliable ntp server
2) Verify connectivity to that ntp server

I was seeing some random failures in the installation process, which were cause by issues with ntp.

---

### Post by john-vanommen on 2015-03-01
While installing Triple O, I ran into some issues. Being able to destroy the seed VM and the network bridge on the seed VM host comes in handy. Here's how I did it:

virsh destroy seed
virsh undefined seed
virsh net-undefined brbm
virsh net-destroy brbm
ovs-vsctl del-br brbm
ovs-vsctl emer-reset
ifdown eth0 && ifup eth0

---

