---
title: "Problem with OVS and MTU"
date: 2017-08-07
forum: Virtualisation
---

### Post by apoz on 2017-08-07
Hi all,

I'm having some problem -apparently- with OVS and MTU(and QinQ VLAN), may be someone can give me some hint to try to determine the cause. I'm running 16.04  server in this machine.


Summarizing the scenario is the following:

I have OVS handling my VM connectivity to a VM in the following way :

```

HOST_INTERFACE ---- veth0 ---- veth1  ---- veth1.203 ----- ovs_load ---  VM_interface (tag 1) ---- VM_1
                         (veth peer interface pair)    (veth vlan)     (ovs switch)    (ovs tap with tag)

```

My traffic is IPV6 and I do some wget to create http traffic between some machine (external) and the VM_1.

The interesting bits of the scenario:
[LIST]
[*]The TCP is set up between the external machine and the VM_1
[*]BUT, when the response of VM_1 web server gets back to the client machine, the packet seems to be dropped in my ovs_load bridge (ovs has static configuration, NOT Openflow). The counter of dropped packages in the OVS does not get increased, though.
[/LIST]

_The problem is definitely related to the VLAN tagging (QinQ) and the MTU, because if I set the MTU in VM_1 interface to 1400 (so, the responses from that web server are smaller), everything works as expected._

The version of the ovs is the official packet provided by Ubuntu
```

ovs-vswitchd --version
ovs-vswitchd (Open vSwitch) 2.5.2
Compiled Mar 15 2017 13:55:24

```

I made the obvious changes in the MTU of the OVS and the interfaces, and now it's set to 9000.
```

1270: ovs_load: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9000 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
1271: veth1.203@veth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9000 qdisc noqueue master ovs-system state UP mode DEFAULT group default qlen 1000
1256: veth1@veth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9000 qdisc noqueue master br_untagged state UP mode DEFAULT group default qlen 1000
1257: veth0@veth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9000 qdisc noqueue master br_clos state UP mode DEFAULT group default qlen 1000

```


**Anyone is aware of any problem with MTU and OVS 2.5.2? Is there any log I can check to determine the cause?**  **Any additional parameters I can check for the MTU (apart of the MTU of the interfaces)?**

I think the 2nd VLAN tag in the packet is included by the veth (of vlan type) and it works as expected (as it happens in the first 'small' packet to set up the TCP).

Thank you very much in advance! Any help is truly appreciated!

Regards,
Andrés

---

