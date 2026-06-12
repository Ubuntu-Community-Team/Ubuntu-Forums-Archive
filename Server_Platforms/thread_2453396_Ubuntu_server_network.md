---
title: "Ubuntu server network"
date: 2020-11-09
forum: Server Platforms
---

### Post by danielb630 on 2020-11-09
hey all, 
im trying to set a small virtual environment that includes a DHCP and DNS server , a web server and two clients , 
after installing the DHCP and configuring it , everything was fine , but im having a hard time configuring and understanding the network ,
the machine is not connected to the internet,
im using NAT and ive turned down the DHCP service from VMWARE because i want my DHCP server to assign addresses to the other machines,
what is my default gateway on a virtual machine ? 
sorry for the ignorance , i will appreciate any kind of help


/etc/network/interfaces : 


auto lo
iface lo inet loopback




auto ens33
iface ens33 inet static
        address 192.168.10.10
        netmask 255.255.255.0
        gateway 192.168.10.1
        dns-nameservers 8.8.8.8






ifconfig : 


ens33: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.10.10  netmask 255.255.255.0  broadcast 192.168.10.255
        inet6 fe80::20c:29ff:fe64:f361  prefixlen 64  scopeid 0x20<link>
        ether 00:0c:29:64:f3:61  txqueuelen 1000  (Ethernet)
        RX packets 2886  bytes 214120 (214.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1609  bytes 204925 (204.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 182  bytes 13474 (13.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 182  bytes 13474 (13.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0




systemctl status isc-dhcp-server : 


&#9679; isc-dhcp-server.service - ISC DHCP IPv4 server
   Loaded: loaded (/lib/systemd/system/isc-dhcp-server.service; enabled; vendor
   Active: active (running) since Mon 2020-11-09 18:24:56 UTC; 1h 0min ago
     Docs: man:dhcpd(8)
 Main PID: 1039 (dhcpd)
    Tasks: 1 (limit: 2232)
   CGroup: /system.slice/isc-dhcp-server.service
           &#9492;&#9472;1039 dhcpd -user dhcpd -group dhcpd -f -4 -pf /run/dhcp-server/dhcp


Nov 09 19:20:03 server dhcpd[1039]: DHCPDISCOVER from 00:0c:29:64:f3:61 (server)
Nov 09 19:20:04 server dhcpd[1039]: DHCPOFFER on 192.168.10.13 to 00:0c:29:64:f3
Nov 09 19:21:07 server dhcpd[1039]: DHCPDISCOVER from 00:0c:29:64:f3:61 (server)
Nov 09 19:21:08 server dhcpd[1039]: DHCPOFFER on 192.168.10.13 to 00:0c:29:64:f3
Nov 09 19:22:11 server dhcpd[1039]: DHCPDISCOVER from 00:0c:29:64:f3:61 (server)
Nov 09 19:22:12 server dhcpd[1039]: DHCPOFFER on 192.168.10.13 to 00:0c:29:64:f3
Nov 09 19:23:14 server dhcpd[1039]: DHCPDISCOVER from 00:0c:29:64:f3:61 (server)
Nov 09 19:23:15 server dhcpd[1039]: DHCPOFFER on 192.168.10.13 to 00:0c:29:64:f3
Nov 09 19:24:17 server dhcpd[1039]: DHCPDISCOVER from 00:0c:29:64:f3:61 (server)
Nov 09 19:24:18 server dhcpd[1039]: DHCPOFFER on 192.168.10.13 to 00:0c:29:64:f3
lines 1-19/19 (END)

---

### Post by darkod on 2020-11-09
The gateway is the router connecting both networks.

If you plan to have an isolated environment inside vmware you can do that but you would still need the traffic to be routed to the outside and the internet somehow. One option is a VM serving as router which has two NICs. One on the LAN and with internet access, the other NIC in the vmware isolated network.

---

### Post by SeijiSensei on 2020-11-09
You don't need NAT.  

The server can easily handle DHCP, DNS and web services on one machine.

Are the clients also virtual machines? If there's just the three machines, then you don't really need a gateway.  All of them should be able to communicate among themselves using broadcasts. If the server was sending traffic to the Internet, then you'd need NAT with the server as a gateway. You'd also need to activate IPv4 packet forwarding in /etc/sysctl.conf.

---

### Post by danielb630 on 2020-11-09
> **darkod said:**
> The gateway is the router connecting both networks.

If you plan to have an isolated environment inside vmware you can do that but you would still need the traffic to be routed to the outside and the internet somehow. One option is a VM serving as router which has two NICs. One on the LAN and with internet access, the other NIC in the vmware isolated network.
Can you please explain me how to do that ?
> **SeijiSensei said:**
> You don't need NAT.  

The server can easily handle DHCP, DNS and web services on one machine.

Are the clients also virtual machines? If there's just the three machines, then you don't really need a gateway.  All of them should be able to communicate among themselves using broadcasts. If the server was sending traffic to the Internet, then you'd need NAT with the server as a gateway. You'd also need to activate IPv4 packet forwarding in /etc/sysctl.conf.
The clients are also virtual machines, i want to configure a default gateway because i want to practice ,
can i make my server as the default gateway ? 
And if yes , should my other virtual machines be on the same NIC for it to work properly ?

---

### Post by SeijiSensei on 2020-11-09
Yes, you can make the server the gateway if you follow the steps I mentioned. 

All the machines need to be in the same IP subnet, e.g., 10.10.10.0-255 (aka 10.10.10.0/24). Usually a router lives at the .1 or .254 address. So I'd assign 10.10.10.1 to the server, and use a range of addresses in the same space for the clients like 10.10.10.100-199. You can specify this in the configuration for isc-dhcp-server In the DHCP configuration, set 10.10.10.1 as the default gateway. 

Best practice is to give the server a static IP address not managed by DHCP.  Or you can use a "DHCP reservation" to permanently pair the server's MAC address with its IP.  If the machine described above with interface ens33 is the server, then its MAC address is 00:0c:29:64:f3:61.

However unless the server is designed to forward traffic to some upstream network, you don't really need a gateway, but you can specify one for practice.

---

### Post by danielb630 on 2020-11-10
> **SeijiSensei said:**
> Yes, you can make the server the gateway if you follow the steps I mentioned. 

All the machines need to be in the same IP subnet, e.g., 10.10.10.0-255 (aka 10.10.10.0/24). Usually a router lives at the .1 or .254 address. So I'd assign 10.10.10.1 to the server, and use a range of addresses in the same space for the clients like 10.10.10.100-199. You can specify this in the configuration for isc-dhcp-server In the DHCP configuration, set 10.10.10.1 as the default gateway. 

Best practice is to give the server a static IP address not managed by DHCP.  Or you can use a "DHCP reservation" to permanently pair the server's MAC address with its IP.  If the machine described above with interface ens33 is the server, then its MAC address is 00:0c:29:64:f3:61.

However unless the server is designed to forward traffic to some upstream network, you don't really need a gateway, but you can specify one for practice.

Thank you very much man !
Ill try it today after work&#128591;

---

### Post by danielb630 on 2020-11-12
after doing that , how do i connect it to the network ?

---

### Post by SeijiSensei on 2020-11-12
Which network? You should already have a network among the virtual machines.

Are you asking how to interconnect the virtual network with the public Internet? 

I don't use VMWARE, but VirtualBox. There the simplest solution would be to have all the virtual machines running in "bridged" mode, so the virtuals have IPs on the same network as the physical host. But if you must maintain separation between the two, you'd probably need to 

1) add a second interface to the router/server in bridged mode;
2) make the default route on the clients the router/server, but point the default route on that machine to your router that connects to the Internet;
3) edit /etc/sysctl.conf and enable net.ipv4.ip_forward as described there;
4) add an iptables masquerading rule for traffic leaving the virtual network and going to your Internet router.

I haven't done this; this is just based on my general experience with networking on Linux.

---

### Post by danielb630 on 2020-11-13
> **SeijiSensei said:**
> Which network? You should already have a network among the virtual machines.

Are you asking how to interconnect the virtual network with the public Internet? 

I don't use VMWARE, but VirtualBox. There the simplest solution would be to have all the virtual machines running in "bridged" mode, so the virtuals have IPs on the same network as the physical host. But if you must maintain separation between the two, you'd probably need to 

1) add a second interface to the router/server in bridged mode;
2) make the default route on the clients the router/server, but point the default route on that machine to your router that connects to the Internet;
3) edit /etc/sysctl.conf and enable net.ipv4.ip_forward as described there;
4) add an iptables masquerading rule for traffic leaving the virtual network and going to your Internet router.

I haven't done this; this is just based on my general experience with networking on Linux.

Im talking about the DHCP server that i would like to make also my router, 
should i edit /etc/network/interfaces and add a new interface ? 
do i need the new interface to be static? do i need the DHCP server to be on bridged or NAT?
can i make only the new interface bridged ?

---

### Post by TheFu on 2020-11-13
/etc/network/interfaces was deprecated with 17.10.  Netplan is how newer releases are configured.
DHCP server needs to be on the same subnet and only 1 should be available for any client to find.

Which VMware hypervisor is being used?  They make 6 of them, last time I counted. Each has very different capabilities.

---

### Post by SeijiSensei on 2020-11-13
The virtual server is running isc-dhcp-server, right, and serving address information to the virtual clients.  It does not need to be bridged at all.  It's only serving addresses on the virtual network. And if you don't want to interconnect this little network with any other, then you don't need NAT or multiple interfaces. Each virtual machine will be operating in the virtual network space, and that network will be isolated from any others.

As I said before, the router/server should have a static address conventionally either at .1 or .254.

If you haven't read [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html), particularly section 6.2 on networking "modes" and section 6.7 on "host-only" networking, now would be a good time.

---

