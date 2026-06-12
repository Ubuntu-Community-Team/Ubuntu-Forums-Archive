---
title: "virt-install throws an error"
date: 2014-07-07
forum: Virtualisation
---

### Post by steggur on 2014-07-07
Ubuntu 14.04 LDS Development 3.15.0-6-generic
ASUS Z97-C m/b
Haswell i7 4790
32Gb

Trying to set up a virtual machine using:
fallocate -l 57344 /var/lib/libvirt/images/Bodeind.img
sudo virt-install -r 8192 -n Bodeind -f /var/lib/libvirt/images/Bodeind.img --cdrom /usr/src/ubuntu-14.04-server-amd64.iso

When I do virt-install I get the following error:
Starting install...
ERROR    internal error: Cannot find suitable CPU model for given data
Domain installation does not appear to have been successful.
If it was, you can restart your domain by running:
  virsh --connect qemu:///system start Bodeind
otherwise, please restart your installation.

/etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto em1
iface em1 inet manual

auto ovsbr0
iface ovsbr0 inet static
    address 192.168.10.50
    netmask 255.255.255.0
    network 192.168.10.0
    broadcast 192.168.10.255
    gateway 192.168.10.1
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.10.40
    dns-search bodeind.is
    bridge_ports em1
root@mail:/var/lib/libvirt/images# 

followed this article to set up ovsbr0
[http://www.rivy.org/2014/04/install-a-kvm-host-on-ubuntu-14-04-trusty-tahr/](http://www.rivy.org/2014/04/install-a-kvm-host-on-ubuntu-14-04-trusty-tahr/)

Has anyone run into this problem or know a solution to this?

---

### Post by KillerKelvUK on 2014-07-07
Is this your first vm guest or do you have others running?  What hypervisor are you using?

Have you considered a GUI management tool such as Virt-Manager, automates most processes and minimises chance of a bad keystroke in cli?

---

### Post by steggur on 2014-07-07
This is the first vm guest using KVM.
I have both tried virt-install and virt-manager from a gui and I am getting the same error.

---

### Post by KillerKelvUK on 2014-07-08
Have you validated first your hardware is capable of running virtual machines?

Have a read through this [http://www.cyberciti.biz/faq/linux-xen-vmware-kvm-intel-vt-amd-v-support/](http://www.cyberciti.biz/faq/linux-xen-vmware-kvm-intel-vt-amd-v-support/)

Post back the results of running

```
grep --color vmx /proc/cpuinfo
```

---

