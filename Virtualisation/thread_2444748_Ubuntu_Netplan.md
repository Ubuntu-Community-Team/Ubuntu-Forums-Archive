---
title: "Ubuntu Netplan"
date: 2020-06-03
forum: Virtualisation
---

### Post by khanblr on 2020-06-03
Hello experts,

Trying to create a bridge adapter using netplan for deploying KVM.

```
Current scenario, 4 x 10gig interface 
2 x 10 gig -- bond0
2 x 10 gig -- bond1

1 x bond0 - bond0.3700 ---> Vlan 3700
1 x bond1 - bond1.3701 -->  Vlan 3701

wanted to create bridge adapters, (br0 & br1 ) Could anyone provide some solution.

Please find the current configuration ( 50-cloud-init.yaml )

network:
    bonds:
        bond0:
            interfaces:
            - enp175s0f0
            - enp175s0f1
        parameters:
            mode: active-backup

        bond1:
            interfaces:
            - enp176s0f0
            - enp176s0f1
        parameters:
            mode: active-backup
    ethernets:
        enp175s0f0: {}
        enp175s0f1: {}
        enp176s0f0: {}
        enp176s0f1: {}
    version: 2

    vlans:
        bond0.3700
            addresses:
            - 10.0.0.10
            gateway4: 10.0.0.1
            id: 3700
            link: bond0
            nameservers:
                addresses:
                - 10.0.0.125
                search:
                - testlab.com

        bond1.3701
            addresses:
            - 10.0.1.10
            gateway4: 10.0.1.1
            id: 3701
            link: bond1
            nameservers: {}
---------------------------------------------------------------
```

---

### Post by Tadaen_Sylvermane on 2020-06-03
Don't know much about netplan, and I don't use anything beyond basic static ip with bridges. I'm fairly sure things need to be defined in order, but not positive. As such this is how I would write it. I'm taking a shot at the vlan part from this link. [https://netplan.io/examples](https://netplan.io/examples)  Also I'm not sure if 24 is the proper netmask for you. You need to determine that.

```
network:
 version: 2
 renderer: networkd
 ethernets:
  enp175s0f0:
   dhcp4: false
  enp175s0f1:
   dhcp4: false
  enp176s0f0:
   dhcp4: false
  enp176s0f1:
   dhcp4: false
 bonds:
  bond0:
   interfaces: [enp175s0f0, enp175s0f1]
   dhcp4: false
   parameters:
    mode: active-backup
  bond1:
   interfaces: [enp176s0f0, enp176s0f1]
   dhcp4: false
   parameters:
    mode: active-backup
 bridges:
  br0:
   interfaces: [bond0]
    dhcp4: false
  br1:
   interfaces: [bond1]
    dhcp4: false
 vlans:
  vlan0:
   id: 3700
   link: [br0]
   addresses: [10.0.0.10/24]
   gateway4: 10.0.0.1
   nameservers:
    addresses: [10.0.0.125]
    search: [testlab.com]
  vlan1:
   id: 3701
   link: [br1]
   addresses: [10.0.1.10/24]
   gateway4: 10.0.1.1
```

Again I am no expert.

---

### Post by wildmanne39 on 2020-06-03
*Thread moved to **Virtualisation for a more appropriate fit**.*

---

### Post by khanblr on 2020-06-04
Hello [[COLOR=#000000]Tadaen_Sylvermane[/COLOR]]("https://ubuntuforums.org/member.php?u=1914514")

Thank you so much, yes it did work.

:guitar:

---

