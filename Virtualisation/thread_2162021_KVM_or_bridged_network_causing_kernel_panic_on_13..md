---
title: "KVM or bridged network causing kernel panic on 13.04?"
date: 2013-07-12
forum: Virtualisation
---

### Post by 1clue on 2013-07-12
Hi,

I have an Xubuntu host running 13.04 with qemu-kvm and bridged networking per the documentation.  The guests are on LVM2 and generally using raw disk type.

I get occasional kernel panics, like once a week.  So far I've been so anxious to get the box back up that I haven't had time to really investigate, but on one occasion the screen showed an exception which was in the br0 interface.

So I guess I have to ask a couple questions:
[LIST=1]
[*]Is anyone else getting this sort of thing?  I think not because I'm not finding it in the forum.
[*]Is 12.04 going to be more stable than 13.04?
[*]Is it feasible to wipe off the 13.04 on the host and put 12.04 on it, and still use the same guests?
[*]Is it reasonable to expect more stability that way?
[/LIST]

Thanks.

---

### Post by DrJohn999 on 2013-07-17
Just installed a fresh Ubuntu 13.04 going up from 12.04, similar kvm-qemu and bridge setup, perhaps. The VMs are on raw VG-LVM images. I will watch out for a panic. Here's the bridge setup (that worked reliably in 12.04) and was copied over to 13.04, so far so good...

```
~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto p4p1
iface p4p1 inet manual

auto br0
iface br0 inet static
	address 192.168.33.2
	netmask 255.255.255.0
	network 192.168.33.0
	broadcast 192.168.33.255
	gateway 192.168.33.1
	up ip addr add 192.168.133.2/24 brd 192.168.133.255 dev br0 label br0:0
	dns-nameservers 184.16.4.22 184.16.33.54
	bridge_ports p4p1
        bridge_stp on
        bridge_maxwait 0
        bridge_fd 0
```

12.04 may be more stable than 13.04, but in this case there are some features I wanted to try out, namely Spice, which seem to be improved in 13.04

I have separated the LVM's into individual Volume Groups: a 1 TB disk contains /boot and RAID1-swap, plus RAID-1 MD0 and MD1 for system volume groups: VG0 contains LV's for / and /home, VG1 contains LVs for the VM disk images. This way I can run the normal installer from a thumb and use the stock partitioner to reset /, /boot, swap while leaving /home and the VM images untouched. Then it's not so hard to change distros.

---

