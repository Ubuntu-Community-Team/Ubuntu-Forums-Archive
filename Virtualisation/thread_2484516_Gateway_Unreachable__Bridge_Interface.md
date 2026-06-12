---
title: "Gateway Unreachable : Bridge Interface"
date: 2023-03-01
forum: Virtualisation
---

### Post by kalidassan-dinesh on 2023-03-01
Hello Folks,

Once the netplan for bridge interface is applied , the gateway becomes unreachable. In the absence of bridge interface (physical interface) the  gateway was reachable.

This is VM hosted in ESXi.

```

lsb_release -a

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic
```


```


/etc/netplan/

network:
  version: 2
  renderer: networkd

  ethernets:
    ens160:
      dhcp4: false
      dhcp6: false
      #addresses: [10.86.185.55/25]
      #gateway4: 192.
      #mtu: 1500
      #nameservers:
      #  addresses: [8.8.8.8]

  bridges:
    br0:
      interfaces: [ens160]
      addresses: [10.86.185.55/25]
      gateway4: 10.86.185.1
      mtu: 1500
      nameservers:
        addresses: [8.8.8.8]
      dhcp4: no
      dhcp6: no
      macaddress: 88:d7:f6:78:91:72
```

---

### Post by DuckHook on 2023-03-01
*Thread moved to **Virtualisation** as the more appropriate forum.*

---

### Post by MAFoElffen on 2023-03-02
<Is both a virtualization and (virtual) networking question>

Why are you applying a bridged virt switch to a VMware ESXi hosted VM Guest? That would get you to whatever virtual switched network you applied to the ESXi Guest. 

Is that also Bridged? Are you doing nested virtuals hosted on that VM Guest?

Asking both those questions to see if you are trying to get a nested virtual machined through two bridges to the network of the ESXi Host. Otherwise, all that in the NetPlan is not really needed right? nothing. It is then, just going to get a nested VM to whatever virtual network of the nested VM's VM host, which just happens to be a VM Guest to ESXi...
 
If doing nested Virt's: To get that to work easily, add another NIC to the VM config and apply that bridge to the second Ethernet device. Setup the first Ethernet device as another static IP (like you did for that first one). Using two Ethernet devices you then have one for the host, and one for the bridge...

In reality, the bridge doesn't need a static IP address (because a bridge is pass-through), but I set it up with one just like you did, for diagnostics and accounting.

---

