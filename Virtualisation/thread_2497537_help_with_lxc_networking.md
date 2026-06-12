---
title: "help with lxc networking"
date: 2024-05-09
forum: Virtualisation
---

### Post by coolmike8902 on 2024-05-09
I made a custom configuration in order to have a larger storage pool. Here is the profile I made:

config: {}
description: B970Pro LXD profile
devices:
  eth0:
    nictype: bridged
    parent: lxdbr0
    type: nic
  root:
    path: /
    pool: B970Pro
    type: disk
name: B970Pro
used_by:
- /1.0/instances/handy-pipefish
- /1.0/instances/faithful-bedbug
- /1.0/instances/stable-ostrich

I am able to ping the instances from the host, but not outside of the host. If I perform: lxc network show lxdbr0, I get this:
config:
  ipv4.address: 10.93.5.1/24
  ipv4.nat: "true"
  ipv4.routes: 10.122.135.135/32
  ipv6.address: fd42:22b0:3deb:3bc6::1/64
  ipv6.nat: "true"
description: ""
name: lxdbr0
type: bridge
used_by:
- /1.0/instances/handy-pipefish
- /1.0/instances/stable-ostrich
- /1.0/profiles/B970Pro
- /1.0/profiles/default
managed: true
status: Created
locations:
- none

Can someone please help me troubleshoot this issue?

Thanks.

---

### Post by TheFu on 2024-05-09
please edit and wrap output in code-tags to retain indentation. Make it easier for someone to help you, if they can.  Show the exact commands used - many people don't touch this stuff often enough to remember how to show details.

I've never used lxdbr0 nor have I added any ipv[46].* settings for LXD.

Since I'm using a separate bridge, not the one created, and I seldom touch any networking once the *lxd init* is done. It is listed as unmanaged. Doubt I can help your question.  A few years ago, I set the defaults to use a bridge I'd manually created and never touched it again.  Inside each container, setup a static IP.  I'm running 7 lxc containers that way.  Also, I disable all IPv6 on my hosts.  I started doing this when IPv6 started being enabled by default.  After attending a few IPv6 training classes, I decided I didn't know how to secure it, so it was best to just disable it for my needs.

---

### Post by ian-weisser on 2024-05-09
LXD bridging is a two step process.

1) Netplan (create the bridge and connect it to the real LAN)
2) LXD Profile (use the bridge)

If you skip step 1, then LXD creates a bridge which cannot talk outside of the host because it's not connected to the LAN.

I wrote an example of a simple working setup last week at [https://ubuntuforums.org/showthread.php?t=2497365&p=14188192#post14188192](https://ubuntuforums.org/showthread.php?t=2497365&p=14188192#post14188192)

---

### Post by coolmike8902 on 2024-05-16
Forgive the late reply. I will try and figure out how to do that. Thanks.

---

### Post by coolmike8902 on 2024-05-17
I had it working, and now it doesn't. I believe I have followed your instructions, so I'm at a loss. Here's my host netplan:

```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp7s0:
      dhcp4: no
    eno2:
      dhcp4: no
    eno1:
      dhcp4: no
    enp9s0f1:
      dhcp4: no
    enp9s0f0:
      dhcp4: no
  bridges:
    bridge0:
        addresses:

```

and then the profile I'm using:

```
config: {}
description: B970Pro LXD profile
devices:
  eth0:
    name: eth0
    nictype: bridged
    parent: bridge0
    type: nic
```

and lastly the netplan on the container:

```
network:
    version: 2
    ethernets:
        eth0:
            dhcp4: true


```

Am I missing something? Thanks.

---

### Post by Tadaen_Sylvermane on 2024-05-17
```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp7s0:
      dhcp4: no
    eno2:
      dhcp4: no
    eno1:
      dhcp4: no
    enp9s0f1:
      dhcp4: no
    enp9s0f0:
      dhcp4: no
  bridges:
    bridge0:
        addresses:
```

You need to assign the bridge to interfaces, and give it a static ip if you need. Here is my netplan from my home server. Use it as a template / example as needed.

```
network:
 version: 2
 renderer: networkd
 ethernets:
  enp4s0:
   dhcp4: false
   dhcp6: false
 bridges:
  br0:
   dhcp4: false
   dhcp6: false
   interfaces: [enp4s0]
   addresses: [192.168.1.2/24]
   gateway4: 192.168.1.240
   nameservers:
    addresses: [8.8.8.8, 8.8.4.4]
```

Once you have the bridge properly configured on the host you can re-run ```
lxd init
``` and specify the bridge, in my example ```
br0
``` At this point they will be on the lan like any other physical machine.

---

### Post by TheFu on 2024-05-18
My stance is, if it is important enough to have a container, then it is important enough to have a static IP.
I'd never use DHCP for a container.

---

