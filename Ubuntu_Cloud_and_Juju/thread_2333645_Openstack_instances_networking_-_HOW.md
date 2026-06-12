---
title: "Openstack instances networking - HOW?"
date: 2016-08-11
forum: Ubuntu Cloud and Juju
---

### Post by bladedoyle on 2016-08-11
I configured a 5-system MAAS + Landscape + OpenStack using the landscape/juju openstack installer but have not been able to get networking configured to access the instances.

As required, I have 5 physical systems each with IPMI power control, 3 of them have 2 "disks", and I have 2 networks (public net for the maas and the openstack network node, and private network for all of them).  I configure maas and install landscape using "openstack-install" (juju).

In landscape web interface, while selecting the openstack components and setting configuration for open Vswitch, I select the public network and configure the address range, gateway, etc.  
The open vswitch configuration also asks me for "Tenant CIDR" and "Tenant gateway".  

Question:   What network is it asking for?   Is this the same as the "internal" network I configured for MAAS?   Is this a virtual network to be created by open vswitch?  Do I need to configure this as a 3rd network between compute and networking nodes - either a physical interface or a virtual interface on a bridge?  Something else?

When installing openstack via landscape/juju, should I expect instance networking to get configured for me, or are there additional manual steps I need to take?  Please provide a link to instructions.

So far I have not been able to ping or ssh into an instance.  When I poke around neutron and openvswitch I see this:

root@compute2:/home/ubuntu# ovs-ofctl show br-tun
OFPT_FEATURES_REPLY (xid=0x2): dpid:00003a460fd2224f
n_tables:254, n_buffers:256
capabilities: FLOW_STATS TABLE_STATS PORT_STATS QUEUE_STATS ARP_MATCH_IP
actions: output enqueue set_vlan_vid set_vlan_pcp strip_vlan mod_dl_src mod_dl_dst mod_nw_src mod_nw_dst mod_nw_tos mod_tp_src mod_tp_dst
 1(patch-int): addr:e2:55:1d:10:d3:7e
     config:     0
     state:      0
     speed: 0 Mbps now, 0 Mbps max
 2(gre-0a055072): addr:e2:5f:6b:20:4b:3f
     config:     0
     state:      0
     speed: 0 Mbps now, 0 Mbps max
 LOCAL(br-tun): addr:3a:46:0f:d2:22:4f
     config:     PORT_DOWN
     state:      LINK_DOWN
     speed: 0 Mbps now, 0 Mbps max
OFPT_GET_CONFIG_REPLY (xid=0x4): frags=normal miss_send_len=0

Is this "PORT_DOWN"/"LINK_DOWN" a cause of my problems or a symptom?
What are the next troubleshooting steps I should take?


Any help is much appreciated.
Blade.

---

### Post by bladedoyle on 2016-08-15
Hello ubuntu cloud community!

Bump.

Please ask for additional information or to clarify my question if its not clear.

For claiming to be the leader in openstack cloud deploys, the activity here seems .... too quiet.   Certainly somebody has installed OpenStack via Ubuntu landscape and figured out what additional steps are needed to ssh to newly created instances?  I am currently working with Ubuntu but if this project is dead I'll consider taking RDO for a testdrive.

Thanks.
Blade.

---

### Post by aeltester on 2016-08-16
I have not used the software you're using but when I create vxlans, the network attributes are always those the next level up. thus your gateway, dns etc refer to that of the host.

next you would create ip ranges and attach nics to vms, some of them might be gateways, dns etc for other vms on the same layer.

when you instantiate vms from sunstone or whatever openstack ships, the configuration from the template ie which nic, which ip, which gateway the virtual lan has been configured to take is used next to the one you configure in your /etc/network/interfaces. thus one of them should be nulled or they should match.

btw, i dropped openstack for opennebula but that's off topic.

---

