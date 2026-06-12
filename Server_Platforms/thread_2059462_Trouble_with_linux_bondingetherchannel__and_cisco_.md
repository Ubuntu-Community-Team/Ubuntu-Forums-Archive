---
title: "Trouble with linux bonding/etherchannel  and cisco switch"
date: 2012-09-18
forum: Server Platforms
---

### Post by FORCED-INDUCTN on 2012-09-18
Hello I have an Ubuntu 12.04 server. I am trying to get an etherchannel running between it and a Cisco Nexus 5548P.

Here is the relevant part of /etc/network/intefaces:

auto eth4
iface eth4 inet manual
        bond-master bond0
        bond-primary eth4 eth5 eth6 eth7
auto eth5
iface eth5 inet manual
        bond-master bond0
        bond-primary eth4 eth5 eth6 eth7
auto eth6
iface eth6 inet manual
        bond-master bond0
        bond-primary eth4 eth5 eth6 eth7
auto eth7
iface eth7 inet manual
        bond-master bond0
        bond-primary eth4 eth5 eth6 eth7

auto bond0
iface bond0 inet manual
        bond-slaves none
        bond_miimon 100
        bond_mode 802.3ad
# DO-SAN inteface @ bond0
auto vlan77
iface vlan77 inet static
        address 10.1.77.40
        netmask 255.255.255.0
        vlan_raw_device bond0

Here is the Cisco config part:
interface Ethernet1/25
  description Fortress
  switchport mode trunk
  switchport trunk allowed vlan 10,69,130-133
  spanning-tree port type edge trunk
  channel-group 4040 mode active

interface Ethernet1/26
  description Fortress
  switchport mode trunk
  switchport trunk allowed vlan 10,69,130-133
  spanning-tree port type edge trunk
  channel-group 4040 mode active

interface Ethernet1/27
  description Fortress
  switchport mode trunk
  switchport trunk allowed vlan 10,69,130-133
  spanning-tree port type edge trunk
  channel-group 4040 mode active

interface Ethernet1/28
  description Fortress
  switchport mode trunk
  switchport trunk allowed vlan 10,69,130-133
  spanning-tree port type edge trunk
  channel-group 4040 mode active

When I run the status command on the Nexus I get:

show port-channel summary
Flags:  D - Down        P - Up in port-channel (members)
        I - Individual  H - Hot-standby (LACP only)
        s - Suspended   r - Module-removed
        S - Switched    R - Routed
        U - Up (port-channel)
--------------------------------------------------------------------------------
Group Port-       Type     Protocol  Member Ports
      Channel
--------------------------------------------------------------------------------
10    Po10(SD)    Eth      LACP      Eth1/29(D)   Eth1/30(D)   Eth1/31(D)
                                     Eth1/32(D)
4024  Po4024(SD)  Eth      LACP      Eth1/17(D)   Eth1/18(D)   Eth1/19(D)
                                     Eth1/20(D)
4026  Po4026(SD)  Eth      LACP      Eth1/21(D)   Eth1/22(D)   Eth1/23(D)
                                     Eth1/24(D)
4040  Po4040(SU)  Eth      LACP      Eth1/25(P)   Eth1/26(P)   Eth1/27(P)
                                     Eth1/28(P)
****

Only one port comes up (eth1/27) I cannot figure out why the others won't come up :(

Any ideas?

--Forced

---

### Post by jam35y30 on 2012-10-01
What MTU do you have on the Ubuntu side, Nexus side is 1500Bytes?

Also keep the ports clean. Meaning enable modes as below:

interface e1/1
switchport
sitchport mode trunk
channel-group 1 mode active

Then under the port channel add your "rules"

interface po1
switchport trunk allowed vlan 10,69,130-133
spanning-tree port type edge trunk
no shut

Once configured, if fiber check the rx/tx (swap until you get link light) or if copper then ensure you have a cross-over as I don't recall a mdix command on nexus

Hope that helps and some additional info:

Teaming on the Server
Servers provide several different options for teaming with names that vary according to the vendor. The most common options include:
&#9679;
Active-standby
&#9679;
Active-active transmit load balancing: With this option, only one NIC can transmit and receive, and all NICs can transmit. This configuration enhances the server transmit performance, but doesn&#8217;t improve the receive bandwidth.
&#9679;
Static port channeling: Equivalent to channel-group-mode on, which is PortChannels without any negotiation protocol in place.
&#9679;
IEEE 802.3ad port channeling: This option enables the negotiation of the PortChannel between server and switch, thus allowing the server administrator to know if the configuration was successful. Similarly, it gives the network administrator information on whether the server administrator configured teaming properly.
With vPC support on the switch, the last two options can be deployed with network adapters split on two different access switches, thus achieving increased bandwidth and redundancy at the same time.
In addition, the teamed adapters can be virtualized with VLANs, with each VLAN showing on the server as a physically separate adapter. This allows the consolidation of multiple adapters for increased aggregated bandwidth.
The choice of the teaming option depends on the topology and the configuration of the switching infrastructure. A vPC-based data center enables both static port channeling and 802.3ad port channeling with or without 802.1q VLAN partitioning on the NIC.

James

---

