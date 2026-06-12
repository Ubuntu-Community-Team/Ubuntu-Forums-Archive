---
title: "Is it possible to route LAN through server"
date: 2011-05-03
forum: Server Platforms
---

### Post by corkscrew on 2011-05-03
I have a LAN behind an adsl router, comprised of mixed linux & windows boxes along with a NAS.These are all connected via an unmanged switch which is then connected to the router.

One of the boxes is Lucid Lynx Server. This box has an onboard Gigabit NIC & a PCI Gigabit NIC card.

I would like to know several things

1. Is it possible to route all the LAN traffic through this server before the router? ie LAN > switch > server > router > WAN

2. If this is possible would it slow down the internet connection for the various boxes on the LAN ?

3. Which would the best way to be to configure the Server ie which NIC in the server would I connect the LAN to and which the router to or would it matter?

4. Again if this possible I have no idea how to configure the NIC's on the server to do this is there any reading or simple how to's any where to show me the way?

---

### Post by BbUiDgZ on 2011-05-03
yes this can be done and yes it will slow down your network depending on the cpu speed of your server.
Read up on iptables and static routes or download a standalone network gateway/firewall/router. There are many offerings including ipcop and smoothwall

---

### Post by wineman on 2011-05-03
hi corkscrew

Your server is more than possible, its fairly simple to setup, you just need to know what goes where.

i'm assuming your network setup is like this:

WAN <-> Router <-> (onboard NIC) Ubuntu Proxy Server (PCI Gb card) <-> Switch <-> Lan + NAS

> **corkscrew said:**
> 
1. Is it possible to route all the LAN traffic through this server before the router? ie LAN > switch > server > router > WAN

Yes. using Iptables (optionally with Squid / dansguardian) and dhcp3-server, it is possible.
The config is fairly straightforward without squid, as follows:

First, install a dhcp3-server and iptables:
```
sudo apt-get install dhcp3-server iptables 
```
/etc/init.d/rc.firewall:
```

#!/bin/sh

# Some options to allow for ip routing
echo 1 > /proc/sys/net/ipv4/ip_forward
modprobe ip_nat_ftp
modprobe ip_conntrack_ftp

# Internal interface
int="eth1"
# External interface
ext="eth0"
# Location of iptables (usually /sbin/iptables)
ipt=`which iptables`

# Default input rules - clear everything that already is there
$ipt -F
$ipt -X
$ipt -t nat -F
$ipt -t nat -X
$ipt -A INPUT -i lo -j ACCEPT
$ipt -A OUTPUT -o lo -j ACCEPT

# Ports we want open on the INTERNAL LAN
# in this eg it is ssh, smtp, pop3, smb and webmin
oiports="22 25 110 137 138 139 443 10000"
for oip in $oiports
do
$ipt -A INPUT -i $int -p tcp --dport $oip -j ACCEPT
$ipt -A INPUT -i $int -p udp --dport $oip -j ACCEPT
done

# open ports on eth enternal interface (ie - th internet can 
# can connect to the proxy on these ports
# doesnt have to have ports that are the same as the internal interface,
# except DONT allow smb (137,138,139,443)
oeports="22 25 110 21 10000"
for oep in $oeports
do
$ipt -A INPUT -i $ext -p tcp --dport $oep -j ACCEPT
$ipt -A INPUT -i $ext -p udp --dport $oep -j ACCEPT
$ipt -A INPUT -i $ext -p tcp --dport $oep -j LOG --log-prefix "external-open-port-$oep "
done

# now we open some port forwardings 
# only use this if you want to allow VNC or VPN or MSTSC or whatever 
# access
# 47,1723 is for VPN; 3389 for MSTSC; 5900 is VNC; 80 is for a webserver 
opforwards="47 1723 3389 5900 80" 
# list the IP of the server we're forwarding to
# in this case, we have a class c internal pc
ip="192.168.1.100"
for opf in $opforwards
do 
$ipt -A FORWARD -i $ext -o $int -p tcp --dport $opf -j ACCEPT
$ipt -t nat -A PREROUTING -i $ext -p tcp --dport $opf -j DNAT --to $ip:$opf
done

# allow for internet routing - DMZ Masquerading proxying :P
$ipt -A FORWARD -i $int -o $ext -j ACCEPT
$ipt -A FORWARD -i $ext -o $int -m state --state RELATED,ESTABLISHED -j ACCEPT
$ipt -t nat -A POSTROUTING -o $ext -j MASQUERADE
# lockdown everything else
$ipt -A INPUT -j DROP
$ipt -A FORWARD -j DROP

```

now change the value of this in /etc/sysctl.conf:
```
# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

```
to this by uncommenting the net.ipv4.ip_forward=1

then, setup your dhcp3-server to assign ips. First you need to setup the network interfaces.
if you DSL router gives out DHCP addresses, use this config
in /etc/network/interfaces:
```

auto eth0 eth1 lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet static
    address 192.168.1.1
    netmask 255.255.255.0
    broadcast 192.168.1.255
    network 192.168.1.0


```

otherwise use this config
```

auto eth0 eth1 lo
iface lo inet loopback

iface eth0 inet static
    address <ip address in the router's subnet>
    netmask <router's netmask>
    gateway <router's IP address>
    dns-nameservers <router's IP>,<dns-server-1>,<dns-server-2>
# eg: 192.168.1.1 is 192.168.1.0
    network <subnet of router>.0
     

auto eth1
iface eth1 inet static
    address 192.168.1.1
    netmask 255.255.255.0
    broadcast 192.168.1.255
    network 192.168.1.0


```

then edit your dhcp3-server config:
/etc/init.d/dhcpd.conf:
```

authoritative;
ddns-update-style none;
option domain-name "internal";
option domain-name-servers 192.168.1.1;

default-lease-time 6000;
max-lease-time 72000;
log-facility local7;

subnet 192.168.1.0 netmask 255.255.255.0 {
# usually reserve like 10 to 20 ips for servers
  range 192.168.1.26 192.168.1.230;
  option domain-name-servers 192.168.1.1,<router-ip-address>;
  option domain-name "internal";
  option netbios-name-servers 192.168.1.1;
  option routers 192.168.1.1;
  default-lease-time 6000;
  max-lease-time 72000;
}

host routedpc {
# fill in the mac of the PC that you want port forwarding to go to
  hardware ethernet 00:11:22:33:44:55;
  fixed-address 192.168.1.100;
}

```

BIG ONE: Check that your linux pc can actually connect to the net, by going to console and typing
```
ping google.com
```
if you get some nonsense about no such host or whatever, do the following:
add in /etc/resolv.conf:
```
nameserver <dns-server-1-of-your-ISP>
nameserver <dns-server-2-of-your-ISP>
```
try again, it should work now

now just restart everything:
```
sudo /etc/init.d/networking restart
sudo /etc/init.d/dhcp3-server restart
sudo chmod 777 /etc/init.d/rc.firewall
sudo /etc/init.d/rc.firewall
```

if you want, put 
```
sudo /etc/init.d/rc.firewall
```
into /etc/rc.local, so that it'll load at boot.

Problem down. Next?

> **corkscrew said:**
> 
2. If this is possible would it slow down the internet connection for the various boxes on the LAN ?

No, depending on your network load and the speed of your ethernet cards, 
you should have 70 connectivity speed. Your linux box wont really slow down the network, unless you employ traffic shaping.


> **corkscrew said:**
> 
3. Which would the best way to be to configure the Server ie which NIC in the server would I connect the LAN to and which the router to or would it matter?
the best thing to do is attach your onboard nic to your DSL router, and the gigabit card to the switch. on my proxy at home, i have 2 pci-e cards that act as my gigabit network cards, so that i can use my onboard for a special PC (like a wifi router device or master pc or technical pc or whatever). It's up to your preference, ubuntu doesnt really care what crd you use as internal / external, as long as your firewall and dhcp3-server are configured for it.
in the above example config i gave you, the eth0 is the onboard ethernet card, and eth1 is the pci card. eth0 is configured as the external card, ie- it connects to the DSL router, and eth1 is internal and connects to the lan.

> **corkscrew said:**
> 
4. Again if this possible I have no idea how to configure the NIC's on the server to do this is there any reading or simple how to's any where to show me the way?
Yes nic configs are easy.

if your nic is connected to a DHCP server (like ubuntu dhcp server or a DSL router) and your nic is called **eth2**, you need to type the following into /etc/network/interfaces:
```
auto eth0
iface eth1 inet dhcp

```

if you want your nic to be static, and have connectivity to the network & internet via a router/proxy, use this config:
```

auto eth1
iface eth1 inet static
# address of the PC
    address <ip in the subent of your network>
# netmask of the network
    netmask <netmask of your network>
# sunet netmask, eg: in 192.168.1.1/24, 192.168.1.0
    network <subnet of the network>.0
# access to the internet :)
    gateway <ip of your gateway to the internet>
# DNS servers - so your can look up IPS.
# basically set this to your gateway and/or router, and primary ISP NS servers
    dns-nameservers <ip of the gateway>,<ip of your router (if it isn't your gateway)>,<ip of your primary ISP dns server>,<ip of your secondary ISP NS>

```

basically, this is it. seriously hope this helps. When i've got more free time, i'll post a setup for using an authenticated / non-authenticated squid proxy.
with that, you can cache files (useful when you want to save bandwidth on youtube videos or windows updates or AV updates), control internet access (like how to block porn, ads, youtube, facebook, blab blah blah...), create use access limits (like give users a monthly 'cap') and have authenticated access (like asking people for a username & PW, if they dont give it they dont get access, which helps when your company/work has a 60mbit dedicated uncapped line that is publically accessible.)

HTH

wineman

---

### Post by a2j on 2011-05-03
pretty sure you don't need a router between server and WAN (modem). server will be your router.

---

### Post by Rakeshvijayan on 2011-07-18
hello wineman I tested with you script when I use the command ```
sudo /etc/init.d/rc.firewall 
```

I cant able to connect to the internet and share is not done .when I use Iptables -L command it gives me ```
na@ns:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:25 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:pop3 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:netbios-ns 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:netbios-dgm 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:netbios-ssn 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:webmin 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:10000 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh 
LOG        tcp  --  anywhere             anywhere            tcp dpt:ssh LOG level warning prefix `external-open-port-22 ' 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:25 
LOG        tcp  --  anywhere             anywhere            tcp dpt:smtp LOG level warning prefix `external-open-port-25 ' 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:pop3 
LOG        tcp  --  anywhere             anywhere            tcp dpt:pop3 LOG level warning prefix `external-open-port-110 ' 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:fsp 
LOG        tcp  --  anywhere             anywhere            tcp dpt:ftp LOG level warning prefix `external-open-port-21 ' 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:webmin 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:10000 
LOG        tcp  --  anywhere             anywhere            tcp dpt:webmin LOG level warning prefix `external-open-port-10000 ' 
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
DROP       all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere
```


what happened it to me ....

I CHANGED THE IP IN THAT SCRIPT  THIS IS THE  ONLY EDIT I DONE ON THE SCRIPT

---

### Post by Rakeshvijayan on 2011-07-19
hello friends

---

### Post by wineman on 2011-07-20
Rakeshvijayan, hi!

ok so there are a few variables that you need to change:
1) did you set the external interface? (variable is 'ext')
2) did you set the internal interface? (variable is 'int')
3) did you set the net.ipv4.ip_forward=1 in /etc/sysctl.conf?
4) is your DNS and gateway to the IP of the ubuntu proxy?

in ubuntu, if those 4 are set, and you set your PC to dhcp (if you configured DHCP on the ubuntu box) or static IPs (with the DNS and gateway set to the IP of the ubuntu box), you **_should_** haveinternet access. try and connect to your router's webpage to test if the script is messed up or not.
Another test that you can do is the Cisco Connectivity test.
There are 4 steps in the Cisco Connectivity Test:
1) Step 1: Ping your localhost (ie- 'ping 127.0.0.1')
2) Step 2: Ping your ethernet card (ie- ping your IP address)
3) Step 3: Ping your gateway (ie- ping the ubuntu box, and then ping the router)
4) Step 4: Ping an internet address (ie 'ping google.com', because google is NEVER down)

Basically if - at any point in this test - you can't ping an address, you've found the connection problem. i think you might be having a problem in the firewall script that results from the ethernet card configurations. if you want, i'll post an automatic firewall script that sets up the routing automatically and opens (internally) the ports of services that are running and closes all the other ports and determines what ethernet card is external and internal without having to have any user input, would that be better? its a bit similar to my current firewall script but ya i mean like the one thing is go over your DNS/IP setup, and just check that the DHCP server, the DNS servers, the gateway, and the IP address of your PC are correct. then go through this setup COMPLETELY again, and fill in the details into the setup (not on ubuntu forums, but rather on your ubuntu system). If there is still a problem, i'll post another setup of a straight dhcp/iptables proxy system:)

HTH mate

---

### Post by Rakeshvijayan on 2011-07-21
Thanks for your kind words .my requirement will show this attached picture ..If it has any thing wrong please advice me to change ..

---

### Post by Rakeshvijayan on 2011-07-21
wineman from your script I checked my set up of my lan card and every thing ,that all are same as you pointed .. let me know do I need to change the name of my lan  card  /etc/network/interfaces .......I believe that this scrip do that thing
[1) did you set the external interface? (variable is 'ext')
2) did you set the internal interface? (variable is 'int')]
 ```
 # Internal interface
int="eth1"
# External interface
ext="eth0"
```

3) did you set the net.ipv4.ip_forward=1 in /etc/sysctl.conf?

```
# Note: This may impact IPv6 TCP sessions too
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
#net.ipv6.conf.all.forwarding=1


```

4) is your DNS and gateway to the IP of the ubuntu proxy?

No I need to configure dns on the internal system .I just need this server only for NAT , dhcp for this server I dont know how to .present requirement is only NAT .

I give the ip address to my eth0 eth1 as static ..dhcp from the router not enabled .

```
1) Step 1: Ping your localhost (ie- 'ping 127.0.0.1')
2) Step 2: Ping your ethernet card (ie- ping your IP address)
```
This two steps are ok for me to connect  to internet [only server pc] but can only before my system restart ...

AFTER I REINSTALL MY UBUNTU AND SEARCH FOR OTHER SCRIPT

this site help me [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router) ```
echo -e "\n\nLoading simple rc.firewall-iptables version $FWVER..\n"
DEPMOD=/sbin/depmod
MODPROBE=/sbin/modprobe

EXTIF="eth0"
INTIF="eth1"
#INTIF2="eth0"
echo "   External Interface:  $EXTIF"
echo "   Internal Interface:  $INTIF"

#======================================================================
#== No editing beyond this line is required for initial MASQ testing == 
echo -en "   loading modules: "
echo "  - Verifying that all kernel modules are ok"
$DEPMOD -a
echo "----------------------------------------------------------------------"
echo -en "ip_tables, "
$MODPROBE ip_tables
echo -en "nf_conntrack, " 
$MODPROBE nf_conntrack
echo -en "nf_conntrack_ftp, " 
$MODPROBE nf_conntrack_ftp
echo -en "nf_conntrack_irc, " 
$MODPROBE nf_conntrack_irc
echo -en "iptable_nat, "
$MODPROBE iptable_nat
echo -en "nf_nat_ftp, "
$MODPROBE nf_nat_ftp
echo "----------------------------------------------------------------------"
echo -e "   Done loading modules.\n"
echo "   Enabling forwarding.."
echo "1" > /proc/sys/net/ipv4/ip_forward
echo "   Enabling DynamicAddr.."
echo "1" > /proc/sys/net/ipv4/ip_dynaddr 
echo "   Clearing any existing rules and setting default policy.."

iptables-restore <<-EOF
*nat
-A POSTROUTING -o "$EXTIF" -j MASQUERADE
COMMIT
*filter
:INPUT ACCEPT [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]
-A FORWARD -i "$EXTIF" -o "$INTIF" -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT 
-A FORWARD -i "$INTIF" -o "$EXTIF" -j ACCEPT
-A FORWARD -j LOG
COMMIT
EOF

echo -e "\nrc.firewall-iptables v$FWVER done.\n"
```
By using this scrip I need to start that script when the system restart ....if I do so client pc can ping to my gateway of modem else no connection and but restarting the script not give me the internet its allow me to ping DNS of google 8.8.8.8 . Now I am became mad ....I need to Implement above diagram with in one month ....wineman I expect your help ....and scrips 

Thanks

---

### Post by Rakeshvijayan on 2011-07-21
By using the above scrip response from the clint side 


```
clint network configurarion 
server@ns:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:19:d1:97:45:c8  
          inet addr:200.119.2.50  Bcast:200.119.2.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe97:45c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:144354 (144.3 KB)  TX bytes:120631 (120.6 KB)
          Interrupt:41 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3912 (3.9 KB)  TX bytes:3912 (3.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:b0:66:38:d8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)





ping to [self] clint address

server@ns:~$ ping 200.119.2.50
PING 200.119.2.50 (200.119.2.50) 56(84) bytes of data.
64 bytes from 200.119.2.50: icmp_req=1 ttl=64 time=0.039 ms
64 bytes from 200.119.2.50: icmp_req=2 ttl=64 time=0.028 ms
64 bytes from 200.119.2.50: icmp_req=3 ttl=64 time=0.031 ms
^Z
[2]+  Stopped                 ping 200.119.2.50
server@ns:~$ clear



ping to server gateway eth1 address

server@ns:~$ ping 200.119.2.1
PING 200.119.2.1 (200.119.2.1) 56(84) bytes of data.
64 bytes from 200.119.2.1: icmp_req=1 ttl=64 time=0.289 ms
64 bytes from 200.119.2.1: icmp_req=2 ttl=64 time=0.376 ms
64 bytes from 200.119.2.1: icmp_req=3 ttl=64 time=0.201 ms
64 bytes from 200.119.2.1: icmp_req=4 ttl=64 time=0.216 ms
64 bytes from 200.119.2.1: icmp_req=5 ttl=64 time=0.301 ms

^Z
[1]+  Stopped                 ping 200.119.2.1






ping to server eth0 ip 

server@ns:~$ ping 192.168.1.155
PING 192.168.1.155 (192.168.1.155) 56(84) bytes of data.
64 bytes from 192.168.1.155: icmp_req=1 ttl=64 time=0.272 ms
64 bytes from 192.168.1.155: icmp_req=2 ttl=64 time=0.336 ms
64 bytes from 192.168.1.155: icmp_req=3 ttl=64 time=0.256 ms
64 bytes from 192.168.1.155: icmp_req=4 ttl=64 time=0.341 ms
^Z
[3]+  Stopped                 ping 192.168.1.155
server@ns:~$ clear






ping to eth0 gateway [ modem] 



server@ns:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=127 time=1.79 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=127 time=1.22 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=127 time=0.559 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=127 time=1.31 ms
64 bytes from 192.168.1.1: icmp_req=5 ttl=127 time=0.588 ms
64 bytes from 192.168.1.1: icmp_req=6 ttl=127 time=1.34 ms

^Z
[5]+  Stopped                 ping 192.168.1.1
server@ns:~$ clear

replay from google dns

server@ns:~$~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=53 time=83.9 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=53 time=81.7 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=53 time=153 ms
64 bytes from 8.8.8.8: icmp_req=4 ttl=53 time=219 ms
^Z
[1]+  Stopped                 ping 8.8.8.8

server@ns:~$


server@ns:~$ ping www.google.com
ping: unknown host www.google.com
server@ns:~$ ping yahoo.com
ping: unknown host yahoo.com
server@ns:~$ 
```iptables -L result of the server

---

### Post by Rakeshvijayan on 2011-07-21
talks@ns1:~$ sudo tail -f /var/log/messages
[sudo] password for talks: 
Jul 21 12:48:26 ns1 kernel: [12314.319572] sd 7:0:0:0: [sdc] 7811072 512-byte logical blocks: (3.99 GB/3.72 GiB)
Jul 21 12:48:26 ns1 kernel: [12314.324569] sd 7:0:0:0: [sdc] Write Protect is off
Jul 21 12:48:26 ns1 kernel: [12314.341579]  sdc: sdc1
Jul 21 12:48:26 ns1 kernel: [12314.397598] sd 7:0:0:0: [sdc] Attached SCSI removable disk
Jul 21 13:06:37 ns1 kernel: [13404.940715] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 21 13:06:37 ns1 kernel: [13404.944307] e100 0000:04:05.0: eth0: NIC Link is Up 100 Mbps Full Duplex
Jul 21 13:06:37 ns1 kernel: [13404.944889] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jul 21 13:06:37 ns1 kernel: [13405.371195] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jul 21 13:06:38 ns1 kernel: [13406.544373] e1000: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jul 21 13:06:38 ns1 kernel: [13406.544674] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready

---

### Post by wineman on 2011-07-21
ok so i like what you've done but the one thing that i still dont like is how this system doesnt have any DNS configured on eth0. you have to specify your DNS servers. To specify them, please add this line to your config of eth0 in /etc/network/interfaces:
#START
dns-nameservers <ip of name server 1>,<ip of name server 2>
#END
This will allow your server to connect DIRECTLY to the internet itself. 
Something else that is bothering me about your network map is that the system seems to be running SQUID, yet (to the best of my knowledge) squid hasn't been configured, and i haven't accounted for it in the firewall. Please remove it for now (unless it is configured), we can set this up once the systems are able to access the internet from a client side.
To get this script (the one that you got from the Router page) to load at boot, please do the following:
1) Save to the file as /etc/init.d/fw.starter
2) run this command:
chmod 777 /etc/init.d/fw.starter
3) add the following line to /etc/rc.local, just above the 'exit 0' part:
sh /etc/init.d/fw.starter
4) Please change the following lines in my firewall script:
#START
for opf in $opforwards
do 
$ipt -A FORWARD -i $ext -o $int -p tcp --dport $opf-j ACCEPT
$ipt -t nat -A PREROUTING -i $ext -p tcp --dport $opf -j DNAT --to $ip:$opf
done
#END
to
#START
for opf in $opforwards
do 
$ipt -A FORWARD -i $ext -o $int -p tcp --dport $opf -j ACCEPT
$ipt -t nat -A PREROUTING -i $ext -p tcp --dport $opf -j DNAT --to $ip:$opf
done
#END
This corrects the system for port forwarding errors that mess up when the script loads.

5) restart your server to test if this script runs. Now both my firewall script and the Router script will run and so you should get connectivity. 

If this doesnt work, there is a system that i use at home and it's very simple to configure and lock down, it is called Zentyal ([http://www.zentyal.org](http://www.zentyal.org)) and it is very good, its a fulyl functional DMZ/UTM/UMS/UOS and is very reliable, the versin 2.0 is completely stable and should work perfectly for your application. It is also free and based on ubuntu. 
Still, im more than happy to help with everything and anything that pertains to your project:)
Your system does have a few flaws, but lets rather get it working 100% and then sort out the problems.

HTH

---

### Post by Rakeshvijayan on 2011-07-22
Hi friend finally that router scrip is work for me and am happy 


```
[hem, please add this line to your config of eth0 in /etc/network/interfaces:
#START
dns-nameservers <ip of name server 1>,<ip of name server 2>
#END
```

I don't know how its work for me I can access internet with out specify dns-nameservers on eth0 

```
#START
for opf in $opforwards
do 
$ipt -A FORWARD -i $ext -o $int -p tcp --dport $opf-j ACCEPT
$ipt -t nat -A PREROUTING -i $ext -p tcp --dport $opf -j DNAT --to $ip:$opf
done
#END
to
#START
for opf in $opforwards
do 
$ipt -A FORWARD -i $ext -o $int -p tcp --dport $opf -j ACCEPT
$ipt -t nat -A PREROUTING -i $ext -p tcp --dport $opf -j DNAT --to $ip:$opf
done
#END
```is this both are the same script ...On that router script says about log ...where I can find the log and how its work ...and I need to know on the dns part of the client pc I give server's eth1 ip is given first time this not give the connection to internet when I give eth1 gateway connection ok for me .Is this is any wrong ..

Thank for the information of Zentyal ..but I give my hands on ubuntu ....I need to learn ubuntu ...I know I cnt study whole ...

I need to run your scrip also ...this is my 14th day on this issue but your words give me more courage ..

This is the whole thing I did on my system ```

      echo -e "\n\nLoading simple rc.firewall-iptables version $FWVER..\n"
      DEPMOD=/sbin/depmod
      MODPROBE=/sbin/modprobe

      EXTIF="eth0"
      INTIF="eth1"
      #INTIF2="eth0"
      echo "   External Interface:  $EXTIF"
      echo "   Internal Interface:  $INTIF"

      #======================================================================
      #== No editing beyond this line is required for initial MASQ testing == 
      echo -en "   loading modules: "
      echo "  - Verifying that all kernel modules are ok"
      $DEPMOD -a
      echo "----------------------------------------------------------------------"
      echo -en "ip_tables, "
      $MODPROBE ip_tables
      echo -en "nf_conntrack, " 
      $MODPROBE nf_conntrack
      echo -en "nf_conntrack_ftp, " 
      $MODPROBE nf_conntrack_ftp
      echo -en "nf_conntrack_irc, " 
      $MODPROBE nf_conntrack_irc
      echo -en "iptable_nat, "
      $MODPROBE iptable_nat
      echo -en "nf_nat_ftp, "
      $MODPROBE nf_nat_ftp
      echo "----------------------------------------------------------------------"
      echo -e "   Done loading modules.\n"
      echo "   Enabling forwarding.."
      echo "1" > /proc/sys/net/ipv4/ip_forward
      echo "   Enabling DynamicAddr.."
      echo "1" > /proc/sys/net/ipv4/ip_dynaddr 
      echo "   Clearing any existing rules and setting default policy.."

      iptables-restore <<-EOF
      *nat
      -A POSTROUTING -o "$EXTIF" -j MASQUERADE
      COMMIT
      *filter
      :INPUT ACCEPT [0:0]
      :FORWARD DROP [0:0]
      :OUTPUT ACCEPT [0:0]
      -A FORWARD -i "$EXTIF" -o "$INTIF" -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT 
      -A FORWARD -i "$INTIF" -o "$EXTIF" -j ACCEPT
      -A FORWARD -j LOG
      COMMIT
      EOF

      echo -e "\nrc.firewall-iptables v$FWVER done.\n"

After configuring the 2 variables, save the script below as nat.sh and make it executable by doing

    *

      chmod a+x nat.sh


now change the value of this in /etc/sysctl.conf:
Code:

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1



Now, test the script by running as root

    *




      sudo sh nat.sh





    *

If ping responds, make our new script bootable so we don't have to run the script every time we restart.

    *

      sudo cp nat.sh /etc/init.d/
      sudo ln -s /etc/init.d/nat.sh /etc/rc2.d/S95masquradescript

As a final test, restart your computer and test to see if you still have the same functionality. If so then congratulations! If not then make sure you followed the above correctly so the script is bootable.

sudo iptables-save > /etc/iptables.up.rules

do like this in /etc/network/interfaces

auto lo
iface lo inet loopback
pre-up iptables-restore < /etc/iptables.up.rules


auto eth0
iface eth0 inet static
address 192.168.1.155
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1


auto eth1
iface eth1 inet static
address 200.119.2.1
netmask 255.255.255.0
network 200.119.2.0
broadcast 200.119.2.255
dns-nameservers 192.168.1.1

```
Be frank wineman I dont know how Its work for me ..I am going to test it on virtual box

---

### Post by wineman on 2011-07-22
ok you're doing the right thing :) YAY :D This system works.

The configuration for the statically assigned IPs is as follows:
(and yay i finally remembered how to create 'code' tags :D)
```
IP ADDRESS: 200.119.2.<number>
(Subnet mask or) NETMASK: 255.255.255.0
DEFAULT GATEWAY: 200.119.2.1
PREFERRED DNS SERVER: 200.119.2.1
ALTERNATE DNS SERVER: 192.168.1.1

```
Basically, you need to set the DNS servers to the IP of the NAT server and the IP of the router but ONLY on the client.
The DHCP Config for that would be something like this:

```
authoritative;
server-identifier           mathacollege.internal;
ddns-updates                off;
# The reason that the domain name is mathacollege.internal is
# so that the client do not become broadcast on the internet,
# as mathacollege.internal is a an illegal TLD Domain name
option domain-name "mathacollege.internal";
option domain-name-servers 200.119.2.1;

default-lease-time 6000;
max-lease-time 72000;
log-facility local7;

subnet 200.119.2.0 netmask 255.255.255.0 {
  range 200.119.2.25 200.119.250;
  option domain-name-servers 200.119.2.1,192.168.1.1;
  option domain-name "mathacollege.internal";
  option ip-forwarding off;
  option netbios-dd-servers 200.119.2.1;
  option netbios-name-servers 200.119.2.1;
  option routers 200.119.2.1;
  option broadcast-address 200.119.2.255;
  default-lease-time 6000;
  max-lease-time 72000;
}

subnet 192.168.1.0 netmask 255.255.255.0 {}
```

This should direct the clients to your system's NAT server, i hope this helps somehow. Copy the above settings into the DHCP server's config file and then restart it ('service dhcp3-server restart') and then try and connect to the internet again from your client. 
A Virtual-box is a brilliant idea for a client, as it is isolated and can be broken and destroyed and then rebuilt in a matter of seconds. I use them for server development at home sometimes, although i prefer a real physical box to one of them for server technology.
i like the steps that you took to make that nat script work.

you also asked about the log,everything that iptables logs is saved in either syslog or messages (syslog in ubuntu, which is /var/log/syslog; messages is in RPM systems like redhat or mandriva or fedora, which is /var/log/messages) under lines similar to this:

```
Jul 22 11:26:27 iptables rules="" in="eth0" out="eth1" proto="tcp"....
```

it looks fairly similar to that, with the application header or either "iptables" or "kernel". sometimes the system will spew out messages based on the kernel or the kernel subsystem (which runs iptables). 

HTH

---

