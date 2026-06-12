---
title: "Networking fails to start"
date: 2009-12-10
forum: Virtualisation
---

### Post by satimis on 2009-12-10
Hi folks,


KVM
host - Debian 5.0
VM (guest) - Ubuntu 9.10

/etc/network/interfaces
```


# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static

        address         192.168.0.30
        netmask         255.255.255.0
        network         192.168.0.0
        broadcast       192.168.0.255
        gateway         192.168.0.1
        bridge_ports    eth0
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stp      off

```


$ sudo /etc/init.d/networking restart```

 * Reconfiguring network interfaces...                                     * if-up.d/mountnfs[eth0]: waiting for interface br0 before doing NFS mounts
SIOCSIFADDR: No such device
br0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
br0: ERROR while getting interface flags: No such device
br0: ERROR while getting interface flags: No such device
Failed to bring up br0.

```

Please advise how to fix the problem.

TIA

B.R.
satimis

---

### Post by Druke on 2009-12-10
is this the networking on the guest or the host? I am assuming it's the host that wont launch the bridge.

make sure the vm host has bridge-utils installed

```
sudo apt-get install bridge-utils
```

---

### Post by satimis on 2009-12-10
> **Druke said:**
> is this the networking on the guest or the host? I am assuming it's the host that wont launch the bridge.

make sure the vm host has bridge-utils installed

```
sudo apt-get install bridge-utils
```

Hi Druke,

Thanks.  Your advice gives me a hint.  

VM host already has bridge-utils installed.  But VM guest also needs it.  After having it installed on VM guest my problem is solved.

B.R.
satimis

---

### Post by Druke on 2009-12-10
glad to help!

I'm a bit curious as to why the guest needs a bridged connection, (nested vms perhaps?) but oh well, problem solved.

---

### Post by satimis on 2009-12-11
> **Druke said:**
> glad to help!

I'm a bit curious as to why the guest needs a bridged connection, (nested vms perhaps?) but oh well, problem solved.
Hi Druke,

I'm also at a lost of this discovery.  There are several VMs on this Virtual Machine running for several months.  I checked the documents re their installation and couldn't find record of installing bridge-utils.

It took me couple days to discover this problem.

B.R.
satimis

---

### Post by pp. on 2009-12-11
My Debian guest also failed to detect its network cards. I am running VirtualBox in an Ubuntu 9.10 host. The failure occurred after upgrading Virtual Box. Unfortunately, I can't remember which version of VirtualBox was the last one which worked.

I kind of solved my problem by installing VMWare Player instead of VirtualBox.

---

### Post by satimis on 2009-12-11
> **pp. said:**
> My Debian guest also failed to detect its network cards. I am running VirtualBox in an Ubuntu 9.10 host. The failure occurred after upgrading Virtual Box. Unfortunately, I can't remember which version of VirtualBox was the last one which worked.

I kind of solved my problem by installing VMWare Player instead of VirtualBox.
I have no experience on VitualBox.  I ran Xen(Open Source), Vserver, OpenVZ, VMWare(Free edition) before.  My opinion is;
If not looking for full virtualization better use Xen or VServer or OpenVZ.  Their guests share kernel saving lot of space, most suitable for server.  Unless you need to run multi desktops on the same PC.

satimis

---

