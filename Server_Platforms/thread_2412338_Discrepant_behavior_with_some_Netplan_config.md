---
title: "Discrepant behavior with some Netplan config"
date: 2019-02-11
forum: Server Platforms
---

### Post by mc-rpg on 2019-02-11
I'm running an ubuntu server 18.04 under VirtualBox with 2 network adapters: NAT Network (enp0s3) and a Host-only Adapter (enp0s8). I use the NAT to access the internet and the Host-only Adapter to SSH in from my local machine. Using the following netplan config gives me unstable results, sometimes I do get internet on enp0s3 and others I don't. When I shutdown the server, close vb and start it again I almost never get internet on this interface. But if I just restart netplan a couple of times or just the virtualized server (leaving virtualbox running) I do sometimes get internetwork.
```
network:
    ethernets:
        enp0s3:
            addresses: [10.0.0.200/24,]
            dhcp4: no
            dhcp6: no
            gateway4: 10.0.0.1
            nameservers:
                addresses: [8.8.8.8, 8.8.4.4]
        enp0s8:
            addresses: [192.168.1.2/24,]
            dhcp4: no
            dhcp6: no
            gateway4: 192.168.1.1
            nameservers:
                addresses: [8.8.8.8, 8.8.4.4]
    version: 2
```

However, after changing the netplan config to the following always results in me being able to access the internet from the natted interface and able to SSH in from the other int:
```
network:
    ethernets:
        enp0s3:
            addresses: [10.0.0.200/24,]
            dhcp4: no
            dhcp6: no
            #gateway4: 10.0.0.1
            nameservers:
                addresses: [8.8.8.8, 8.8.4.4]
            routes:
            - to: 0.0.0.0/0
              via: 10.0.0.1
        enp0s8:
            addresses: [192.168.1.2/24,]
            dhcp4: no
            dhcp6: no
            #gateway4: 192.168.1.1
            nameservers:
                addresses: [8.8.8.8, 8.8.4.4]
            routes:
            - to: 0.0.0.0/0
              via: 192.168.1.1/24  
    version: 2
```

Can someone tell me what is the difference between one configuration and the other? To me they seem equivalent of each other.

This is the natnetwork:
```
$ VBoxManage natnetwork list
NAT Networks:

Name:        natnet1
Network:     10.0.0.0/24
Gateway:     10.0.0.1
IPv6:        No
Enabled:     Yes
```

UPDATE: this didn't actually solve my problem, I still get intermitent internet access via the natted interface.

---

