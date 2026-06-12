---
title: "Help with nic bond + tagged vlan + bridging on Precise server"
date: 2012-07-28
forum: Server Platforms
---

### Post by mid_crisis on 2012-07-28
I'm trying to get several boxes with Precise server configured for hosting KVM virtual machines.
Two or four NICS bonded with tagged vlan's and three bridges.
using the interfaces file below I can manually start and stop networking and get the interfaces up but they do not survive a reboot and I get the dreaded "waiting 60 more seconds for network..."

##################interfaces#######################
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual
    bond-master bond0

auto eth1
iface eth1 inet manual
    bond-master bond0

auto eth2
iface eth2 inet manual
    bond-master bond0

auto eth3
iface eth3 inet manual
    bond-master bond0

auto bond0
iface bond0 inet manual
bond-slaves none
bond-mode 2
bond-miimon 100

# The primary network interface
auto vlan168
iface vlan168 inet manual
    vlan_raw_device bond0

# The private net
auto vlan169
iface vlan169 inet manual
    vlan_raw_device bond0

# Storage network
auto vlan340
iface vlan340 inet manual
    vlan_raw_device bond

auto br168
iface br168 inet static
    address xxxx.xxxx.xxxx.6
    netmask 255.255.255.128
    network xxxx.xxxx.xxxx.0
    gateway xxxx.xxxx.xxxx.1
    # dns-* options are provided by the reolvconf package if installed
    dns-nameservers xxxx.xxxx.xxxx.xxxx
    dns-search search.domain
    bridge_ports vlan168
    bridge_maxwait 0
    bridge_fd 0
    bridge_stp on

auto br169
iface br169 inet static
    address xxxx.xxxx.xxxx.134
    netmask 255.255.255.128
    gateway xxxx.xxxx.xxxx.129
    bridge_ports vlan169
    bridge_maxwait 0
    bridge_fd 0
    bridge_stp on

auto br340
iface br340 inet static
    address xxxx.xxxx.xxxx.6
    netmask 255.255.255.128
    gateway xxxx.xxxx.xxxx.1
    bridge_ports vlan340
    bridge_maxwait 0
    bridge_fd 0
    bridge_stp on
######################interfaces########################

Like I said I can get the interfaces up by consoling in and issuing:

service networking stop/start
or
/etc/init.d/networking stop/start

In order to get the interfaces up.

lscpi:

03:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
03:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
04:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
04:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)

cat /proc/net/vlan/config:

VLAN Dev name	 | VLAN ID
Name-Type: VLAN_NAME_TYPE_PLUS_VID_NO_PAD
vlan168        | 168  | bond0
vlan169        | 169  | bond0
vlan340        | 340  | bond0

sudo lsmod | grep 8021:

8021q                  24084  0 
garp                   14602  1 8021q

some output from dmesg:

bonding: bond0: Warning: clearing HW address of bond0 while it still has VLANs.
[ 5645.900362] bonding: bond0: When re-adding slaves, make sure the bond's HW address matches its VLANs'.
[ 5649.398476] 8021q: adding VLAN 0 to HW filter on device bond0
[ 5649.399284] 8021q: VLANs not supported on bond0
[ 5649.407286] 8021q: VLANs not supported on bond0
[ 5649.415180] 8021q: VLANs not supported on bond0
[ 5649.442451] 8021q: adding VLAN 0 to HW filter on device bond0


Any help would be greatly appreciated!

---

### Post by mid_crisis on 2012-07-30
Hey all, I seem to have worked this out for myself,
Turned out to be the bond mode - when set to 1 all seems fine.
I still get several "VLANs not supported on bond0" messages but no "Recieved a packet with it's own address" errors.
And Generally the interfaces come up much more smoothly.
We'll see if it survives the week :)

I did need to add these entries to /etc/sysctl.conf

net.bridge.bridge-nf-call-ip6tables = 0
net.bridge.bridge-nf-call-iptables = 0
net.bridge.bridge-nf-call-arptables = 0
net.bridge.bridge-nf-filter-vlan-tagged = 0

and then

sysctl -p

As well as flush ebtables

ebtables -F

Then I took down the non functional bridge interfaces

ifconfig brxx down
brctl delbr brxx
...

then change the bond mode to 1 in the interfaces file
bond-mode 1

then started the networking.

Even seems to survive a reboot

---

