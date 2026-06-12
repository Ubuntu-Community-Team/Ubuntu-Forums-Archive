---
title: "Server 10.04 -- Bond/VLAN"
date: 2010-08-25
forum: Server Platforms
---

### Post by dasunsrule32 on 2010-08-25
I am having issues with a simple VLAN setup. I have a vm server (vmware 2.0.2-latestbuild), two Dell Powerconnect 3024 switches, a Cisco RV082 router and a Cisco 1720 modular router connecting to the T1.

I have configured the RV082 as a dual-WAN with the DMZ enabled and set to an external IP range. I have an internal subnet of [192.168.56.0/24]("http://192.168.56.0/24") and the external subnet of 1xx.xxx.xxx.244-253 enabled in the router.

The Dell Powerconnect 3024's are running together. I have two VLAN's, VID=1,2. I have VLAN1 on the internal subnet and VLAN2 on the DMZ port. the vm server is part of VLAN1 and is working correctly with the rest of the network, all ping requests work, traffic, etc is fine. I have bonded eth0/1 into bond0 and then added a VLAN2, so bond0.2 and have added a new Bridged network adapter to the VLAN2 adapter.

Here is my current config that works only with the internal subnet:
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto bond0
iface bond0 inet static
address 192.168.56.2
netmask 255.255.255.0
network 192.168.56.0
gateway 192.168.56.1
broadcast 192.168.56.255
post-up ifenslave bond0 eth0 eth1
post-up vconfig add bond0 2
pre-down vconfig rem bond0.2
pre-down ifenslave -d bond0 eth0 eth1

#VLAN2 -- Web VLAN
auto bond0.2
iface bond0.2 inet manual
up ifconfig bond0.2 0.0.0.0 up

```Here is the config I tried while setting the system to bon0, bond0.1, bond0.1:
```

# The loopback network interface
auto lo
iface lo inet loopback

# Create bond interface and VLAN's
auto bond0
iface bond0 inet manual
post-up ifenslave bond0 eth0 eth1
post-up vconfig add bond0 1
post-up vconfig add bond0 2
pre-down vconfig rem bond0.1
pre-down vconfig rem bond0.2
pre-down ifenslave -d bond0 eth0 eth1

# VLAN1 -- Internal VLAN
auto bond0.1
iface bond0.1 inet static
address 192.168.56.2
netmask 255.255.255.0
network 192.168.56.0
gateway 192.168.56.1
broadcast 192.168.56.255

#VLAN2 -- Web VLAN
auto bond0.2
iface bond0.2 inet manual

```The second config file works, but not with this server, nothing can ping it or use its services, as a result, VLAN2 wouldn't work..

The vm server is plugged into the gigabit ports on the first switch and is untagged in VLAN1, and it is set to tagged in VLAN2 and the DMZ port that is part of VLAN2 is untagged and on switch2. I have not included the DMZ port in VLAN1.

I have added the DMZ adapter to my virtual machine, win2k3 ent box, and the internal adapter works correctly, however, the DMZ adapter does not.

I am at a loss as what to do. I have been running around in circles with this now for a bit and could really use the help. Thank you in advance for any help that can be offered!

---

### Post by dasunsrule32 on 2010-08-26
Anyone have any ideas or suggestions that I could try? Thank you.

---

### Post by grittyminder on 2010-08-26
It's been a while since I've fiddled with VLANs, but I'll try to help.


1) I am assuming that you have the vlan package installed?


2) You'll still need to define the physical (virtual?) network interface. Try adding the following before your VLAN definition (assuming it is named 'eth0'):

iface eth0 inet manual


3) I remember having problems with invalid VLAN names in the past. I do not know of all the acceptable naming conventions, but I do know that I was able to get "vlan<vlan#>" to work (e.g. vlan1, vlan350, vlan900, etc.) Try renaming bond0 to vlan100 or something like that.


4) All that post-up/pre-down stuff... get rid of it all. Instead add the following (assuming eth0):

vlan_raw_device eth0


5) Restart networking. You should see something like this:

Set name-type for VLAN subsystem. Should be visible in /proc/net/vlan/config
Added VLAN with VID == 4 to IF -:eth0:-
Set name-type for VLAN subsystem. Should be visible in /proc/net/vlan/config
Added VLAN with VID == 5 to IF -:eth0:-
Set name-type for VLAN subsystem. Should be visible in /proc/net/vlan/config
Added VLAN with VID == 101 to IF -:eth0:- 


So your modified networking file should look something like this:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface eth0 inet manual

auto vlan1
iface vlan1 inet static
address 192.168.56.2
netmask 255.255.255.0
network 192.168.56.0
gateway 192.168.56.1
broadcast 192.168.56.255
vlan_raw_device eth0

---

### Post by sh1ny on 2010-08-27
Not sure if it's related, but i was having problems with bridging over a bond when i upgraded to 10.04. I am using KVM, with the bridge, and while the host had networking, none of the guests would. At first i though it was the bridge, then it turned out that the way bonding is configured slightly changed in lucid. 

```
auto bond0
iface bond0 inet manual
        bond-slaves none
        bond-mode 1
        bond-miimon 100

auto eth0
iface eth0 inet manual
        bond-master bond0
        bond-primary eth0 eth1

auto eth1
iface eth1 inet manual
        bond-master bond0
        bond-primary eth0 eth1

```

This is how i had to change it to work. Again - not sure if this will help with VLAN over bond, but it did help with bridge over bond.

---

### Post by dasunsrule32 on 2010-08-27
> **grittyminder said:**
> It's been a while since I've fiddled with VLANs, but I'll try to help.


1) I am assuming that you have the vlan package installed?


2) You'll still need to define the physical (virtual?) network interface. Try adding the following before your VLAN definition (assuming it is named 'eth0'):

iface eth0 inet manual


3) I remember having problems with invalid VLAN names in the past. I do not know of all the acceptable naming conventions, but I do know that I was able to get "vlan<vlan#>" to work (e.g. vlan1, vlan350, vlan900, etc.) Try renaming bond0 to vlan100 or something like that.


4) All that post-up/pre-down stuff... get rid of it all. Instead add the following (assuming eth0):

vlan_raw_device eth0


5) Restart networking. You should see something like this:

Set name-type for VLAN subsystem. Should be visible in /proc/net/vlan/config
Added VLAN with VID == 4 to IF -:eth0:-
Set name-type for VLAN subsystem. Should be visible in /proc/net/vlan/config
Added VLAN with VID == 5 to IF -:eth0:-
Set name-type for VLAN subsystem. Should be visible in /proc/net/vlan/config
Added VLAN with VID == 101 to IF -:eth0:- 


So your modified networking file should look something like this:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface eth0 inet manual

auto vlan1
iface vlan1 inet static
address 192.168.56.2
netmask 255.255.255.0
network 192.168.56.0
gateway 192.168.56.1
broadcast 192.168.56.255
vlan_raw_device eth0


Thank you for the response, but you are having me kill my bond, which I need. That isn't what I need, I need to bond and then create VLAN's on top of that bond. Although I may be able to still create the bond and then use the vlan1 config you are using. I will check this out too. Thank you. :)

---

### Post by dasunsrule32 on 2010-08-27
> **sh1ny said:**
> Not sure if it's related, but i was having problems with bridging over a bond when i upgraded to 10.04. I am using KVM, with the bridge, and while the host had networking, none of the guests would. At first i though it was the bridge, then it turned out that the way bonding is configured slightly changed in lucid. 

```
auto bond0
iface bond0 inet manual
        bond-slaves none
        bond-mode 1
        bond-miimon 100

auto eth0
iface eth0 inet manual
        bond-master bond0
        bond-primary eth0 eth1

auto eth1
iface eth1 inet manual
        bond-master bond0
        bond-primary eth0 eth1

```This is how i had to change it to work. Again - not sure if this will help with VLAN over bond, but it did help with bridge over bond.

This looks like something that could work, I will give this a try in the next week or so to see if it works. Thank you for the response

---

### Post by Ednet on 2010-08-31
Implemented the below configuration for a demo.
Note that there is a suspected bug here (or a configuration method which may need to be optimized) as I had to restart the networking service (for each boot) to avoid LACP problems.

##########################

auto bond0
iface bond0 inet manual
        bond-slaves none
        bond-mode 4
        bond-miimon 100

auto eth0
iface eth0 inet manual
        bond-master bond0
        bond-primary eth0 eth1

auto eth1
iface eth1 inet manual
        bond-master bond0
        bond-primary eth0 eth1

auto vlan10
iface vlan10 inet static
        address 1.1.1.1
        netmask 255.255.255.0
        gateway 1.1.1.254
        vlan_raw_device bond0

auto vlan11
iface vlan11 inet static
        address 2.2.2.1
        netmask 255.255.255.0
        vlan_raw_device bond0

##########################
# Remember to restart the networking service, as problems were 
# detected while applying the above configuration on Ubuntu 
# Server 10.4.
##########################

For those who are interested in working with OpenVPN in bridging mode, the bridge can be linked to one of the VLAN/s and moving the IP configuration from the VLAN to the Bridge.

Thanks,
Edy.

---

### Post by sh1ny on 2010-08-31
I've had a few reboots where networking wouldn't start right away, but that's just until the bond reinitializes the slaves. Surely, a network restart helps, but it would come up anyway. You might have something like that in dmesg in such a boot :


```
[    7.253322] bonding: bond0: doing slave updates when interface is down.
```

Then it detects the first interface, but it seems down ( the switch didn't up the port fast enough i guess ) :

```
[    7.253329] bonding: bond0: enslaving eth0 as a backup interface with a down link
```

Then it detected the second link :


```
[    7.253354] bonding: bond0: Adding slave eth1.
```

Then it took a few more probes to sort it out :

```
[    7.253356] bonding bond0: master_dev is not up in bond_enslave
[    7.310082]   alloc irq_desc for 62 on node -1
[    7.310086]   alloc kstat_irqs on node -1
[    7.310100] bnx2 0000:05:00.0: irq 62 for MSI/MSI-X
[    7.440012] bnx2: eth1: using MSI
[    7.442014] bonding: bond0: enslaving eth1 as a backup interface with a down link.
[    7.442010] bonding: bond0: Setting eth0 as primary slave.
[    7.603196] bonding: bond0: Setting eth0 as primary slave.
[    7.606110] device bond0 entered promiscuous mode
[    7.609903] ADDRCONF(NETDEV_UP): bond0: link is not ready
[    8.889748] bnx2: eth0 NIC Copper Link is Up, 100 Mbps full duplex
[    8.901886] bonding: bond0: link status definitely up for interface eth0.
[    8.901891] bonding: bond0: making interface eth0 the new active one.
[    8.901895] device eth0 entered promiscuous mode
[    8.901919] bonding: bond0: first active interface up!
[    8.903921] ADDRCONF(NETDEV_CHANGE): bond0: link becomes ready
[    8.903987] br0: port 1(bond0) entering forwarding state
[    9.168875] bnx2: eth1 NIC Copper Link is Up, 100 Mbps full duplex
[    9.201885] bonding: bond0: link status definitely up for interface eth1.
```


While in previous ubuntu's i didn't had such "challenges" with bonding, it's still working properly in lucid...just a tad bit weirder.

---

