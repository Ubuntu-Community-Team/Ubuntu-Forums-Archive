---
title: "How to configure a public IP address on LXD guest"
date: 2017-01-24
forum: Virtualisation
---

### Post by itcrowdsource on 2017-01-24
Hi,

I'm struggling to attach a public IP address to a LXD guest system. Does anyone has experience how to set this up properly? I'm running Ubuntu 16.04 with LXD version 2.0.8-0ubuntu1~ubuntu16.04.2 500 and also installed bridge-utils to create bridges.

I've succesfully created a bridge on the host which is properly routed/reachable over te internet.

This is the config on my host:
```

auto eth0:1
iface eth0:1 inet manual


auto br2
iface br2 inet static
    address x.x.x.x
    netmask 255.255.255.0
    network x.x.x.0
    broadcast x.x.x.255
    gateway x.x.x.254
    bridge_ports eth0:1
    bridge_ports wan_phy #I've also tried this settings without any results
    bridge_stp off
    bridge_fd 0
    bridge_maxwait 0
```

After that, I've created a profile that connects the guest nic to the host (I've tried several nictypes: bridged, macvlan, physical and p2p):```


config:
  raw.lxc: lxc.aa_allow_incomplete=1
description: ""
devices:
  eth0:
    name: eth0
    nictype: macvlan
    parent: br2
    type: nic
  eth1:
    name: eth1
    nictype: bridged
    parent: br0
    type: nic

On the guest:

auto eth1
iface eth1 inet static
    address 192.x.x.x
    netmask 255.255.255.0
    network 192.x.x.0
    broadcast 192.x.x.255


auto eth0
iface eth0 inet static
    address x.x.x.x
    netmask 255.255.255.0
    network x.x.x.0
    broadcast x.x.x.255
    gateway x.x.x.254
```

With some nictype configurations I'm able to ping the public IP on the host. But The public IP of the guest is unreachable over te internet.

Hope anybody has a good suggestion how to publish a public IP properly on a VM?

Many thanks in advance!

---

### Post by SeijiSensei on 2017-01-24
Did your ISP allocate an IP subnet to your account so you have multiple public addresses available?

---

### Post by itcrowdsource on 2017-01-24
Hi SeijiSensei, yes I do have multiple IP addresses available. I also managed to configure these addresses on the physical interface. But I can't get it working on the guest itself.
[COLOR=#000000]**_SeijiSensei_**[/COLOR][COLOR=#000000]**_SeijiSensei_**[/COLOR]

---

### Post by SeijiSensei on 2017-01-24
Did you leave the address you want to use unallocated on the host machine?  It looks like you are using virtual interfaces like eth0:1 to assign the other IPs.  In a bridged arrangement, the VM appears to be on the same network as the host, so you cannot assign the same address to an interface on the host.

---

### Post by itcrowdsource on 2017-01-25
I've configured the host with a different public IP which is in the same subnet as the LXD guest. So my host is currently configured with two public IP's as follows:
The first public IP is by default provisioned to eth0 if I enroll a new server. I've also created a bridge for that interface (br1) which is currently not in use. 

Besides that I've configured a secondary virtual interface (eth0:1) which also has a bridge of its own (br2). The br2 interface is configured with one of the public IP addresses from a new IP block (different network range) that I got from my provider. I'm able to reach this public IP address on the br2 interface over the internet so routing/connection towards the host seems to be OK.

The guest system has another public IP address from the same IP block which is attached to the same br2 interface. I was thinking that if the public IP on br2 was reachable the secondary IP of the LXD guest should also reachable. But that isn't the case currently. Something on the host prohibits the further communication towards the LXD guest.

---

### Post by SeijiSensei on 2017-01-25
I've not used LXD, just VirtualBox. With that VM manager, configuring a VM's interface as bridged is handled entirely by VirtualBox.  I don't need to create a bridge interface on the host in advance.  Maybe you do, but maybe you don't?  My VM comes up with an eth0 interface with an address on the host's subnet.

If you can't work things out this way, you could go to a NAT arrangement with iptables tunnels from ports on the host back to ports on the guest.  That's nowhere near as flexible as using the bridge though.

---

### Post by itcrowdsource on 2017-01-27
I think this isn't related to LXD specifically but rather setting up a bridge properly. I'm going to try some other configuration options first.

---

### Post by itcrowdsource on 2017-01-28
I finally found the cause of the issue. It seemed that my ISP routes traffic to the main IP address of my server. I've enabled sysctl routing and added the appropriate routes towards the br1 interface which is being used by the guests. On the guest VM I've configured the gateway address pointing to the main IP of the host.
[COLOR=#000000]**_SeijiSensei_**[/COLOR]

---

