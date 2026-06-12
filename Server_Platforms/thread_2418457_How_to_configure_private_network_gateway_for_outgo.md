---
title: "How to configure private network gateway for outgoing traffic"
date: 2019-05-07
forum: Server Platforms
---

### Post by plangeard on 2019-05-07
I have 2 servers (ubuntu 18.04) in  a private network, one has a public ip:

  
[LIST]
[*]"lb" has 2 interfaces with 1 public ip and 1 private ip ( ens3 51.83.14.172 and ens4 192.168.0.1)


[*]"node01" has 1 private ip (ens1 192.168.0.12)

[/LIST]
  I want to route the outgoing traffic of node1 by "lb"

  node01 ens4 => lb ens4 => lb ens 3 => internet

  Here is my configuration but I can ping internet from node01
  server lb

[HTML]
ifconfig
ens3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 51.83.14.172  netmask 255.255.255.255  broadcast 0.0.0.0
        inet6 fe80::f816:3eff:fe50:df72  prefixlen 64  scopeid 0x20<link>
        ether fa:16:3e:50:df:72  txqueuelen 1000  (Ethernet)
        RX packets 164514  bytes 19045889 (19.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 149861  bytes 10579204 (10.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

ens4: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.1  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::f816:3eff:fe18:e04  prefixlen 64  scopeid 0x20<link>
        ether fa:16:3e:18:0e:04  txqueuelen 1000  (Ethernet)
        RX packets 2947  bytes 411124 (411.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3766  bytes 269126 (269.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 533  bytes 63226 (63.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 533  bytes 63226 (63.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

/etc/netplan/50-cloud-init.yaml

network:
    version: 2
    ethernets:
        ens3:
            dhcp4: true
        ens4:
            addresses: [192.168.0.1/24]
            nameservers:
              addresses: [8.8.8.8,8.8.4.4]
            dhcp4: no
[/HTML]


server node01


[HTML]

ifconfig
ens4: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.12  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::f816:3eff:fea4:3df7  prefixlen 64  scopeid 0x20<link>
        ether fa:16:3e:a4:3d:f7  txqueuelen 1000  (Ethernet)
        RX packets 3588  bytes 283573 (283.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1628  bytes 282583 (282.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 522  bytes 41957 (41.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 522  bytes 41957 (41.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


/etc/netplan/50-cloud-init.yaml

network:
    version: 2
    ethernets:
        ens4:
            addresses: [192.168.0.12/24]
            nameservers:
              addresses: [8.8.8.8]
            dhcp4: no
            gateway4: 192.168.0.1
[/HTML]

---

### Post by TheFu on 2019-05-07
Did you enable routing in the kernel?  I don't have 18.04 and don't use netplan. Sorry.
Ars has a step-by-step guide for using Ubuntu server as a router from a few years ago. It isn't for 18.04, so you'll need to translate the networking parts.

---

### Post by SeijiSensei on 2019-05-07
You need to enable ipv4 packet forwarding in the kernel, and also add an iptables rules to "masquerade" your internal network using your public IP.  To fix forwarding, edit as root /etc/sysctl.conf on the lb machine and remove the hash tag at the beginning of 

```
net.ipv4.ip_forwarding=1
```

Reboot.  Now enter this command on lb:

```
sudo iptables -t nat -A POSTROUTING -j MASQUERADE
```

See if node01 can now ping Internet addresses like 8.8.8.8.  If so, you can have it run automatically at boot like this:

```

sudo echo '/sbin/iptables -t nat -A POSTROUTING -j MASQUERADE' >> /etc/rc.local
sudo chmod u+x /etc/rc.local

```

Now you should have an executable file called /etc/rc.local.  That will be run at the end of the boot sequence. (There doesn't need to be a "sudo" in rc.local since it runs with root privileges by default.)

---

