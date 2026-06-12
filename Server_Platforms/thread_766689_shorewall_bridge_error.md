---
title: "shorewall bridge error"
date: 2008-04-25
forum: Server Platforms
---

### Post by sitedesign on 2008-04-25
When I "shorewall clear" the server works as a bridge perfect.

I have set-up a server as a shorewall bridging firewall but get an error when starting:

```
Starting Shorewall....
Initializing...
Clearing Traffic Control/QOS
Deleting user chains...
Enabling Loopback and DNS Lookups
Creating Interface Chains...
Setting up SMURF control...
Setting up Black List...
Setting up ARP filtering...
Setting up Route Filtering...
Setting up Accept Source Routing...
IP Forwarding Enabled
Setting up SYN Flood Protection...
Setting up Rules...
Setting up Actions...
Creating action chain Drop
Creating action chain Reject
Creating action chain dropBcast
Creating action chain dropInvalid
Creating action chain dropNotSyn
Applying Policies...
Activating Rules...
iptables: Invalid argument
   ERROR: Command "/sbin/iptables -A OUTPUT -o br0 -j br0_out" Failed
```

My shorewall interfaces file:
```
-	br0		detect		routefilter
```

My shorewall hosts file:
```
#ZONE		HOST(S)		OPTIONS
net		br0:eth0
loc		br0:eth1
```

My shorewall zones file:
```
fw	firewall
net	ipv4
loc	ipv4
```

My shorewall conf file has bridging enabled

My network interfaces file:
```
auto br0
iface br0 inet static
	address		*my public IP*
	network		*my public network*
	netmask		255.255.255.192
	gateway		*my public gateway*
	pre-up		ifconfig eth0 down
	pre-up		ifconfig eth1 down
	pre-up		brctl addbr br0
	pre-up		brctl addif br0 eth0
	pre-up		brctl addif br0 eth1
	pre-up		ifconfig eth0 0.0.0.0
	pre-up 		/usr/sbin/ethtool -s eth0 speed 10 duplex full autoneg off
	pre-up		ifconfig eth1 0.0.0.0
	pre-up 		/usr/sbin/ethtool -s eth1 speed 10 duplex full autoneg off
	post-down	ifconfig eth1 down
	post-down	ifconfig eth0 down
	post-down	ifconfig br0 down
	post-down	brctl delif br0 eth1
	post-down	brctl delif br0 eth0
	post-down	brctl delbr br0
```

Any help would be much appreciated.

Regards Peter King

---

### Post by kosc on 2008-10-29
I have same problem, here is link that I followed
[http://www.shorewall.net/4.0/bridge.html]("http://www.shorewall.net/4.0/bridge.html")

PC box have 2 ETH (eth0 and eth1) and ubuntu 8.04.1 LTS
newest shorewall & bridge-utils is installed 
[COLOR="DarkRed"]shorewall-shell/hardy uptodate 4.0.6-1
shorewall/hardy uptodate 4.0.6-1
shorewall-common/hardy uptodate 4.0.6-1
bridge-utils/hardy uptodate 1.2-2
[/COLOR]
**here is /etc/network/interface**
[COLOR="DarkRed"]auto lo
iface lo inet loopback

auto br0
iface br0 inet static
 address 192.168.1.9
 netmask 255.255.255.0
 gateway 192.168.1.1
 bridge-ports eth0 eth1
 bridge_maxwait 0
 pre-up /sbin/ip link set eth0 up
 pre-up /sbin/ip link set eth1 up
 pre-up /usr/sbin/brctl addbr br0
 pre-up /usr/sbin/brctl addif br0 eth0
 pre-up /usr/sbin/brctl addif br0 eth1[/COLOR]

**/etc/shorewall/interfaces**
[COLOR="DarkRed"]-       br0             192.168.1.255
[/COLOR]
**/etc/shorewall/policy**
[COLOR="DarkRed"]loc             net             ACCEPT
net             all             DROP            info
all             all             REJECT          info[/COLOR]

**/etc/shorewall/zones**
[COLOR="DarkRed"]fw      firewall
net     ipv4
loc     ipv4[/COLOR]

**/etc/shorewall/hosts**
[COLOR="DarkRed"]net     br0:eth0
loc     br0:eth1[/COLOR]

**/etc/shorewall/shorewall.conf**
[COLOR="DarkRed"]BRIDGING=Yes[/COLOR]

**/etc/shorewall/routestopped**
[COLOR="DarkRed"]br0             192.168.1.0/24          routeback[/COLOR]

bridge is working fine but when shorewall is started, there are errors.
**/var/log/syslog**
[COLOR="DarkRed"]Oct 29 08:54:46 router kernel: [   42.346739] physdev match: using --physdev-out in the OUTPUT, FORWARD and POSTROUTING chains for non-bridged traffic is not supported anymore.
Oct 29 08:54:46 router kernel: [   42.346739] physdev match: using --physdev-out in the OUTPUT, FORWARD and POSTROUTING chains for non-bridged traffic is not supported anymore.
Oct 29 08:54:46 router kernel: [   42.346739] physdev match: using --physdev-out in the OUTPUT, FORWARD and POSTROUTING chains for non-bridged traffic is not supported anymore.
...[/COLOR]

**var/log/shorewall-init.log**
...
[COLOR="DarkRed"]08:54:45 Setting up Actions...
08:54:45 Creating action chain Drop
08:54:45    Rule "REJECT - - tcp 113 -  - " added.
08:54:45    Rule "dropBcast        " added.
08:54:45    Rule "ACCEPT - - icmp fragmentation-needed -  - " added.
08:54:45    Rule "ACCEPT - - icmp time-exceeded -  - " added.
08:54:45    Rule "dropInvalid        " added.
08:54:45    Rule "DROP - - udp 135,445 -  - " added.
08:54:45    Rule "DROP - - udp 137:139 -  - " added.
08:54:45    Rule "DROP - - udp 1024: 137  - " added.
08:54:45    Rule "DROP - - tcp 135,139,445 -  - " added.
08:54:45    Rule "DROP - - udp 1900 -  - " added.
08:54:45    Rule "dropNotSyn - - tcp     " added.
08:54:45    Rule "DROP - - udp - 53  - " added.
08:54:45 Creating action chain Reject
08:54:45    Rule "REJECT - - tcp 113 -  - " added.
08:54:45    Rule "dropBcast        " added.
08:54:45    Rule "ACCEPT - - icmp fragmentation-needed -  - " added.
08:54:45    Rule "ACCEPT - - icmp time-exceeded -  - " added.
08:54:45    Rule "dropInvalid        " added.
08:54:45    Rule "REJECT - - udp 135,445 -  - " added.
08:54:45    Rule "REJECT - - udp 137:139 -  - " added.
08:54:45    Rule "REJECT - - udp 1024: 137  - " added.
08:54:45    Rule "REJECT - - tcp 135,139,445 -  - " added.
08:54:45    Rule "DROP - - udp 1900 -  - " added.
08:54:45    Rule "dropNotSyn - - tcp     " added.
08:54:45    Rule "DROP - - udp - 53  - " added.
08:54:45 Creating action chain dropBcast
08:54:45 Creating action chain dropInvalid
08:54:45 Creating action chain dropNotSyn
08:54:45 Applying Policies...
08:54:45 Activating Rules...
[B]iptables: Invalid argument
   ERROR: Command "/sbin/iptables -A OUTPUT -o br0 -j br0_out" Failed[/B]
08:54:45 Processing /etc/shorewall/stop ...
08:54:45 Processing /etc/shorewall/stopped ...
Terminated
[/COLOR]

---

### Post by kosc on 2008-11-03
Thanks to Damir Jurica from infosol and Tom Eastep from shorewall, for pointing me in right direction. This is good URL [http://www.shorewall.net/3.0/bridge.html]("http://www.shorewall.net/3.0/bridge.html")

Since kernel 2.6.20. the physdev match capability was reduced in function to the point where in can no longer be used for Shorewall zone definition, see [http://www.shorewall.net/3.0/NewBridge.html]("http://www.shorewall.net/3.0/NewBridge.html")

in short this is what I changed:

**/etc/shorewall/shorewall.conf**
[COLOR="DarkRed"]IP_FORWARDING=On
BRIDGING=No
IMPLICIT_CONTINUE=Yes[/COLOR]

**/etc/shorewall/interfaces**
[COLOR="DarkRed"]net     br0    192.168.1.255   routeback[/COLOR]

**/etc/shorewall/hosts**
[COLOR="DarkRed"]loc  br0:192.168.1.11,192.168.1.10[/COLOR]

Set policy to what you like
**/etc/shorewall/policy**
[COLOR="DarkRed"]loc  net    ACCEPT
net  loc    ACCEPT
all  all    REJECT          info[/COLOR]

**/etc/shorewall/hosts**
[COLOR="DarkRed"]loc  br0:192.168.1.11,192.168.1.10[/COLOR]

**/etc/shorewall/zones**
[COLOR="DarkRed"]fw           firewall
net          ipv4
loc:net      ipv4
[/COLOR]

this error is reported in **/var/log/syslog** even bridge and shorewall works fine.
[COLOR="DarkRed"]br0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.[/COLOR]

I found on net that this could be error in **bridge-utils** [https://bugs.launchpad.net/ubuntu/+source/bridge-utils/+bug/274298]("https://bugs.launchpad.net/ubuntu/+source/bridge-utils/+bug/274298")

---

