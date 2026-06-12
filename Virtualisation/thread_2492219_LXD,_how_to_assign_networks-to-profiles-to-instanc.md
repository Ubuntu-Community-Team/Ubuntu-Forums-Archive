---
title: "LXD, how to assign networks-to-profiles-to-instance?"
date: 2023-11-03
forum: Virtualisation
---

### Post by rrlangly2 on 2023-11-03
I'm having an issue trying to get instances to talk to each other. I create two LXD neworks.

```
$ lxc network create lanA ipv4.address=192.168.1.1/24 ipv6.address=none ipv4.dhcp=true
$ lxc network create wanA ipv4.address=10.10.10.1/24 ipv6.address=none
```

I then create a profile for each instance type. The first, I'm trying to get ip's on two different interfaces, one for the local lan, and a second to route across a simulated wan (not yet created).

    ```
$ lxc profile create profile1
$ lxc profile device add profile1 root disk path=/ pool=default
$ lxc profile device add profile1 intA nic name=enp1s0 network=lanA
$ lxc profile device add profile1 intB nic name=enp2s0 network=wanA
```

On the second, just a single interface.
    ```
$ lxc profile create profile2
$ lxc profile device add profile2 root disk path=/ pool=default
$ lxc profile device add profile2 intA nic name=enp1s0 network=lanA
```

I then launch two instances with these profiles.

    ```
$ lxc launch ubuntu:20.04 instB --profile profile2
$ lxc launch ubuntu:20.04 instA --profile profile1
```
    
The problem is that when I run `lxc list`, I don't see any ip's in the IPV4 column. Is this not a valid use of profiles? If I could get this to work, then I would create a wanB, lanB just like lanA and wanA, and have a lanA-wanA-wanB-lanB routed network which is my goal.

Thanks for any help.

---

### Post by MAFoElffen on 2023-11-03
Instead of ipv4.address, should you have rather done ipv4.gateway=XXX.XXX.XXX.XXX/24? Wouldn't using what you did, set every container to that IP address resulting in an address conflict?

Just what I see there so far.

Could you please post the results of 
```

lxc profile show profile1
lxc profile show profile2
lxc network list

```

---

### Post by rrlangly2 on 2023-11-04
I renamed things to hopefully make it a bit clearer. I don't believe ipv4.gateway=xxx.xxx.xxx.xxx/24 is needed at this point because the instances are both on a managed bridge, have ipv4.dhcp=true (so they should get at least ip's and not have ip conflicts), and should be able to talk to each other on their interfaces as they would both be on the same lan.

Here's the profiles and networks.

$ lxc profile show lan-profile
```
config: {}
description: ""
devices:
  lan_if:
    name: enp1s0
    network: lan_A
    type: nic
  root:
    path: /
    pool: default
    type: disk
name: lan-profile
used_by:
- /1.0/instances/instA
- /1.0/instances/instB
```

$ lxc profile show wan-profile
```
config: {}
description: ""
devices:
  lan_if:
    name: enp1s0
    network: lan_A
    type: nic
  root:
    path: /
    pool: default
    type: disk
  wan_if:
    name: enp2s0
    network: wan
    type: nic
name: wan-profile
used_by:
- /1.0/instances/instC

```

$ lxc network show lan_A
```
config:
  ipv4.address: 192.168.1.1/24
  ipv4.dhcp: "true"
  ipv4.nat: "true"
  ipv6.address: none
description: ""
name: lan_A
type: bridge
used_by:
- /1.0/instances/instA
- /1.0/instances/instB
- /1.0/instances/instC
- /1.0/profiles/lan-profile
- /1.0/profiles/wan-profile
managed: true
status: Created
locations:
- none

```

$ lxc network show wan
```
config:
  ipv4.address: 10.10.10.1/24
  ipv4.nat: "true"
  ipv6.address: none
description: ""
name: wan
type: bridge
used_by:
- /1.0/instances/instC
- /1.0/profiles/wan-profile
managed: true
status: Created
locations:
- none

```

Instance A, B, and C are all on the same lan (192.168.1.0/24) and instC is to have a second interface (10.10.10.0/24) that allow traffic to instD (not shown because I'm not there yet). Right now, I just want to get ip's on instances A, B, and C for each interface.

---

### Post by MAFoElffen on 2023-11-04
I'm not sure it works like that... I see what you are trying to do, but...

When you create a profile you do:
```

lxc profile create <profile_name>
lxc profile set <profile_name> <option_key>=<option_value> <option_key>=<option_value> ...
lxc profile device add <profile_name> <device_name> <device_type> <device_option_key>=<device_option_value> <device_option_key>=<device_option_value> ...
lxc profile device set <profile_name> <device_name> <device_option_key>=<device_option_value> <device_option_key>=<device_option_value> ...

```

When you add a profile to an instance, you do:
```

lxc profile add <instance_name> <profile_name>

```
A profile will look like this:
```

config: {}
description: Default LXD profile
devices:
  eth0:
    name: eth0
    network: lxdbr0
    type: nic
  root:
    path: /
    pool: maf1_pool
    type: disk
name: default
used_by:
- /1.0/instances/maf1-alpine1
- /1.0/instances/maf1-centos1
- /1.0/instances/maf1-jammy1
- /1.0/instances/maf1-oracle1
- /1.0/instances/maf1-tumbleweed1
- /1.0/instances/maf1-archlinux1
- /1.0/instances/maf1-gentoo1

```
See where is says "network: "? That would be one of the network device names listed in the first column of this 
```

mafoelffen@Mikes-ThinkPad-T520:~/Downloads$ lxc network list
+---------+----------+---------+-----------------+---------------------------+-------------+---------+---------+
|  NAME   |   TYPE   | MANAGED |      IPV4       |           IPV6            | DESCRIPTION | USED BY |  STATE  |
+---------+----------+---------+-----------------+---------------------------+-------------+---------+---------+
| enp0s25 | physical | NO      |                 |                           |             | 0       |         |
+---------+----------+---------+-----------------+---------------------------+-------------+---------+---------+
| lxcbr0  | bridge   | NO      |                 |                           |             | 0       |         |
+---------+----------+---------+-----------------+---------------------------+-------------+---------+---------+
| lxdbr0  | bridge   | YES     | 10.137.170.1/24 | fd42:faa0:db6f:bf0a::1/64 |             | 8       | CREATED |
+---------+----------+---------+-----------------+---------------------------+-------------+---------+---------+
| virbr0  | bridge   | NO      |                 |                           |             | 0       |         |
+---------+----------+---------+-----------------+---------------------------+-------------+---------+---------+
| virbr1  | bridge   | NO      |                 |                           |             | 0       |         |
+---------+----------+---------+-----------------+---------------------------+-------------+---------+---------+
| virbr2  | bridge   | NO      |                 |                           |             | 0       |         |
+---------+----------+---------+-----------------+---------------------------+-------------+---------+---------+
| virbr3  | bridge   | NO      |                 |                           |             | 0       |         |
+---------+----------+---------+-----------------+---------------------------+-------------+---------+---------+
| wlp3s0  | physical | NO      |                 |                           |             | 0       |         |
+---------+----------+---------+-----------------+---------------------------+-------------+---------+---------+

```
Which you didn't post the results of, like I asked...

You create an LXC network with:
```

lxc network create <name> --type=<network_type> [configuration_options...]

```
And attach it to an instance's "network device" like this:
```

lxc network attach <network_name> <instance_name> [<device_name>] [<interface_name>]
# or this
lxc config device add <instance_name> <device_name> nic network=<network_name>

```
You seem to want to do that all in one step treating both as the same thing. right?

...And since you seem to not believe me, this is from one of the maintainers of LXC, telling someone else how to do the same, and NOT to use ipv4.address in a network def or profile: [https://discuss.linuxcontainers.org/t/attach-network-to-profile/1135/4](https://discuss.linuxcontainers.org/t/attach-network-to-profile/1135/4)

---

### Post by rrlangly2 on 2023-11-06
I thought showing the devices would let you know what was in the list, but here's the list.

$ lxc network list
```
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
| lan_A    | bridge   | YES     |             | 5       |
+----------+----------+---------+-------------+---------+
| lxcbr0   | bridge   | NO      |             | 0       |
+----------+----------+---------+-------------+---------+
| lxdbr0   | bridge   | YES     |             | 1       |
+----------+----------+---------+-------------+---------+
| virbr0   | bridge   | NO      |             | 0       |
+----------+----------+---------+-------------+---------+
| wan      | bridge   | YES     |             | 2       |
+----------+----------+---------+-------------+---------+
| wlp110s0 | physical | NO      |             | 0       |
+----------+----------+---------+-------------+---------+

```

It's not that I don't believe you, but it's not clear what you're saying or appears we're doing the same thing according to the docs. I'm starting to wonder if bridged will work for me.

---

### Post by MAFoElffen on 2023-11-06
If you do not declare a '-type' in the network create command, then it uses it's the default type, which is 'bridge'. The valid types you can use are bridge, ovn, macvlan, sriov, and physical.

---

