---
title: "vmplayer Ubuntu Linux Host cannot connect to Linux Guest"
date: 2014-01-25
forum: Virtualisation
---

### Post by rupert-sakanastudio on 2014-01-25
I have two physical host machines running vmplayer 6.0.1, one host is Win7 and one host is Ubuntu
both are running the same VMX image from the same OVA file on their own respective NAT's
Strangely I'm getting different levels of connectivity under seemingly the same settings.
both have the dhcp + host adapter included in the NAT setup

Physical Lan 192.168.1.0
Gateway 192.168.1.254
Windows Host#1 192.168.1.67
Ubuntu Host#2 192.168.1.68

NAT#1 192.168.100.0
Windows Host#1 192.168.100.1
Host Gateway 192.168.100.2
Linux Guest 192.168.100.31

NAT#2 192.168.100.0
Ubuntu Host#2 192.168.100.1
Host Gateway 192.168.100.2
Linux Guest 192.168.100.31

Both Guests can ping their respective Host
Windows Host can ping its guest and with putty SSH is possible
Ubuntu Host cannot ping its guest - error is ping: sendmsg: Operation not permitted
Nor is ssh possible from Ubuntu host to the linux guest

Both guests return nmap outputs on the NAT for: nmap -sn 192.168.100.0/24
192.168.100.2 (virtual router device/gateway)
192.168.100.31 (self)
Both can ping www addresses
Neither see the Host at 192.168.100.1
However Windows host can be "ping"ed to by it's guest on the Bridge Network address (192.168.1.68)
This is not possible on the Ubuntu host's guest to see the host on 192.168.1.67

I have not been able to find documentation that this host/guest communication has been disabled on Linux hosts. Have any other people suffered Linux host visibility issues on NAT networks with vmplayer too? is there a work around?
/etc/vmware/networking definitely has "VNET_8_VIRTUAL_ADAPTER yes" in it
and 
/etc/vmware/vmnet8/dhcpd/dhcpd.conf has the fixed ip of the host stated and I confirmed with ifconfig on host.

---

