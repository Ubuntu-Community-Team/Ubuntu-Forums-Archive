---
title: "Ubuntu Server 11.10 Bonding-VLAN-Bridge"
date: 2011-11-05
forum: Server Platforms
---

### Post by happynix on 2011-11-05
I just wanted to post this as a possible help to someone.

I have several Ubuntu servers running Ganeti and vserver hosts.
(I chose Ganeti for my mostly static Virtualized environment)

I have two interfaces in each Server
All traffic traverses some sort of VLAN
[LIST=1]
[*] Bond the interfaces together
[*] Create Vlan interfaces
[*] Create a bridge for each vlan for the virtual machine instances
[/LIST]

I was able to get a working configuration from a post at[[COLOR="Blue"]FloatingToll[/COLOR]]("http://floatingatoll.posterous.com/ganeti-and-ubuntu-1004-lucid-configuring-brid"). Unfortunately I ran into a problem during reboot similar to  [[COLOR="Blue"]Bug 574456[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/ifenslave-2.6/+bug/574456"). 
Initally I was able to make it all work by using a modprobe alias for bonding. However, Scott Phelps (from [[COLOR="Blue"]Bug 574456[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/ifenslave-2.6/+bug/574456")) pointed out that my configuration, while operational was not appropriate for the ubuntu hotplug way of doing things.  On his advice I made a few alterations, got rid of the modprobe alias and I am down to this **/etc/network/interfaces** (only) configuration.

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
auto lo
iface lo inet loopback

# Notes:
#  - Don't assign an IP to a bonded interface if it's bound to a bridged interface.
#  - You'll probably want at least one interface configured for dhcp or a static IP.
#  - bond-slaves none on the bond device required because networking is event driven 
#    from the hardware interface(s)
#  - This configuration has no interfaces on unTagged VLANs

# Packages required:
#  - ifenslave2.6
#  - vlan
#  - bridge-utils
#######################################
########## INTERFACE BONDING ##########
# Configure the primary bonding interface that will be used for NIC1/NIC2 pairing.
auto bond0
# The IP will be assigned to the associated bridging interface.
iface bond0 inet manual
   # This option must always be 'none'; use "bond-master" on each interface.
    bond-slaves none
    # Common modes are active-backup and 802.3ad [1]
    bond-mode 802.3ad
    bond-ad_select bandwidth
    bond-lacp_rate slow
    # MII link monitoring frequency in ms [2]
    bond-miimon 100
    bond-use_carrier 1
    # Wait this long in ms before disabling an interface after MII failure [2]
    bond-downdelay 200
    # Wait this long in ms before enabling an interface after MII recovery [2]
    bond-updelay 200
    # This part seemed important to have the interface come up on boot (Thanks to Scott.Phelps)
    bond-primary eth0 eth1

# Bind the NIC1 physical interface to the primary bonding interface.
auto eth0
# Permit the bonded interface to turn this interface up/down as necessary.
allow-bond0 eth0
iface eth0 inet manual
   bond-master bond0
   bond-primary eth0 eth1

# Bind the NIC2 physical interface to the primary bonding interface.
auto eth1
# Permit the bonded interface to turn this interface up/down as necessary.
allow-bond0 eth1
iface eth1 inet manual
   bond-master bond0
   bond-primary eth0 eth1

#######################################
####### VLAN TAGGING INTERFACES #######
# Create an interface on a VLAN on the primary bonding interface.
auto bond0.10
iface bond0.10 inet manual
    # Older versions of Ubunti/Debian may need to specify raw vlan device
    #  grep -e "eth\*\.\*" /etc/network/if-pre-up.d/vlan |grep bond || echo "You need vlan-raw-device"
    #vlan-raw-device bond0

auto bond0.30
iface bond0.30 inet manual

auto bond0.31
iface bond0.31 inet manual

auto bond0.40
iface bond0.40 inet manual

#######################################
######### BRIDGING INTERFACES #########
# In this instance only bridge/vlan 100 is the control network
#  The other vlan/bridges are where all the vm instances live
# Create a bridged interface.
auto br10-CONTROL
iface br10-CONTROL inet static
    # Static assign the IP, netmask, default gateway.
    address 172.31.254.70
    netmask 255.255.255.0
    gateway 172.31.254.1
    # Bind one or more interfaces to the bridge.
    bridge_ports bond0.10

# Create a bridged interface.
auto br30-DMZ
iface br30-DMZ inet manual
    bridge_ports bond0.30

# Create a bridged interface.
auto br31-HOSTED
iface br31-HOSTED inet manual
    bridge_ports bond0.31

# Create a bridged interface.
auto br40-PRODUCTION
iface br40-PRODUCTION inet manual
    bridge_ports bond0.40

```

I hope someone else finds this useful.

---

### Post by gtoo-dtux on 2012-02-03
Although this configuration makes a lot of sense, It does not seem to work for me.  I am running the Desktop version of Ubuntu 11.10.  Could it be that NetworkManager is interfering with the process or are there maybe scripts which are in the Server version that are missing in the Desktop version?

---

### Post by danielmayer on 2012-02-19
> **gtoo-dtux said:**
> Although this configuration makes a lot of sense, It does not seem to work for me.  I am running the Desktop version of Ubuntu 11.10.  Could it be that NetworkManager is interfering with the process or are there maybe scripts which are in the Server version that are missing in the Desktop version?

Most likely not. Don't forget to install as stated in the script:
# Packages required:
#  - ifenslave2.6
#  - vlan
#  - bridge-utils
apt-get install ...

Thanks happynix, this conf is sorely missing in the ubuntu docs/wikis. I didn't understand many years, why the config of bonding/bridging in Ubuntu changed at least three times without documenting it sufficiently...
Your conf works like a charm, though I don't use Vlans.

---

### Post by tebrown on 2012-03-03
danielmayer, 

 Can you post your config?  I tried this on ubuntu 11.04, but without much luck.  If I take out the "bond-slaves none" line, I can at least get the network to come up. If leave that in, I get "Bond unitialized" error messages spewing on power up. 

```
#######################################
########## INTERFACE BONDING ##########
# Configure the primary bonding interface that will be used for NIC1/NIC2 pairing.
auto bond0
# The IP will be assigned to the associated bridging interface.
iface bond0 inet static
    address 10.3.178.1
    gateway 10.3.178.254
    netmask 255.255.255.0
    network 10.3.178.0
    broadcast 10.3.178.255
    # This option must always be 'none'; use "bond-master" on each interface.
    bond-slaves none
    # Common modes are active-backup and 802.3ad [1]
    bond-mode 802.3ad
    bond-ad_select bandwidth
    bond-lacp_rate slow
    # MII link monitoring frequency in ms [2]
    bond-miimon 100
    bond-use_carrier 1
    # Wait this long in ms before disabling an interface after MII failure [2]
    bond-downdelay 200
    # Wait this long in ms before enabling an interface after MII recovery [2]
    bond-updelay 200
    # This part seemed important to have the interface come up on boot (Thanks to Scott.Phelps)
    bond-primary eth0 eth1

# Bind the NIC1 physical interface to the primary bonding interface.
auto eth0
# Permit the bonded interface to turn this interface up/down as necessary.
allow-bond0 eth0
iface eth0 inet manual
   bond-master bond0
   bond-primary eth0 eth1

# Bind the NIC2 physical interface to the primary bonding interface.
auto eth1
# Permit the bonded interface to turn this interface up/down as necessary.
allow-bond0 eth1
iface eth1 inet manual
   bond-master bond0
   bond-primary eth0 eth1

```

---

### Post by tebrown on 2012-03-03
danielmayer, 

 Can you post your config?  I tried this on ubuntu 11.04, but without much luck.  If I take out the "bond-slaves none" line, I can at least get the network to come up. If leave that in, I get "Bond unitialized" error messages spewing on power up. 

```
#######################################
########## INTERFACE BONDING ##########
# Configure the primary bonding interface that will be used for NIC1/NIC2 pairing.
auto bond0
# The IP will be assigned to the associated bridging interface.
iface bond0 inet static
    address 10.3.178.1
    gateway 10.3.178.254
    netmask 255.255.255.0
    network 10.3.178.0
    broadcast 10.3.178.255
    # This option must always be 'none'; use "bond-master" on each interface.
    bond-slaves none
    # Common modes are active-backup and 802.3ad [1]
    bond-mode 802.3ad
    bond-ad_select bandwidth
    bond-lacp_rate slow
    # MII link monitoring frequency in ms [2]
    bond-miimon 100
    bond-use_carrier 1
    # Wait this long in ms before disabling an interface after MII failure [2]
    bond-downdelay 200
    # Wait this long in ms before enabling an interface after MII recovery [2]
    bond-updelay 200
    # This part seemed important to have the interface come up on boot (Thanks to Scott.Phelps)
    bond-primary eth0 eth1

# Bind the NIC1 physical interface to the primary bonding interface.
auto eth0
# Permit the bonded interface to turn this interface up/down as necessary.
allow-bond0 eth0
iface eth0 inet manual
   bond-master bond0
   bond-primary eth0 eth1

# Bind the NIC2 physical interface to the primary bonding interface.
auto eth1
# Permit the bonded interface to turn this interface up/down as necessary.
allow-bond0 eth1
iface eth1 inet manual
   bond-master bond0
   bond-primary eth0 eth1

```

---

