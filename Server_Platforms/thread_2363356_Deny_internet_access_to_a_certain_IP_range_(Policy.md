---
title: "Deny internet access to a certain IP range (Policy based routing?)"
date: 2017-06-09
forum: Server Platforms
---

### Post by tccz on 2017-06-09
Hi everyone,

this is my first post here and in general, I am still quite new to server administration. If I am barking up the wrong tree completely, please feel free to tell me so!

Anyway, I have set up an instance of Ubuntu Server 16.04.2 LTS on a local server. On it I am running a variety of servers, including DHCP and DNS. The idea is to provide Intranet access with custom domain names, which is actually working fine enough. Clients connect to the server using a Wifi router with DHCP disabled and up until now there is no internet access for either clients or server, so far so good.

I am now looking to allow the server to access the internet without the clients being able to access it as well. The TP-Link router I am using allow me to plug in a 3g dongle (unfortunately that is all that will work here in rural Turkana) which connects fine. When I change the servers network configuration to use the router as a gateway it connects to the internet just fine but so do all the clients in the Wireless.

Is it possible to deny Internet access to all clients (which the server is assigning IP addresses to, say 192.168.0.75-150) while still allowing them to resolve local DNS requests? 

The setup is as follows:

TP-Link router with DHCP disabled and established 3G connection on 192.168.0.1
Server with the following /etc/network/interfaces/ on 192.168.0.100

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo eno1 eno1:1 eno1:2 eno1:3 eno1:4 eno1:5 eno1:6 eno1:7 eno1:8 eno1:9 eno1:10 eno1:11 eno1:12
iface lo inet loopback


# The primary network interface
#iface eno1 inet dhcp
iface eno1 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        gateway 192.168.0.0
        #dns-nameservers 8.8.8.8


iface eno1:1 inet static
        address 192.168.0.25
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0


iface eno1:2 inet static
        address 192.168.0.21
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0

[...]


```

This is the subnet I have configured in the DHCP.conf, which is supposed to resolve local addresses but not access the internet:
```

option broadcast-address 192.168.0.255;
option routers 192.168.0.1;
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
#


# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style interim;


# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers 192.168.0.100;


default-lease-time 600;
max-lease-time 7200;


# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;


# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;


[...]
subnet 192.168.0.0 netmask 255.255.255.0 {
        max-lease-time 86400;
        range 192.168.0.75 192.168.0.150;
        }



```

I might be going about this completely the wrong way or perhaps the solution is very simple. Essentially I would like the configured subnet to only access the intranet while the server itself and anything running on it can access the internet.

Thanks in advance.

Tim

---

### Post by darkod on 2017-06-09
Are the clients using 192.168.0.1 as a gateway? I assume yes... In such case it would be difficult to limit them using internet because it is the router that is giving them internet, not the server. The server does give them the dhcp leases, but if that lease tells them to use 192.168.0.1 as a GW, and 192.168.0.1 has internet, the clients will have internet automatically.

You can check if you can limit the internet on the router but usually for home routers those option are very limited or non-existent.

One solution might be to set your server in between the router and the clients. In such case your server will be router for the clients and you can easily tell it not to give them internet traffic. Such setups are usually done by using separate subnet for the clients, and you would need another wi-fi access point because they can't connect to the router directly, otherwise again they have internet right away...

---

### Post by SeijiSensei on 2017-06-09
If the server sits between the clients and the TP-Link, then they won't have access to the Internet by default since IP packet forwarding is disabled in /etc/sysctl.conf.  The server will need an Ethernet adapter, if it doesn't have one already, and you'll need a [network switch]("https://www.newegg.com/Switches/SubCategory/ID-30") to which the clients, and the server's Ethernet adapter, will all connect.  Configure DHCP to make the server the clients' default gateway.  The server should have the TP-Link device as its default gateway.

---

### Post by tccz on 2017-06-10
I have followed your advice and configured the DHCP server to broadcast the server's IP as the default gateway for clients and configured the server's network interface to use the router as a gateway. It seems to work! The clients can connect to the Wifi and locally resolved domains continue to work as before. They can also resolve external domains, probably due to the Server now being able to resolve them itself. However, even though they resolve fine, the clients can't connect to any external resources. I will monitor the behaviour but it seems this solution will work.  (Might there be any way to stop the clients resolving external domain names?)

Thanks for your advice and the other answer given!!

Best Tim

---

### Post by SeijiSensei on 2017-06-11
You could block the clients' ability to make all DNS requests by adding an iptables rule to the server.  Suppose that the server uses eno1 to connect to the clients. Then the rule
```
sudo /sbin/iptables -A INPUT -i eno1 -p udp --dport 53 -j REJECT
```
will block queries arriving from the clients on the eno1 interface to the DNS port 53/udp.  

If this works for you, you can make the rule permanent by adding it to the file /etc/rc.local without the "sudo" prefix.

If you want the clients to resolve local addresses but not external ones, you'll probably need to set up BIND on the server and have it handle the local address space.  The server itself can have its resolver pointing to an Internet server like the one from your ISP or Google's 8.8.8.8.

My guess is that your router is maintaining the mappings between local client addresses and hostnames.  If that's the case, things get a bit trickier.  You could move the entire DHCP/DNS apparatus from the router to the server using [isc-dhcp-server]("https://help.ubuntu.com/community/isc-dhcp-server") and bind9 for those tasks.  They have [hooks to add the mappings]("https://blog.bigdinosaur.org/running-bind9-and-isc-dhcp/") created by DHCP to the DNS records when new clients get their addresses.

---

