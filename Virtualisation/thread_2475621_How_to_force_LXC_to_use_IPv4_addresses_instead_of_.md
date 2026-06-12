---
title: "How to force LXC to use IPv4 addresses instead of IPv6"
date: 2022-06-02
forum: Virtualisation
---

### Post by antoman.san on 2022-06-02
Hi, I'm trying to install a VM under LXC, using LXD frontend.

I've followed the instructions on the LXD site, and I managed to create an empty VM and installing Win11 on it.
The problem is that the VM uses IPv6 and not IPv4, so network connection doesn't work properly.

```
lxc list
+-------+---------+------+------+-----------------+-----------+
| NAME  |  STATE  | IPV4 | IPV6 |      TYPE       | SNAPSHOTS |
+-------+---------+------+------+-----------------+-----------+
| win11 | STOPPED |      |      | VIRTUAL-MACHINE | 0         |
+-------+---------+------+------+-----------------+-----------+

lxc start win11 --console=vga

lxc list
+-------+---------+------+----------------------------------------------+-----------------+-----------+
| NAME  |  STATE  | IPV4 |                     IPV6                     |      TYPE       | SNAPSHOTS |
+-------+---------+------+----------------------------------------------+-----------------+-----------+
| win11 | RUNNING |      | fd42:79f8:8fd2:a2d:216:3eff:fe09:f244 (eth0) | VIRTUAL-MACHINE | 0         |
+-------+---------+------+----------------------------------------------+-----------------+-----------+
```

I'm under Ubuntu 22:04 classic environment.

Is here someone who can help me to configure LXC in order to force use of IPv4 for all VM and containers? ;)

---

### Post by TheFu on 2022-06-02
Set the IPv4 address you want in the container?  Is this a trick question?

BTW, you aren't using LXC with a Windows guest. That is definitely NOT a Linux Container. It is likely using a hypervisor like kvm-qemu. I typically use virt-manager to setup and install whole VMs on KVM.  Virt-manager is very much like the GUI for virtualbox or VMware Workstation, just with more enterprise features and almost too much flexibility. Normal people who need a VM GUI would probably like "Multipass".  [https://ubuntu.com/server/docs/virtualization-multipass](https://ubuntu.com/server/docs/virtualization-multipass)

Also, I've never let LXD control KVM and wouldn't know how to connect to a client that requires a GUI to be useful like Windows.

For non-Windows systems, i.e. Linux containers, you can setup the networking however you like in general. I have a bridge (created outside lxd) that I've setup as the default network device for lxd containers to use.  This bridge provides containers with access to the LAN DHCP server, until I can get logged in and manually set a static IP in the normal way for the specific distro.  For Ubuntu Servers, that is usually in the netplan YAML files under /etc/netplan/.

```
$ lxc network list
+--------+----------+---------+-------------+---------+
|  NAME  |   TYPE   | MANAGED | DESCRIPTION | USED BY |
+--------+----------+---------+-------------+---------+
| br0    | bridge   | NO      |             | 4       |
+--------+----------+---------+-------------+---------+
| enp3s0 | physical | NO      |             | 0       |
+--------+----------+---------+-------------+---------+
| lxdbr0 | bridge   | YES     |             | 0       |
+--------+----------+---------+-------------+---------+
| br1    | bridge   | NO      |             | 0       |
+--------+----------+---------+-------------+---------+
```
As you can see, I ignore the lxd-bridge and virt-manager bridge under lxd.  there are a number of **lxc network** commands. The manpage was sufficient for me to figure out it a few years ago when I set this all up.  The available manpages are:
```
$ man lxc.network{tab}{tab}
lxc.network                 lxc.network.detach          lxc.network.list-leases
lxc.network.attach          lxc.network.detach-profile  lxc.network.rename
lxc.network.attach-profile  lxc.network.edit            lxc.network.set
lxc.network.create          lxc.network.get             lxc.network.show
lxc.network.delete          lxc.network.list            lxc.network.unset

```
though, like many manpages, they aren't all as clear as we'd like.

---

