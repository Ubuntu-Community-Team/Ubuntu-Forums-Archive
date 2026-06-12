---
title: "kvm and ubuntu: High cpu load with network io"
date: 2017-10-28
forum: Virtualisation
---

### Post by jmarin on 2017-10-28
Hi,

I have installed ubuntu-server 16.04.3 as host and kvm guest OS on Compulab uSVR with SSD disks.  I set up the guest using virt-manager and changed NIC device model to virtio.  On the host side the system uses a bridge device.  Everything works, but when I receive data from network to the guest, qemu-system-x86_64 uses 100% or more cpu on the host side.  My network is currently only 100 Mbps, so the cpu load is way too high.  The same happens with NFS and scp.  Outbound traffic causes about 70% cpu load. 

I tried the same with xen (the same guest running off the same disk as with kvm) and the cpu load was only 16% (same network and getting the same 11.5 MBps to the guest).  With xen, the system power consumption was 22 W during the file transfer - with kvm, it was 32 W.

I have tried googling and checking everything I know of, but I can't get the cpu load down with kvm.  When the host and guest are idle, the cpu load is close to zero with both kvm and xen.

(On the other hand, disk io is much faster with kvm, so it makes harder to switch to xen..)

Any ideas?  Other than switching permanently to xen.. :-)

---

### Post by TheFu on 2017-10-28
How did you setup the linux bridge?  The default bridges form libvirt have a history of poor performance, while manually created bridges provide native network performance.

Which chips are used in the NIC?  realtek requires more CPU than Intel PRO/1000 NICs. Intel off-loads most processing to the ASIC on the NIC.  This is well documented.

I used Xen for a few years. Only had a few issues with it - usually refusing to boot after a kernel update and issues with kernel modules inside guests having conflicts - nfs would be an issue, for example. Besides that it was good, solid.

Anyway - that's all I have for suggestions.

---

### Post by jmarin on 2017-10-28
The bridge is configured in /etc/network/interfaces, the configuration is the same for both kvm and xen.  And as it's the qemu_system... process that is using lots of cpu, I don't think it's the bridge to blame?

The NIC(s) are Intel Pro/1000 and they are the same with both xen and kvm :-)

I have been using xen for several years, but I thought I'd give kvm a try as I've read it has a slightly better performance.. but if it eats the cpu like this, I'll probably install xen on the boot disk and forget about kvm.

---

### Post by TheFu on 2017-10-28
Are your VMs using KVM acceleration or only QEMU?   Qemu is slower than full KVM (HW) acceleration.

Using Xen isn't the end of the world, especially if it works better on your hardware.
There are lots of other tweaks (caching model, CPU pinning/types), but none better than using virtio for storage and networking.

I'm confused. In the OP, you say you have 10/100 network, but then claim to have Intel PRO/1000 NICs?  Which is it?  Is it just that you don't have a GigE switch?  I see 920 Mbps on my Intel NICs with a $20 GigE switch.  Regardless of the physical NIC, the guests should be using virtio, period. Always.

From inside the guest, the virtio for networking
```
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Virtio network device
       vendor: Red Hat, Inc
       ....

```

There are some not-so-great settings that can be put into the bridge setup.  If you post it, someone might be able to help.

---

### Post by jmarin on 2017-10-28
Thanks for the replies.  I'm new to kvm, how can I tell if I'm using KVM or only QEMU?  I created the guest machine using the GUI software and the guest is automatically started, so .. ;-)  On the host side, I see this [COLOR=#000000]qemu-system-x86_64 process with a very long list of command line options including "-enable-kvm".

Yes, the system has gigabit Ethernet ports, but the switches are only 10/100 Mbps at the moment.  lshw prints the same information on my guest as on yours.  Bridge config is:

[/COLOR][COLOR=#000000]auto br0
iface br0 inet static
  address a.b.c.d/24
  bridge_ports enp0s25
  bridge_stp      off
  bridge_maxwait  0
  bridge_fd       0
[/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by TheFu on 2017-10-28
That address line isn't like any I've ever seen.
Normally, there are 3 lines needed.  address, gateway, netmask.

I see in the 16.04 manpages for "interfaces" that address like you've specified should work - that would cover the address and netmask, but not the gateway.
I use:```

  bridge_fd 0
  bridge_hello 2
  bridge_maxage 12
  bridge_stp off
```

The manpage for the bridge-utils-interfaces has some very interesting information inside.  It does not show the address as you have shown it. Don't know if that matters or not.

---

### Post by jmarin on 2017-10-29
I decided to go to xen, but I'm still interested if someone knows how to solve the high cpu load problem with kvm.

---

### Post by TheFu on 2017-10-29
> **jmarin said:**
> I decided to go to xen, but I'm still interested if someone knows how to solve the high cpu load problem with kvm.

I can assure you that network performance issues/overhead aren't a normal concern with KVM. 
I assume you tuned your KVM setup using the main available guides?

[https://www.linux-kvm.org/page/Tuning_KVM](https://www.linux-kvm.org/page/Tuning_KVM)

[https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html-single/Virtualization_Tuning_and_Optimization_Guide/](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html-single/Virtualization_Tuning_and_Optimization_Guide/)

I wish you luck.  Having the choice between 2 great server-class, F/LOSS, hypervisors really is great, however.

---

