---
title: "KVM/QEMU Subnet"
date: 2012-08-01
forum: Virtualisation
---

### Post by garebearcarson on 2012-08-01
[COLOR=#000000][FONT=Sans]I want to test a [maas]("https://wiki.ubuntu.com/ServerTeam/MAAS/") install via kvm/qemu/libvrt (using virt-manager). Is there a way I can create a subnet and install a maas host as dhcp owner within that subnet?

I would prefer the subnet to use NAT to connect out as well, but this is not essential.

Edit:
Easier than I thought, just added the line 
```
<bootp file='pxelinux.0' server='192.168.122.236' />
```
to the libvrt network to enable pxe booting from the guest server [/FONT][/COLOR][COLOR=#000000][FONT=Sans]192.168.122.236[/FONT][/COLOR]

---

