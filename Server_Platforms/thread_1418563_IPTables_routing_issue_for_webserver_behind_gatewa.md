---
title: "IPTables routing issue for webserver behind gateway"
date: 2010-02-28
forum: Server Platforms
---

### Post by twistedtwig on 2010-02-28
Hi all,

It has been a while since I looked at IPtables and I seem to be worse than before as I can not seem to get my webserver online.  Below is my firewall rules on the gateway server that is running the dhcp server accessing the net.  The webserver is inside my network on a static IP (192.168.0.98, default port).  When I use Nmap or GRC.com I see that port 80 is open but when I browse to it it always fails with a connection error, (nmap will not also connect and figure out what the web server is).

If can nmap the webserver and browse to it just fine via same IP inside my network.  The issue seems to be that the gateway server can not ping the webserver.

my gateway server is connected to a router that goes off to my home pc and a ESXi server with a couple of VM web Servers running on them.  

The gateway server can ping the home PC but not the webserver.  The home pc can connect to them all.  The webserver can connect to the web just fine and ping all machines.

I do not understand why the gateway server can not route to the webserver, but can to everything else.

```
#!/bin/sh
iptables="/sbin/iptables"
modprobe="/sbin/modprobe"
depmod="/sbin/depmod"

EXTIF="eth2"
INTIF="eth1"

load () {

  $depmod -a

  $modprobe ip_tables
  $modprobe ip_conntrack
  $modprobe ip_conntrack_ftp
  $modprobe ip_conntrack_irc
  $modprobe iptable_nat
  $modprobe ip_nat_ftp

echo "enable forwarding.."
echo "1" > /proc/sys/net/ipv4/ip_forward
echo "enable dynamic addr"
echo "1" > /proc/sys/net/ipv4/ip_dynaddr

# start firewall

  # default policies
  $iptables -P INPUT DROP
  $iptables -F INPUT
  $iptables -P OUTPUT DROP
  $iptables -F OUTPUT
  $iptables -P FORWARD DROP
  $iptables -F FORWARD
  $iptables -t nat -F


echo "   Opening loopback interface for socket based services."
$iptables -A INPUT -i lo -j ACCEPT
$iptables -A OUTPUT -o lo -j ACCEPT

echo "   Allow all connections OUT and only existing and related ones IN"
$iptables -A INPUT -i $INTIF -j ACCEPT
$iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$iptables -A OUTPUT -o $EXTIF -j ACCEPT
$iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$iptables -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
$iptables -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
$iptables -A FORWARD -j LOG

echo "   Enabling SNAT (MASQUERADE) functionality on $EXTIF"
$iptables -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

$iptables -A INPUT -i $INTIF -j ACCEPT
$iptables -A OUTPUT -o $INTIF -j ACCEPT

echo "   Allowing packets with ICMP data (i.e. ping)."
$iptables -A INPUT -p icmp -j ACCEPT
$iptables -A OUTPUT -p icmp -j ACCEPT

$iptables -A INPUT -p udp -i $INTIF --dport 67 -m state --state NEW -j ACCEPT

echo "   Port 137 is for NetBIOS."
$iptables -A INPUT -i $INTIF -p udp --dport 137 -j ACCEPT
$iptables -A OUTPUT -o $INTIF -p udp --dport 137 -j ACCEPT

echo "   Opening port 53 for DNS queries."
$iptables -A INPUT -p udp -i $EXTIF --sport 53 -j ACCEPT

#iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to 192.168.0.2:3128
#iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

echo "   opening Apache webserver"
$iptables -A PREROUTING -t nat -i $EXTIF -p tcp --dport 80 -j DNAT --to 192.168.0.98:80
$iptables -A FORWARD -p tcp -m state --state NEW -d 192.168.0.98 --dport 80 -j ACCEPT

# this is designed to stop brute force attacks
$iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 6/minute --limit-burst 5 -j ACCEPT

}

flush () {

   echo "flushing rules..." $iptables -P FORWARD ACCEPT
   $iptables -F INPUT
   $iptables -P INPUT ACCEPT
   echo "rules flushed"

}

case "$1" in

   start|restart)
     flush
     load
     ;;
   stop)
     flush
     ;;
*)
    echo "usage: start|stop|restart."
    ;;

esac
exit 0

```

route info:

> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
5e0412a6.bb.sky *               255.255.255.255 UH    0      0        0 eth2
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
default         5e0412a6.bb.sky 0.0.0.0         UG    100    0        0 eth2


ifconfig:

```
eth1      Link encap:Ethernet  HWaddr 00:22:b0:cf:4a:1c
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:b0ff:fecf:4a1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79023 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57786 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11580918 (11.5 MB)  TX bytes:22872030 (22.8 MB)
          Interrupt:17 Base address:0x2b00

eth2      Link encap:Ethernet  HWaddr 00:0c:f1:7c:45:5b
          inet addr:94.4.18.166  Bcast:94.4.18.166  Mask:255.255.255.255
          inet6 addr: fe80::20c:f1ff:fe7c:455b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:21631721 (21.6 MB)  TX bytes:7685444 (7.6 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1517 (1.5 KB)  TX bytes:1517 (1.5 KB)

```

I would be really grateful for any and all help with this.

Thanks

Jon

---

### Post by twistedtwig on 2010-02-28
just took one of the webservers off of static and used DHCP, it got a lease from the gateway server.  could ping the web but gateway server still couldn't ping its new IP address.  only difference I can see in network is that it is on EXSi VM box. powered up a Ubuntu Live CD on a wireless laptop going through the same router and the server can ping that no problem.

---

### Post by stlsaint on 2010-02-28
maybe this will help.[ IPtables]("http://bodhizazen.net/Tutorials/iptables/").

---

### Post by twistedtwig on 2010-03-02
thanks for the link, it definitely helped with my knowledge.  Unfortunately I still can not get it to work.

I still believe it is the firewall that is stopping the requests getting through, or getting back out.

Some of the solutions I have been reading about used their public IP as the destination for outbound traffic, but I have a dynamic IP so I don't see how I can use those solutions.

I am very confused and really want to get my site back up.

Any help or suggestions would be so wonderfully received.

Thanks

---

