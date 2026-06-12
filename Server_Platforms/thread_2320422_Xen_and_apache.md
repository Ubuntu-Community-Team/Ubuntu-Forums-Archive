---
title: "Xen and apache"
date: 2016-04-13
forum: Server Platforms
---

### Post by mikeossur on 2016-04-13
Hi all,
  This is a xen bridge issue.  I have a web server guest.  When people  click on a web page, the apache logs show the IP of the bridge, not the persons IP who clicked on the page.  The bridge should be transparent (and is on my older Debian configuration)

I have a pretty strait forward set up, or at least I think I do.  Any ideas why my guest web server logs are not seeing the users IP? What would be the typical cause?

Thanks all.

# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo xenbr0 xenbr1


iface lo inet loopback


# The primary network interface


iface xenbr0 inet static


bridge_ports p6p1
address 74.xxx.xxx.5
netmask 255.255.255.240
gateway 74.xxx.xxx.14


#bridge_stp off


dns-nameservers 68.xxx.xxx.146 68.xxx.xxx.98




iface xenbr1 inet static
bridge_ports eth1
#bridge_stp off


address 192.168.1.1
netmask 255.255.255.0
#broadcast 192.168.1.255




post-up ethtool --offload p6p1 gso off tso off sg off gro off
post-up ethtool --offload eth1 gso off tso off sg off gro off



# This is an autoconfigured IPv6 interface
#iface p6p1 inet6 auto




bridge name	bridge id		STP enabled	interfaces
xenbr0		8000.00a0244d1fbe	no		p6p1
							vif2.0
							vif7.0
							vif8.0
xenbr1		8000.feffffffffff	no		vif1.0
							vif2.1
							vif7.1
							vif8.1
							vif9.0

---

