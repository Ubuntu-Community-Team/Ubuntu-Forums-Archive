---
title: "No network to guest OS - netplan / routing issue"
date: 2018-11-02
forum: Virtualisation
---

### Post by newbee112 on 2018-11-02
Hi, 
I have an issue that i have spent several hours on an i can not get it resolved. 
OS: ubuntu 18.04

I am unable to get virtual machines to get an assigned IP address, i am running KVM.
What i try to archive is pretty straight forward, spin up a debian 9 image in a VM with an IP address that i can SSH to from within my local network. 

/etc/libvirt/qemu/networks/br0.xml
```
 
<network>
  <name>br0</name>
  <uuid>a4fb5638-6c6c-4180-a288-4aff0ff34277</uuid>
  <forward mode='bridge'/>
  <bridge name='br0'/>
</network>

```

/etc/netplan/01-netcfg.yaml
```

network:
  version: 2
  renderer: networkd
  ethernets:
    enp4s0:
      dhcp4: true
  bridges:
    br0:
      dhcp4: yes
      interfaces:
        - enp4s0

```

newbee@server:/etc/netplan$ sudo netplan --debug  apply
```

** (generate:32201): DEBUG: 15:24:09.382: Processing input file //etc/netplan/01-netcfg.yaml..
** (generate:32201): DEBUG: 15:24:09.382: starting new processing pass
** (generate:32201): DEBUG: 15:24:09.382: enp4s0: setting default backend to 1
** (generate:32201): DEBUG: 15:24:09.382: br0: setting default backend to 1
** (generate:32201): DEBUG: 15:24:09.382: Generating output files..
** (generate:32201): DEBUG: 15:24:09.382: NetworkManager: definition enp4s0 is not for us (backend 1)
** (generate:32201): DEBUG: 15:24:09.383: NetworkManager: definition br0 is not for us (backend 1)
DEBUG:netplan generated networkd configuration exists, restarting networkd
DEBUG:no netplan generated NM configuration exists
DEBUG:Cannot replug virbr0: cannot read link /sys/class/net/virbr0/device: [Errno 2] No such file or directory: '/sys/class/net/virbr0/device'
DEBUG:netplan triggering .link rules for virbr0
DEBUG:device enp4s0 operstate is up, not replugging
DEBUG:netplan triggering .link rules for enp4s0
DEBUG:device br0 operstate is up, not replugging
DEBUG:netplan triggering .link rules for br0
DEBUG:Cannot replug virbr0-nic: cannot read link /sys/class/net/virbr0-nic/device: [Errno 2] No such file or directory: '/sys/class/net/virbr0-nic/device'
DEBUG:netplan triggering .link rules for virbr0-nic
DEBUG:device vnet0 operstate is unknown, not replugging
DEBUG:netplan triggering .link rules for vnet0
DEBUG:device lo operstate is unknown, not replugging
DEBUG:netplan triggering .link rules for lo

```

newbee@server:/etc/netplan$ sudo networkctl status -a

```

&#9679; 1: lo
       Link File: /lib/systemd/network/99-default.link
    Network File: n/a
            Type: loopback
           State: carrier (unmanaged)
         Address: 127.0.0.1
                  ::1


&#9679; 2: enp4s0
       Link File: /lib/systemd/network/99-default.link
    Network File: /run/systemd/network/10-netplan-enp4s0.network
            Type: ether
           State: carrier (configured)
            Path: pci-0000:04:00.0
          Driver: r8169
          Vendor: Realtek Semiconductor Co., Ltd.
           Model: RTL-8110SC/8169SC Gigabit Ethernet
      HW Address: 00:50:8d:bc:ac:79 (ABIT COMPUTER CORPORATION)


&#9679; 3: br0
       Link File: /lib/systemd/network/99-default.link
    Network File: /run/systemd/network/10-netplan-br0.network
            Type: ether
           State: routable (configured)
          Driver: bridge
      HW Address: 5a:e0:79:6e:d1:eb
         Address: 192.168.10.80
                  fe80::58e0:79ff:fe6e:d1eb
         Gateway: 192.168.10.1 (Synology Incorporated)
             DNS: 192.168.10.1


&#9679; 4: virbr0
       Link File: /lib/systemd/network/99-default.link
    Network File: n/a
            Type: ether
           State: no-carrier (unmanaged)
          Driver: bridge
      HW Address: 52:54:00:f9:73:e8
         Address: 192.168.122.1


&#9679; 5: virbr0-nic
       Link File: /lib/systemd/network/99-default.link
    Network File: n/a
            Type: ether
           State: off (unmanaged)
          Driver: tun
      HW Address: 52:54:00:f9:73:e8


&#9679; 9: vnet0
       Link File: /lib/systemd/network/99-default.link
    Network File: n/a
            Type: ether
           State: degraded (unmanaged)
          Driver: tun
      HW Address: fe:54:00:eb:ac:f6
         Address: fe80::fc54:ff:feeb:acf6

```

newbee@server:/etc/netplan$ ifconfig
```

br0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.10.80  netmask 255.255.255.0  broadcast 192.168.10.255
        inet6 fe80::58e0:79ff:fe6e:d1eb  prefixlen 64  scopeid 0x20<link>
        ether 5a:e0:79:6e:d1:eb  txqueuelen 1000  (Ethernet)
        RX packets 12405  bytes 2086058 (2.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 10779  bytes 17360328 (17.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


enp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether 00:50:8d:bc:ac:79  txqueuelen 1000  (Ethernet)
        RX packets 12554  bytes 2274857 (2.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 17495  bytes 17737100 (17.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 1351  bytes 83896 (83.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1351  bytes 83896 (83.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
        ether 52:54:00:f9:73:e8  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2  bytes 521 (521.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


vnet0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::fc54:ff:feeb:acf6  prefixlen 64  scopeid 0x20<link>
        ether fe:54:00:eb:ac:f6  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1  bytes 90 (90.0 B)
        TX errors 0  dropped 924 overruns 0  carrier 0  collisions 0

```

newbee@server:/etc/netplan$ virsh net-list

```

 Name                 State      Autostart     Persistent
----------------------------------------------------------
 br0                  active     yes           yes
 default              active     yes           yes

```

newbee@server:/etc/netplan$ virsh net-dhcp-leases br0

```

Expiry Time          MAC address        Protocol  IP address                Hostname        Client ID or DUID
-------------------------------------------------------------------------------------------------------------------

```

newbee@server:/etc/netplan$ virsh net-dhcp-leases default 

```

Expiry Time          MAC address        Protocol  IP address                Hostname        Client ID or DUID
-------------------------------------------------------------------------------------------------------------------

```



```


virsh # list
 Id    Name                           State
----------------------------------------------------
 4     hassio                         running

```

root@hassio:~# ip address show (manual typed, since i can only connect to host via virtual machine manager / remote desktop)
```

1:  lo: <LOOPBACK, UP, LOWER_UP> mtu 65536 qdisk noqueue state UNKNOWN group default qlen 1
      link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
      inet 127.0.0.1/8 scope hose 1o
           valid_lft forever preferred_lft forever
      inet6  ::1/128 scope host
            valid_lft forever preferred_lft forever
2:  ens3: <BROADCARS,MULTICAST> mtu 1500 qdisk noop state DOWN group default qlen 1000
       link/ether 52:54:00:eb:ac:f6 brd ff:ff:ff:ff:ff:ff

```



I assume the problem is related to the host and not the guest, but i am unable to figure out what to do. Anyone have an idea? 
my guess is that the problem is related to the netplan configuration. 

Many thanks

---

### Post by slickymaster on 2018-11-02
Thread moved to **Virtualisation** for a better fit

---

