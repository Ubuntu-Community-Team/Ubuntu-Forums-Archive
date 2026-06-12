---
title: "KVM Host with multiple static IPs and netplan, ubuntu 18.04"
date: 2019-02-06
forum: Server Platforms
---

### Post by richcoding on 2019-02-06
I have dedicated server with Ubuntu 18.04 headless, tha is going to be used as KVM Host server. The server was assigned with several static IPv4 addresses. My plan is to use one static IPv4 for Host server and rest IPv4 adresses for guest machines.

Server has two ethernet interfaces now bonded together.

I am looking for help how to define bridges/interfaces that will be used in every guest machine. How to configure netplan on host machine to provide interfaces for KVM guest setup.

here are details: server has several IP assigned:
xx.xx.xx.130/25
xx.xx.xx.131/25
xx.xx.xx.132/25
...
xx.xx.xx.137/25


I want to set up xx.xx.xx.130/25 for HOST machine (dedicated server)
and rest for individual guest machines (KVM guests)


My actual netplan config is this


01-necfg.yaml
===============
```
# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
            dhcp4: false
            optional: true
    eno2:
            dhcp4: false
            optional: true
           

```

02-bondings.yaml
================
```
network:
    version: 2
    renderer: networkd
    bonds:
        bond0:
            interfaces: [eno1, eno2]
            addresses: 
              - xx.xx.xx.130/25
              - xx.xx.xx.131/25
              - xx.xx.xx.132/25
              - xx.xx.xx.133/25
              - xx.xx.xx.134/25
              - xx.xx.xx.135/25
              - xx.xx.xx.136/25
              - xx.xx.xx.137/25
              - 2...:....:....::2/64  
            gateway4: xx.xx.xx.129
            gateway6: 2xxx:xxx:xxx::1
            parameters:
                mode: 802.3ad
            nameservers:
                search: [static.mmmmmmmmmm.net]
                addresses: 
                  - nn.nn.nn.nn
                  - n2.n2.n2.n2
                  - 2yyy:yyy:y:yy::3
                  - 2yyy:yyy:y:y::5
            dhcp4: false
            optional: true





```

---

### Post by darkod on 2019-02-06
Don't assign all IPs to the host bond. Only the one IP that you want to use for it.

After creating the bond you will also need to create a bridge. When creating the guest VMs you will assign them to use the bridge connection. That way it will simulate as if the guest VM is connected by cable same like the physical host. And assigning static IP to each of the guest VMs will work.

---

### Post by richcoding on 2019-02-06
Thank you!
Richard

---

### Post by phillw on 2019-02-15
With my KVM instance you also need to assign virtual MAC addresses as well :)  I use an OVH server.

Regards,

Phill.

---

