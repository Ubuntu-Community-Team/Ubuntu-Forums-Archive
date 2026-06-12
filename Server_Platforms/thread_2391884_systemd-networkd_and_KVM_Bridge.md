---
title: "systemd-networkd and KVM Bridge"
date: 2018-05-14
forum: Server Platforms
---

### Post by Doenerverkaufer on 2018-05-14
Hi everyone,

I'm pulling my hair out on this one... Trying to get a bridge with an additional IP on my server so that I can pull up some more VMs which can connect to the Internet through the Main Network but I can't get the bridge to work. Everytime I add "Bridge=br0" to my main network configuration the server doesn't come up again and systemd-networkd gets a "timeout" on the startup screen. Is there any way I can get you guys more info? Here is my config:

**/etc/systemd/network/10-enp0s31f6.network**
```

[Match]
Name=enp0s31f6


[Network]
Address=2a01:V6_IP::2/64
Gateway=195.XXX.XXX.129
Gateway=fe80::1
[FONT=Verdana]Bridge=br0[/FONT]


[Address]
Address=195.XXX.XXX.190
Peer=195.XXX.XXX.129/32

```

**/etc/systemd/network/20-bridge.network**
```

[Match]
Name=br0
[Network]
IPForward=yes
[Address]
Address=195.XXX.XXX.ADDITIONAL_IP/26
Gateway=195.XXX.XXX.129

```

[B]/etc/systemd/network/br0.netdev
[/B]```

[NetDev]
Name=br0
Kind=bridge
MACAddress=MAIN_NETWORKCARD_MAC

```

any help is appreciated :)

---

### Post by TheFu on 2018-05-14
Which Ubuntu release? Network settings have changed in the different releases.

---

### Post by Doenerverkaufer on 2018-05-14
18.04

---

### Post by mikewebb on 2018-05-18
Sounds like another case of Netplan sticks again.

For a quick on bridging using Netplan checkout 
[https://webby.land/2018/04/27/bridging-under-ubuntu-18-04/](https://webby.land/2018/04/27/bridging-under-ubuntu-18-04/)

---

### Post by mikewebb on 2018-05-19
I thought I would revisit this as the OP was also in relation to KVM bridging and I only covered the Netplan side.  Since installing 18.04, I've only been using LXD and bridging has been working fine.  So, I thought I would fire up VMM and create a KVM install and bind it to the bridge I had previously created (br0). 

When trying to define the br0 interface under Network Interface (QWMU/KVM Connection Details), all my other interfaces would show up for selection but not my br0.  I thought I would go ahead and create the VM anyway and when at step 5/5 of "Create a new virtual machine", then selected "Specify shared device name" and entered br0 and carried on installing.

I noticed a new vnet0appeared and my VM pulled an IP from my LAN DHCP server and I can ping out to the internet from the VM.

vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UNKNOWN group default qlen 1000
    link/ether fe:54:00:6e:11:c0 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fc54:ff:fe6e:11c0/64 scope link 
       valid_lft forever preferred_lft forever

The interface section of my domains xml looks like 
   <interface type='bridge'>
      <mac address='52:54:00:6e:11:c0'/>
      <source bridge='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>

I don't know why my vnet0 interface is state UNKNOWN while my veth devices used by containers (also using br0) show state UP.  I also don't know why VMM doesn't list br0 as an interface option either.  But either way, that's how I got a netplan bridge and a KVM VM to use it.

Hope that helps a bit more.

---

### Post by mikewebb on 2018-05-20
OK, just out of curiosity I created a simple .xml file with 

<network>
  <name>br0</name>
  <forward mode="bridge"/>
  <bridge name="br0" />
</network>

in it and did a net-define on it and started it.  br0 was now an option in the drop list mentioned before.  I continued to create the VM and it pulled an IP from my  DHCP server and could ping out.  Both vnet1 and vnet0 still show br0 state UNKNOWN.

I just realised I don't have bridge tools installed maybe this has something to do with that.  How was I even able to create the bridge with it?

Anyway, there you go

---

### Post by Doug S on 2018-05-20
There is a pending MP (Merge Proposal) for the Ubuntu Serverguide that deals with the re-write needed for netplan. Bridging is covered.

Why wasn't this done before the release of 18.04? Well, for my part of it, I didn't even know about the changes. Anyway, it should be published in a few days. Meanwhile you might be able to extract useful information from the source code (docbook markup).

References:
[https://code.launchpad.net/~powersj/serverguide/network-revamp-18.04/+merge/345788](https://code.launchpad.net/~powersj/serverguide/network-revamp-18.04/+merge/345788)
[https://bugs.launchpad.net/serverguide/+bug/1769007](https://bugs.launchpad.net/serverguide/+bug/1769007)

EDIT: bridge-utils is not required anymore. Extract from the referenced MP:```
> +      Before configuring a bridge you will need to install the <application>bridge-utils</application> package.  To install the

this isn't true; we no longer need bridge-utils and that may bring in ifupdown which we don't really want either.  Same goes for VLANs

```

---

