---
title: "What has changed with nic bonding??"
date: 2012-02-27
forum: Server Platforms
---

### Post by MakOwner on 2012-02-27
I just ran apt-get update; apt-get upgrade and kernel 3.0.0-16 was installed which required a reboot.  

Upon reboot, I have no network connectivity...

I bond eth0 and eth1 into bond0 using /etc/network/interfaces (or did, anyway..)

```

auto bond0
iface bond0 inet dhcp
slaves eth0 eth1
# LACP confuration
bond_mode 0
bond_miimon 1500

```

This worked fine until this update.
Either of the interfaces, if configured individually work fine too, so it's not a hardware issue.

---

### Post by hawkmage on 2012-02-27
I have a multi boot system with Ubuntu 11.10 that I had been using a bond of the two built in NICs.  This is working in CEntOS 6.2 but when I saw this post I went and booted into Ubuntu and the bond interface looks to be up but it is not communicating.  

So you are not the only one experiencing this.

---

### Post by MakOwner on 2012-02-28
> **hawkmage said:**
> I have a multi boot system with Ubuntu 11.10 that I had been using a bond of the two built in NICs.  This is working in CEntOS 6.2 but when I saw this post I went and booted into Ubuntu and the bond interface looks to be up but it is not communicating.  

So you are not the only one experiencing this.

After a reboot bond0 is created but with no link or configuration, and neither of the physical interfaces are up.  I can down the bond, then manually assemble the interface.

Anyone have any hints?

---

### Post by zeljkojagust on 2012-02-28
Did you check /etc/modprobe.d/bonding.conf file (maybe it's not called bonding.conf on your installation). In it you should have alias configuration for your bonded interface and options for bonding defined. Probably you updated ifenslave package and destroyed that configuration. If not shure what I'm talking about please check this link: [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

---

### Post by MakOwner on 2012-02-28
> **zeljkojagust said:**
> Did you check /etc/modprobe.d/bonding.conf file (maybe it's not called bonding.conf on your installation). In it you should have alias configuration for your bonded interface and options for bonding defined. Probably you updated ifenslave package and destroyed that configuration. If not shure what I'm talking about please check this link: [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

I added bonding to the /etc/modules.
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

bonding
loop
lp
rtc


```

But that doesn't allow the assembly at boot time.
After the boot I can manually assemble the bonded interface and I can then see that the module is loaded.

```

$ lsmod
Module                  Size  Used by
...
bonding               109740  0 
...
tg3                   147729  0 

```


So, some issue with the order of loading I suppose.

I found a post with a reference to past issues with this and they came up with a series of modprobe commands in the /etc/network/interfaces file.  I'm going to be remote and can't work on this for a few days now.  Hope the damn thing doesn't need a reboot.

I have a 10.04 LTS server that needs a reboot and several updates applied - anyone know if this wonderful feature will affect it too?

---

### Post by hawkmage on 2012-02-28
OK, I got mine working again.

I am not sure if this is the same for your /etc/network/interfaces file but previously but I only had the bond0 interface defined and this worked.

What I had was:
```
auto bond0
iface bond0 inet static
 address xxx.xxx.xxx.72
 gateway xxx.xxx.xxx.1
 netmask 255.255.255.0
 bond-slaves eth0 eth1
 # LACP confuration
 bond_mode 802.3ad
 bond_miimon 100
 bond_lacp_rate 1

iface bond0 inet6 static
 address 2001:xxxx:xxxx::72
 netmask 64
 up ip -6 route add default via 2001:xxxx:xxxx::1
 up ip -6 route del default via 2001:xxxx:xxxx::1
```

Based on the instructions in the Ubuntu Bonding page I added the eth0 and eth1 interfaces above the bond0 interface like this:
```
auto eth0
iface eth0 inet manual
 bond-master bond0

auto eth1
iface eth1 inet manual
 bond-master bond0
```

---

### Post by MakOwner on 2012-03-01
I tried this - note that I only have two interfaces and I have been using dhcp on the bonded interface, so I had to modify it a bit.
But this makes it work -- thanks!!!!!!

```

#################################################
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

auto bond0
iface bond0 inet dhcp
slaves eth0 eth1

# LACP confuration
bond_mode 0
bond_miimon 100
# bond_lacp_rate 1

```

---

### Post by MakOwner on 2012-03-01
> **hawkmage said:**
> OK, I got mine working again.

I am not sure if this is the same for your /etc/network/interfaces file but previously but I only had the bond0 interface defined and this worked.



Could you share a link to where you found this documented?
The stuff I found was obviously dated as I found nothing about the requirement for the manual interface entires.

---

### Post by hawkmage on 2012-03-01
It was actually on the page that zeljkojagust posted the link to: [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

---

### Post by MakOwner on 2012-03-25
> **hawkmage said:**
> It was actually on the page that zeljkojagust posted the link to: [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

I'm about to go bald pulling my hair out.
I have it working, but at each boot the MAC address assigned to the bonded pair alternates between the one supplied by the two physical nics.

Anyone know if there is a keyword to assign a MAC address in the interfaces file?

I tried hwaddress and it hangs on boot and eventually completes without networking configured.

---

### Post by lazychris2000 on 2012-05-18
> **MakOwner said:**
> 
Anyone know if there is a keyword to assign a MAC address in the interfaces file?

I literally just fixed this problem about 2 hours ago.  Stumbled across this post looking for a separate issue...but I digress

What I did was add 'hwaddress ether 11:11:11:11:11:11' to /etc/network/interfaces.  
Here's my working interfaces file for reference:

```
auto eth0
iface eth0 inet manual
	bond-master bond0
auto eth1
iface eth1 inet manual
	bond-master bond0
auto bond0
iface bond0 inet dhcp
	hwaddress ether 11:11:11:11:11:11
	bond-mode 0
	bond-miimon 100
	bond-slaves none
```

Of course, you'll have to replace the MAC with whatever you want it to be.  Hope that helps

---

### Post by MakOwner on 2012-05-19
> **lazychris2000 said:**
> I literally just fixed this problem about 2 hours ago.  Stumbled across this post looking for a separate issue...but I digress

What I did was add 'hwaddress ether 11:11:11:11:11:11' to /etc/network/interfaces.  
Here's my working interfaces file for reference:

```
auto eth0
iface eth0 inet manual
	bond-master bond0
auto eth1
iface eth1 inet manual
	bond-master bond0
auto bond0
iface bond0 inet dhcp
	hwaddress ether 11:11:11:11:11:11
	bond-mode 0
	bond-miimon 100
	bond-slaves none
```

Of course, you'll have to replace the MAC with whatever you want it to be.  Hope that helps


That's almost exactly what worked for me -- the biggest thing to watch for (other than the bond-master thing) in the upgrade from 10.04 to 12.04 is that the bond-* keywords changed.  For example bond-miimon used to be bond_miimon.  

Working config with 12.04 LTS
```

################################################
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

# ***OLD LACP configuration***
#bond_mode 0
#bond_miimon 100
#bond_lacp_rate 1


auto bond0
iface bond0 inet dhcp
hwaddress 00:12:34:56:78:99
bond-slaves eth0 eth1
bond-mode 0
bond-miimon 100


```

 
Working config with 10.04 LTS - and this consistentley uses the MAC address of the first interface on bond0

```

################################################
 # This file describes the network interfaces available on your system
 # and how to activate them. For more information, see interfaces(5).

 # The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto bond0
iface bond0 inet dhcp
slaves eth0 eth1

# LACP configuration
bond_mode 0
bond_miimon 100


```


Edit:
And just for the folks who land here from googling (like me, the next time I have to do this)
sudo apt-get install ifenslave
sudo vi /etc/network/interfaces 

Make the changes appropriate to your version, and reboot if you are remote, restart networking if you are local.
So far as I can tell at least when using the minimal install, this works right out of the box.

---

