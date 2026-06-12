---
title: "LXD, why is device name using 'eth0'?"
date: 2023-11-06
forum: Virtualisation
---

### Post by rrlangly2 on 2023-11-06
Why does this configuration result in the `lxc list` results below where it appears to have gotten a DHCP address as specified in the network, but it's shows on eth0 rather than on enp1s0?

$ lxc list    
```
+-------+---------+----------------------+------+-----------+-----------+
| NAME  |  STATE  |         IPV4         | IPV6 |   TYPE    | SNAPSHOTS |
+-------+---------+----------------------+------+-----------+-----------+
| instA | RUNNING | 192.168.1.117 (eth0) |      | CONTAINER | 0         |
+-------+---------+----------------------+------+-----------+-----------+

```
Here is how it was configured.

```
    lxc network create lanA \
        ipv4.address=192.168.1.1/24 \
        ipv6.address=none \
        ipv4.dhcp=true

    lxc profile create lan-profile
    lxc profile device add lan-profile root disk path=/ pool=default
    lxc profile device add lan-profile enp1s0 nic name=mylan network=lanA

    lxc launch ubuntu:focal instA --profile lan-profile
    lxc network attach lanA instA enp1s0

```    
I am trying to create mulitple interfaces for a single instance and can't very well do that if I can't get just one interface right. In the 'lxc profile device add' above, I have 'name=mylan', but it still seems to have used 'eth0' for the name.

Thoughts?

---

$ lxc network list```

+----------+----------+---------+-------------+---------+
|   NAME   |   TYPE   | MANAGED | DESCRIPTION | USED BY |
+----------+----------+---------+-------------+---------+
| br0      | bridge   | NO      |             | 1       |
+----------+----------+---------+-------------+---------+
| br-int   | bridge   | NO      |             | 0       |
+----------+----------+---------+-------------+---------+
| docker0  | bridge   | NO      |             | 0       |
+----------+----------+---------+-------------+---------+
| eno1     | physical | NO      |             | 0       |
+----------+----------+---------+-------------+---------+
| lanA     | bridge   | YES     |             | 2       |
+----------+----------+---------+-------------+---------+
| lxcbr0   | bridge   | NO      |             | 0       |
+----------+----------+---------+-------------+---------+
| lxdbr0   | bridge   | YES     |             | 1       |
+----------+----------+---------+-------------+---------+
| virbr0   | bridge   | NO      |             | 0       |
+----------+----------+---------+-------------+---------+
| wan      | bridge   | YES     |             | 0       |
+----------+----------+---------+-------------+---------+
| wlp110s0 | physical | NO      |             | 0       |
+----------+----------+---------+-------------+---------+

```

$ lxc profile show lan-profile
```
config: {}
description: ""
devices:
  enp1s0:
    name: mylan
    network: lanA
    type: nic
  root:
    path: /
    pool: default
    type: disk
name: lan-profile
used_by:
- /1.0/instances/instA

```
Or am I reading it wrong because according to this, it appears to just be a name?

$ lxc config show instA --expanded
```
architecture: x86_64
config:
  image.architecture: amd64
  image.description: ubuntu 20.04 LTS amd64 (release) (20231011)
  image.label: release
  image.os: ubuntu
  image.release: focal
  image.serial: "20231011"
  image.type: squashfs
  image.version: "20.04"
  volatile.base_image: 1ff1055f282309f25c3c43ad3a2dba2e6c585c45dee442e3e831335d6889643d
  volatile.enp1s0.host_name: veth131b22a0
  volatile.enp1s0.hwaddr: 00:16:2b:46:23:22
  volatile.enp1s0.name: eth0
  volatile.idmap.base: "0"
  volatile.idmap.current: '[{"Isuid":true,"Isgid":false,"Hostid":1000000,"Nsid":0,"Maprange":1000000000},{"Isuid":false,"Isgid":true,"Hostid":1000000,"Nsid":0,"Maprange":1000000000}]'
  volatile.idmap.next: '[{"Isuid":true,"Isgid":false,"Hostid":1000000,"Nsid":0,"Maprange":1000000000},{"Isuid":false,"Isgid":true,"Hostid":1000000,"Nsid":0,"Maprange":1000000000}]'
  volatile.last_state.idmap: '[{"Isuid":true,"Isgid":false,"Hostid":1000000,"Nsid":0,"Maprange":1000000000},{"Isuid":false,"Isgid":true,"Hostid":1000000,"Nsid":0,"Maprange":1000000000}]'
  volatile.last_state.power: RUNNING
  volatile.uuid: 07cddd05-0b4d-427a-ab91-91542bd463bf
devices:
  enp1s0:
    network: lanA
    type: nic
  root:
    path: /
    pool: default
    type: disk
ephemeral: false
profiles:
- lan-profile
stateful: false
description: ""

```

---

### Post by MAFoElffen on 2023-11-06
Look at this first... This is what is there:
```

mafoelffen@Mikes-ThinkPad-T520:~$ lxc list
+------------------+---------+------+------+-----------+-----------+
|       NAME       |  STATE  | IPV4 | IPV6 |   TYPE    | SNAPSHOTS |
+------------------+---------+------+------+-----------+-----------+
| maf1-alpine1     | STOPPED |      |      | CONTAINER | 0         |
+------------------+---------+------+------+-----------+-----------+
| maf1-archlinux1  | STOPPED |      |      | CONTAINER | 0         |
+------------------+---------+------+------+-----------+-----------+
| maf1-centos1     | STOPPED |      |      | CONTAINER | 0         |
+------------------+---------+------+------+-----------+-----------+
| maf1-gentoo1     | STOPPED |      |      | CONTAINER | 0         |
+------------------+---------+------+------+-----------+-----------+
| maf1-jammy1      | STOPPED |      |      | CONTAINER | 0         |
+------------------+---------+------+------+-----------+-----------+
| maf1-oracle1     | STOPPED |      |      | CONTAINER | 0         |
+------------------+---------+------+------+-----------+-----------+
| maf1-tumbleweed1 | STOPPED |      |      | CONTAINER | 0         |
+------------------+---------+------+------+-----------+-----------+
mafoelffen@Mikes-ThinkPad-T520:~$ lxc start maf1-jammy1
mafoelffen@Mikes-ThinkPad-T520:~$ lxc list
+------------------+---------+-----------------------+-----------------------------------------------+-----------+-----------+
|       NAME       |  STATE  |         IPV4          |                     IPV6                      |   TYPE    | SNAPSHOTS |
+------------------+---------+-----------------------+-----------------------------------------------+-----------+-----------+
| maf1-alpine1     | STOPPED |                       |                                               | CONTAINER | 0         |
+------------------+---------+-----------------------+-----------------------------------------------+-----------+-----------+
| maf1-archlinux1  | STOPPED |                       |                                               | CONTAINER | 0         |
+------------------+---------+-----------------------+-----------------------------------------------+-----------+-----------+
| maf1-centos1     | STOPPED |                       |                                               | CONTAINER | 0         |
+------------------+---------+-----------------------+-----------------------------------------------+-----------+-----------+
| maf1-gentoo1     | STOPPED |                       |                                               | CONTAINER | 0         |
+------------------+---------+-----------------------+-----------------------------------------------+-----------+-----------+
| maf1-jammy1      | RUNNING | 10.137.170.139 (eth0) | fd42:faa0:db6f:bf0a:216:3eff:fe9b:9029 (eth0) | CONTAINER | 0         |
+------------------+---------+-----------------------+-----------------------------------------------+-----------+-----------+
| maf1-oracle1     | STOPPED |                       |                                               | CONTAINER | 0         |
+------------------+---------+-----------------------+-----------------------------------------------+-----------+-----------+
| maf1-tumbleweed1 | STOPPED |                       |                                               | CONTAINER | 0         |
+------------------+---------+-----------------------+-----------------------------------------------+-----------+-----------+
mafoelffen@Mikes-ThinkPad-T520:~$ lxc exec maf1-jammy1 -- sudo /bin/bash
root@maf1-jammy1:~# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
10: eth0@if11: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 00:16:3e:9b:90:29 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet 10.137.170.139/24 metric 100 brd 10.137.170.255 scope global dynamic eth0
       valid_lft 3521sec preferred_lft 3521sec
    inet6 fd42:faa0:db6f:bf0a:216:3eff:fe9b:9029/64 scope global mngtmpaddr noprefixroute 
       valid_lft forever preferred_lft forever
    inet6 fe80::216:3eff:fe9b:9029/64 scope link 
       valid_lft forever preferred_lft forever
root@maf1-jammy1:~# ls /sys/class/net
eth0  lo

```
Why does yours show as enp1s0? Because you created a profile and applied it to your container... Probably without looking at it first to query what it did have as devices. If you had checked the LXC doc's, then all say eth0 is the first net device for a container... It doesn't remap the name like physical or VM's.

That did not mean that existed already when you applied that, and that you were configuring what was there, or that it is valid... It added a network device named enp1s0. It did what you asked it to. Of course eth0 is probably sitting there without being configured right?

Check with my last command for the net device names, then do 'ip a' to see what is configured & not. That is what I do... To diagnose, treat it like any other Linux machine, and see what it see's through it's eyes. Right?

---

