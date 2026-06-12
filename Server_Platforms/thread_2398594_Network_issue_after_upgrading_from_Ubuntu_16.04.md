---
title: "Network issue after upgrading from Ubuntu 16.04"
date: 2018-08-14
forum: Server Platforms
---

### Post by im0nkey on 2018-08-14
Hi everyone,

this is my second post here, so please be lenient to me. :-) I researched for hours but can't find a hint how to proceed... :-(

A few weeks ago I upgraded my KVM Server from Ubuntu Server 16.04 to 18.04.01. Now I wanted to change something regarding my network configuration and this issue occurred. I already know, that Bionic Beaver uses netplan instead of the old ifupdown. If I do a fresh install, i.e. on a VM, the network is automatically configured and a Yaml-Script is generated. Unfortunately this did not happen during my upgrade process. Under /etc/netplan/ is no Yaml-Script. So to configure my network correctly, including my planned changes, I just created a "50-cloud-init.yaml" file, withe following content:

```

network:  
version: 2
  ethernets:
    eno1:
      addresses: []
      dhcp4: true
      dhcp6: true
      optional: true
    enp7s0f0:
      addresses: []
      dhcp4: true
      dhcp6: true
      optional: true
    enp7s0f1:
      addresses: []
      dhcp4: true
      dhcp6: true
      optional: true
    enp8s0f0:
      addresses: []
      dhcp4: true
      dhcp6: true
      optional: true
    enp8s0f1:
      addresses: []
      dhcp4: true
      dhcp6: true
      optional: true

```


The first error I noticed, was during boot:

```

[FAILED] Failed to start resolvconf-pull-resolved.service.
See 'systemctl status resolvconf-pull-resolved.service' for details.

```

I'm not sure if this is related to my issue. Anyway the problem now is, I don't have any network access at all. I can't ping the server and the server can't ping anything, either. Oddly enough is that DNS lookups seem to work, but this could also have been read from the cache, I assume. The output from 'systemctl status resolvconf-pull-resolved.service' is:

```

 resolvconf-pull-resolved.service
   Loaded: loaded (/lib/systemd/system/resolvconf-pull-resolved.service; static; vendor preset: enabled)
   Active: failed (Result: start-limit-hit) since Tue 2018-08-14 21:57:55 CEST; 8min ago
  Process: 1606 ExecStart=/bin/sh -c cat /run/systemd/resolve/stub-resolv.conf | /sbin/resolvconf -a systemd-resolved (code=exited, status=0/SUCCESS)
 Main PID: 1606 (code=exited, status=0/SUCCESS)


Aug 14 21:57:59 KVM-Server systemd[1]: Failed to start resolvconf-pull-resolved.service.
Aug 14 21:57:59 KVM-Server systemd[1]: resolvconf-pull-resolved.service: Start request repeated too quickly.
Aug 14 21:57:59 KVM-Server systemd[1]: resolvconf-pull-resolved.service: Failed with result 'start-limit-hit'.
Aug 14 21:57:59 KVM-Server systemd[1]: Failed to start resolvconf-pull-resolved.service.
Aug 14 21:58:00 KVM-Server systemd[1]: resolvconf-pull-resolved.service: Start request repeated too quickly.
Aug 14 21:58:00 KVM-Server systemd[1]: resolvconf-pull-resolved.service: Failed with result 'start-limit-hit'.
Aug 14 21:58:00 KVM-Server systemd[1]: Failed to start resolvconf-pull-resolved.service.
Aug 14 21:58:00 KVM-Server systemd[1]: resolvconf-pull-resolved.service: Start request repeated too quickly.
Aug 14 21:58:00 KVM-Server systemd[1]: resolvconf-pull-resolved.service: Failed with result 'start-limit-hit'.
Aug 14 21:58:00 KVM-Server systemd[1]: Failed to start resolvconf-pull-resolved.service.

```

I'm able to start the service manually, but this does not fix the issue. The output of 'ifconfig' is:

```

bond0: flags=5123<UP,BROADCAST,MASTER,MULTICAST>  mtu 1500
        ether 9e:8e:54:cd:c8:a0  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.100  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fda1:1a78:799b:0:1a66:daff:fe10:6564  prefixlen 64  scopeid 0x0<global>
        inet6 fda1:1a78:799b::9fe  prefixlen 128  scopeid 0x0<global>
        inet6 fe80::1a66:daff:fe10:6564  prefixlen 64  scopeid 0x20<link>
        ether 18:66:da:10:65:64  txqueuelen 1000  (Ethernet)
        RX packets 4754  bytes 6467212 (6.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1873  bytes 178961 (178.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf7e00000-f7e20000


enp7s0f0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 00:24:81:82:dc:89  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 19  memory 0xf7b20000-f7b40000


enp7s0f1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 00:24:81:82:dc:88  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 18  memory 0xf7b00000-f7b20000


enp8s0f0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 00:24:81:82:dc:8b  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 17  memory 0xf7920000-f7940000


enp8s0f1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 00:24:81:82:dc:8a  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xf7900000-f7920000

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 156  bytes 16765 (16.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 156  bytes 16765 (16.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


macvlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.100  netmask 255.255.255.0  broadcast 0.0.0.0
        inet6 fe80::d055:36ff:fe7f:b726  prefixlen 64  scopeid 0x20<link>
        inet6 fda1:1a78:799b:0:d055:36ff:fe7f:b726  prefixlen 64  scopeid 0x0<global>
        inet6 fda1:1a78:799b:0:c599:91b3:35d1:1d14  prefixlen 64  scopeid 0x0<global>
        ether d2:55:36:7f:b7:26  txqueuelen 1000  (Ethernet)
        RX packets 258  bytes 68181 (68.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 13  bytes 1142 (1.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


macvtap0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::5054:ff:fe77:b487  prefixlen 64  scopeid 0x20<link>
        ether 52:54:00:77:b4:87  txqueuelen 500  (Ethernet)
        RX packets 260  bytes 68331 (68.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 67  bytes 6710 (6.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



macvtap1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::5054:ff:fe70:9734  prefixlen 64  scopeid 0x20<link>
        ether 52:54:00:70:97:34  txqueuelen 500  (Ethernet)
        RX packets 3817  bytes 6384880 (6.3 MB)


```

It looks correctly for me and that is even more strange. I tried some other commands to get reports, but it did not lead me to anything and the post is already long enough. I hope someone is able to help me. I will gladly provide any log or output requested.

If I delete the Yaml-Script, everything works again, except that I want to change something and I can't.

Thank you in advance.

Greetings
Sebastian

P.S.: eno1 is the only real device I'm using.

---

### Post by wildmanne39 on 2018-08-14
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by RR123RR on 2018-12-10
Ever found a solution for the resolvconf-pull-resolved.service failing on start?

I have this on Ubuntu server 18.04.1 with netplan, doesn't seem to cause actual issues once booted, but for virtual appliances it makes for a needlessly noisy/scary startup.

---

