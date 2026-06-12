---
title: "Open VPN questions..."
date: 2010-03-23
forum: Server Platforms
---

### Post by Pro_D on 2010-03-23
Hey, trying to add an OpenVPN to my server to accept connections from people out on the internet (provided they have the right keys...)

I know I need to bridge one of my Ethernet devices but I don't know which one I should be bridging...  This is my core question, which one to bridge.  My intent is to allow those who VPN in to have full access to the LAN as if they were jacked in locally.  So eth0 or eth1?

Ubuntu 9.04 btw...

Here is the relevant (active) bits of my interfaces file:
# The loopback network interface
auto lo
iface lo inet loopback

# The internal network interface
auto eth0
iface eth0 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        post-up iptables-restore < /etc/iptables.up.rules

# The primary (internet) network interface
auto eth1
iface eth1 inet dhcp




Additionally (aside):

I have tried bridging both but whichever one I bridge becomes effectively broken.
If I bridge the internet interface then I loose internet access locally (and so obviously via machines behind the server as well).

If I bridge the internal interface then I loose all services that the server provides, except ping.  So I loose DHCP, DNS, iptables NAT routing, samba, openldap, etc...

If local internet access worked bridging the internet interface I could probably setup the other bits (iptables) to point to br0 fairly easily...

---

### Post by doogy2004 on 2010-03-23
I use OpenVPN AS - [http://openvpn.net/index.php/access-server/download-openvpn-as.html](http://openvpn.net/index.php/access-server/download-openvpn-as.html)

It is easy to setup and maintain.

---

### Post by Pro_D on 2010-03-23
Well, it installed, I configured it (for windows hosts) and set the correct values (public IP address, correct adapters) installed the client (on another machine) and got all the way up to what looked like getting an IP address (from the internet side of the network).  Failed.  Additionally it broke 1 or more of the services running on the server within the internal network.

I think I will keep trying along the lines of the links below...
[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)
[https://help.ubuntu.com/9.10/serverguide/C/openvpn.html](https://help.ubuntu.com/9.10/serverguide/C/openvpn.html)

Luckily uninstalling the package put the network back in order and as far as I can tell all services are in working order again.


I think this answered my primary question though - I need to bridge the internet connecting adapter.  Then just track down why I loose internet connectivity on the server system itself...

Thanks for the suggestion though, seems like pretty nice software, especially if I were running a dedicated VPN (or VPN/web server) system.

---

### Post by spynappels on 2010-03-24
Hi,

I've been working on an OpenVPN deployment myself, and you do not need to bridge the connections. You just need to tell it to route LAN IP addresses through your OpenVPN server. You need to make sure though that your LAN IP addresses are different to the LAN IP address of the remote computer.

Example: If your LAN where the OpenVPN server lives has an addressing pool 192.168.1.x and a client connects from a computer on a remote LAN also using 192.168.1.x, when the OpenVPN server pushes a route to the client, it will get confused, as it does not know whether to route an IP of say 192.168.1.50 to it's local LAN or to the remote LAN through the VPN tunnel. I've got around this by setting my LAN IPs to something like 192.168.50.x as this is less likely to be in use in remote locations.

I will check out my server.conf file and look at the exact syntax I used, but as long as ip_forward is set in the server (not in OVPN) you should be able to route to your LAN.

Edit:
Add this section to your server.conf file, substituting your server-side LAN IP. You also need to add a static route in the server-side LAN gateway routing your VPN traffice to your VPN clients through the IP of your OVPN server.

# Push routes to the client to allow it
# to reach other private subnets behind
# the server.  Remember that these
# private subnets will also need
# to know to route the OpenVPN client
# address pool (10.8.0.0/255.255.255.0)
# back to the OpenVPN server.
push "route 192.168.10.0 255.255.255.0" #substitute your #server-side LAN IP here


Hope this helps, do make sure any firewall on your OVPN server is set to allow traffic to and from the server's tun0 interface. Also make sure that ip_forward is enabled in the server, you need to change /proc/sys/net/ipv4/ip_forward to 1. You should be able to use the following command to do that.
```
sudo echo 1> /proc/sys/net/ipv4/ip_forward
```
and remember this is not persistent, if you reboot the VPN server, you will have to do this again.

---

### Post by dipeshmehta on 2010-03-27
> **spynappels said:**
> 
```
sudo echo 1> /proc/sys/net/ipv4/ip_forward
```
and remember this is not persistent, if you reboot the VPN server, you will have to do this again.

You may enable ipv4 forwards into /etc/sysctl.conf, so that if you reboot the server, you shall not have to do it again.

Dipesh

---

### Post by spynappels on 2010-03-27
Could you post the syntax to enable this persistently?

---

### Post by dipeshmehta on 2010-03-27
> **spynappels said:**
> Could you post the syntax to enable this persistently?

Please edit file /etc/sysctl.conf and uncomment the line with ipv4 forwards, thats it.  sysctl.conf gets executed everytime the server boots. (if I am not wrong.... please somebody confirm this) but anyway, this works fine on my ubuntu 8.04 server and openvpn

Dipesh

---

### Post by fang0654 on 2010-03-27
> **dipeshmehta said:**
> Please edit file /etc/sysctl.conf and uncomment the line with ipv4 forwards, thats it.  sysctl.conf gets executed everytime the server boots. (if I am not wrong.... please somebody confirm this) but anyway, this works fine on my ubuntu 8.04 server and openvpn

Dipesh

That's correct, /etc/sysctl.conf gets read every time the system reboots.  You can also import it manually with
```

sysctl -p /etc/sysctl.conf

```

---

### Post by spynappels on 2010-03-27
Cool, thanks.

---

### Post by Pro_D on 2010-03-27
On my front - from reading the correct item to bridge is the internal interface, but listen on the internet interface (for vpn clients).  Also apparently you need to bridge (with tap interface) if you have windows clients and want broadcasts (ipv4) to work.  Also other protocols can work over a bridge/tap than a route/tun.

Additionally, firewall was the reason why all services broke.  <smacks forehead *HARD*>.  Firewall (iptables) was based on interface names for the most part.

I didn't realize that br0 effectively became the internal interface that network communications happens on.

Next up (mentioning where I am going from here, not asking for help)...
-Finish setting up openvpn (initially use openvpn to assign IPs).
-Figure out how to distinguish the tap interface from the internal (br0/eth0) interface for dhcpd.  I know it's easier to just use openvpn to assign IPs to clients however I have dhcpd auto-updating my dns so it's best to use dhcpd for vpn clients.

---

### Post by Pro_D on 2010-03-27
OK, it's basically all working...
-openvpn accepts connection requests from any IP (so I can connect from dynamic locations).
-client gets IP address from dhcp server and not from openvpn meaning dynamic dns update happens so the vpn client can be accessed by name for things like shares.
-bridged network so things like broadcasts work (games).
-dhcp server is aware of if the request is from a tun/tap device or a regular lan connection and DOES NOT hand out gateway info to the vpn client (also different pool of addresses. (this one seems a bit fudged but I am ok with it - relies on tap/tun devices in openvpn having the first 2 bytes for hardware mac address be 00:FF).

1 lingering question though - is there any reason to prefer udp or tcp for the vpn?

[edit]
ok, nevermind.  I had a think on it and thought it might be bad to do TCP if I am running TCP in the tunnel, double the TCP controls.  UDP won't care much and TCP will probably be slowed down...

I took down some notes, wondering if I should make a new thread of something of a howto on this since I found the existing ones a bit lacking besides my stupidity of leaving the firewall up and running while changing this stuff.  For one thing I REALLY had to hunt for that dhcp aspect and found some gotchas in the firewall.
[/edit]

---

### Post by dipeshmehta on 2010-03-27
> **fang0654 said:**
> That's correct, /etc/sysctl.conf gets read every time the system reboots.  You can also import it manually with
```

sysctl -p /etc/sysctl.conf

```

Thanks for information

---

