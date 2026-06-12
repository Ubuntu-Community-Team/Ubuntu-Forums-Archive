---
title: "Cannot ping between Subnets"
date: 2015-12-06
forum: Server Platforms
---

### Post by Barry_Robinson on 2015-12-06
Hi all,

Im totally new to Linux and would appreciate some help. Im basically using a Linux PC as my main router. I have 2 NIC cards and a wifi card installed. Eth1 is connected to my cable modem. Wlan0 is my Access Point and Eth0 plugs into a switch. I did try to bridge Wlan0 and Eth0 and use isc-dhcp-server but could not get this to work. I then set up different subnets for wlan0 and eth0 in dhcp.conf. Everything works fine. Dhcp assigns addresses to Wifi and Wired devices and both can connect to the internet. However the problem is the subnets wont talk to each other. I cannot ping between them. So my wireless devices cannot see my wired NAS for example. I have been checking online but couldn't find anything that worked. I believe its something to do with adding a route.


This is my /etc/network/interfaces file
```

auto loiface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto wlan0
iface wlan0 inet static
        address 10.1.1.1
        netmask 255.255.255.0

auto eth0
iface eth0 inet static
        address 10.1.2.1
        netmask 255.255.255.0

```


And this is my dhcp/dhcpd.config file
```
ddns-update-style none;

authoritative;


log-facility local7;


default-lease-time 86400;
max-lease-time 84600;


# eth0 subnet configuration
subnet 10.1.2.0 netmask 255.255.255.0 {
        range 10.1.2.31 10.1.2.61;
        option routers 10.1.2.1;
        option subnet-mask 255.255.255.0;
        option domain-name-servers 10.1.2.1, 8.8.8.8;
        option broadcast-address 10.1.2.255;
}


# wlan0 subnet configuration
subnet 10.1.1.0 netmask 255.255.255.0 {
        range 10.1.1.10 10.1.1.30;
        option routers 10.1.1.1;
        option subnet-mask 255.255.255.0;
        option domain-name-servers 10.1.1.1, 8.8.8.8;
        option broadcast-address 10.1.1.255;
}
```

Please can anyone help:D
Barry

---

### Post by matt_symes on 2015-12-06
Hi

Welcome to the forums :)

I'm not sure if this is the best forum for your query so I'm moving it to **Server Platforms**. 

I'll leave an expiring redirect for you in 'Networking & Wireless' as well so people can look from there.

> I have been checking online but couldn't find anything that worked. 

Can you detail what you have tried so far.

On the router, please post the output of

```
route -n
```

```
cat  /proc/sys/net/ipv4/ip_forward
```

```
sudo iptables -L -t nat
```

Kind regards

---

### Post by darkod on 2015-12-06
Yes, adding a route is probably what will be needed, but if you want to go a step back and try the bridge again, I could be able to give you some pointers. I haven't tried a two interface bridge so far, but some months ago I needed a single interface bridge and after gathering info on the internet here is how I did it. I will adjust it for your eth0 and wlan0 situation. Here is what you could try in /etc/network/interfaces:
```
auto wlan0
iface wlan0 inet manual

auto eth0
iface eth0 inet manual

# My bridge interface
auto br0
iface br0 inet static
   address 10.1.1.1
   netmask 255.255.255.0
   bridge_ports eth0 wlan0
   bridge_fd 9
   bridge_hello 2
   bridge_maxage 12
   bridge_stp off
```

Those are the values used in my bridge, except that in bridge_ports I have only eth0. I'm not sure if any other parameter needs to be changed when using two interfaces. But you can try it like that first.

After you have done that bridging, the only interface to use is br0 and its IP 10.1.1.1. You forget about eth0 and wlan0, same like they don't even exist. So if it works, you will have to adjust your dhcp settings, etc... Every configuration where the interface is mentioned.

PS. According to this you will need to install the bridge-utils package in case you already haven't. And it seems the bridge_ports and bridge_stp parameters are enough to try and use it. [http://theurbanpenguin.com/wp/index.php/ubuntu-server-creating-a-bridge-interface/](http://theurbanpenguin.com/wp/index.php/ubuntu-server-creating-a-bridge-interface/)

---

### Post by SeijiSensei on 2015-12-06
Did you enable packet forwarding in /etc/sysctl.conf?  If not, edit that file with sudo and remove the hash mark from the line
```
net.ipv4.ip_forward=1
```
and then reboot.  By default Ubuntu does not forward traffic across interfaces as a security measure.

I almost never use bridging; I much prefer to use static routes.  My guess is that the problem is just that IP forwarding is disabled, and you shouldn't need to change the configuration of the interfaces at all nor add any special routes.

---

### Post by darkod on 2015-12-06
But he said both wired (eth0) and wireless (wlan0) dhcp clients have internet access. That would imply forwarding is enabled because they need to go out through eth1. No? With forwarding disabled a box can't serve as a router at all, and in this case that seems to work.

It's only the routing between eth0 and wlan0 subnets. Or probably only a static route needed...

---

### Post by Barry_Robinson on 2015-12-06
Hi Guys,

Thanks for the quick replies.

Matt here is the outputs of the files you requested.

Route -n
```
Kernel IP routing tableDestination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         92.238.97.1     0.0.0.0         UG    0      0        0 eth1
10.1.1.0        0.0.0.0         255.255.255.0   U     0      0        0 wlan0
10.1.2.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
92.238.97.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
```


cat /proc/sys/net/ipv4/ip_forward
```
1
```


Iptables
```
Chain PREROUTING (policy ACCEPT)target     prot opt source               destination


Chain INPUT (policy ACCEPT)
target     prot opt source               destination


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
MASQUERADE  all  --  anywhere             anywhere
```

I have bridge-utils installed Darkod and had the interfaces set up as you have but the bridge never included the wlan0 and dhcp would not give out IP's. Thought this way was much simpler apart from the subnets not talking. Like I said both can connect to the internet but not to each other.

Cheers,
Barry

---

### Post by volkswagner on 2015-12-06
A properly configured router should need explicit rules to allow the traffic you are requesting.

If iptables is your only firewall please post output of the following. (you can mask public ip addresses, but private addresses need to be viewable):
```
iptables -L -n
```

Also I generally like to provide "network" and "broadcast" info for static ip configurations (like example below):

```
auto wlan0
iface wlan0 inet static
        address 10.1.1.1
        netmask 255.255.255.0
        network 10.1.1.0
        broadcast 10.1.1.255
auto eth0
iface eth0 inet static
        address 10.1.2.1
        netmask 255.255.255.0
        network 10.1.2.0
        broadcast 10.1.2.255

```

---

### Post by matt_symes on 2015-12-07
Hi

IP forwarding is set up on the router PC along with masquerading so that is all configured correctly. I did expect this to be the case as both subnets can access the Internet but i have learnt over the years to double check everything :).

> **Barry_Robinson said:**
> Hi Guys,

Thanks for the quick replies.

Matt here is the outputs of the files you requested.

Route -n
```
Kernel IP routing tableDestination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         92.238.97.1     0.0.0.0         UG    0      0        0 eth1
10.1.1.0        0.0.0.0         255.255.255.0   U     0      0        0 wlan0
10.1.2.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
92.238.97.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
```

I'm really no expert at this however....

Currently all your subnet traffic is being routed out the default gateway so, as you said, it looks like you need to add two static routes, one for each internal subnet, to route traffic to the other internal subnet over the correct interface.

For a quick test, let's add them using the route command on your router PC. 

```
sudo route add -net 10.1.2.0 netmask 255.255.255.0 gw 10.1.2.1
sudo route add -net 10.1.1.0 netmask 255.255.255.0 gw 10.1.1.1
```

Then try to ping between the two subnets.

Does this work ?

Kind regards

---

### Post by Barry_Robinson on 2015-12-07
Hi Guys,

Volkswagner, here is the output from iptables -L -n.

```
Chain INPUT (policy ACCEPT)target     prot opt source               destination


Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
LOG        all  --  0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 4
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

Not sure why all addresses are 0. 

I basically downloaded a script from the web. Here is the script.
```
FWVER= 0.76

echo -e "\n\nLoading simple rc.firewall-iptables version $FWVER..\n"




IPTABLES=/sbin/iptables
DEPMOD=/sbin/depmod
MODPROBE=/sbin/modprobe




EXTIF="eth1"
INTIF="wlan0"
INTIF2="eth0"
echo "   External Interface:  $EXTIF"
echo "   Internal Interface:  $INTIF"
echo "   Internal Interface:  $INTIF2"


EXTIP="your external IP address"
echo "   External IP:  $EXTIP"


echo -en "   loading modules: "


echo "  - Verifying that all kernel modules are ok"
$DEPMOD -a


echo -en "ip_tables, "
$MODPROBE ip_tables


echo -en "ip_conntrack, "
$MODPROBE ip_conntrack


echo -en "ip_conntrack_ftp, "
$MODPROBE ip_conntrack_ftp


echo -en "ip_conntrack_irc, "
$MODPROBE ip_conntrack_irc


echo -en "iptable_nat, "
$MODPROBE iptable_nat


echo -en "ip_nat_ftp, "
$MODPROBE ip_nat_ftp


echo -e "   Done loading modules.\n"


echo "   Enabling forwarding.."


echo "1" > /proc/sys/net/ipv4/ip_forward


echo "   Enabling DynamicAddr.."
echo "1" > /proc/sys/net/ipv4/ip_dynaddr


echo "   Clearing any existing rules and setting default policy.."
$IPTABLES -P INPUT ACCEPT
$IPTABLES -F INPUT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -F OUTPUT
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD
$IPTABLES -t nat -F


echo "   FWD: Allow all connections OUT and only existing and related ones IN"
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
$IPTABLES -A FORWARD -j LOG
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF2 -m state --state ESTABLISHED,RELATED \-j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $INTIF2 -m state --state ESTABLISHED,RELATED \-j ACCEPT
$IPTABLES -A FORWARD -i $INTIF2 -o $INTIF -m state --state ESTABLISHED,RELATED \-j ACCEPT
$IPTABLES -A FORWARD -i $INTIF2 -o $EXTIF -j ACCEPT
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP
echo "   Enabling SNAT (MASQUERADE) functionality on $EXTIF"


$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE


echo -e "\nrc.firewall-iptables v$FWVER done.\n"



```

Then I saved this as nat.sh in /etc/init.d/. I then created a symbolic link to this from /etc/rc2.d/S95masquradescript. I assume this script gets run on start up but not sure.

Have also tried adding the routes as suggested by Darkod but still no luck.

Also I have just lost internet access through wlan0 although eth0 is still OK

---

### Post by matt_symes on 2015-12-07
> **Barry_Robinson said:**
> 
...
Not sure why all addresses are 0. 


That will match any IP address.

> Then I saved this as nat.sh in /etc/init.d/. I then created a symbolic link to this from /etc/rc2.d/S95masquradescript. I assume this script gets run on start up but not sure.

That's a pretty old way to start a script (sysV init). Both upstart and systemd have superseded it but it should still work for the moment.

The script will not solve your routing problem between the two subnets though.

> Have also tried adding the routes as suggested by Darkod but still no luck.

Which routes were these ?

> Also I have just lost internet access through wlan0 although eth0 is still OK

I would just concentrate on getting routing between the two subnets working. Don't complicate things with firewall rules until that is fixed. Test at each step.

I found a web page that looks to mimic your setup.

[http://www.thegeekstuff.com/2012/04/route-examples/](http://www.thegeekstuff.com/2012/04/route-examples/)

Kind regards

---

### Post by Barry_Robinson on 2015-12-08
I tried adding 2 routes as suggested by Darkod and also from the site Volkswagner suggested. These were,
```

sudo route add -net 10.1.1.0 netmask 255.255.255.0 gw 10.1.1.1
sudo route add -net 10.1.2.0 netmask 255.255.255.0 gw 10.1.2.1

```

Unfortunately still no luck.

I did manage to sort out the Wifi not accessing the internet. I must have cut out a line from my nat.sh script by mistake.

Going back to the script, I would have thought these lines would allow forwarding between the subnets. Although I must admit I'm not entirely sure what they are doing.
```

$IPTABLES -A FORWARD -i $INTIF -o $INTIF2 -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF2 -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT



```

---

### Post by newbie-user on 2015-12-08
The static routes should be done on the clients, not on the router, as the router already knows the routes. As for iptables, I think it might be complicating your troubleshooting. I would recommend flushing iptables, try to get the routing done correctly first, then reapply iptables after the routing works. Also, I would think that iptables should be done only for the EXTIF, assuming you trust both your subnets. Just make sure you've enabled masquerading.

---

### Post by darkod on 2015-12-09
I was also thinking about iptables and this troubleshooting. I would recommend changing the FORWARD policy to ACCEPT temporarily, that will at least discard iptables rules as possible issue in the routing.
And instead of that script you found you may consider alternative way to load your rules on boot. For example most people these days use a command in /etc/network/interfaces with which you can tell the OS to use iptables-restore and load rules from a file as soon as the interface is up. For example, in the eth1 definition you can use something like:
```
post-up iptables-restore < /etc/iptables.rules
```

Then you create the /etc/iptables.rules file which contains only the rules and policies you need. It's much cleaner and understandable.

As for the routing and the static routes, I still fail to figure out the problem. Even if clients do not have static routes, shouldn't they send the packets to its default GW? In this case that's the ubuntu server box you have connected to the internet and the two internal networks. Once the packets reach there, that box knows where to forward them, no? So why would any static routes be needed?

---

### Post by Barry_Robinson on 2015-12-10
Well eventually gave up. I did manage to sort out pinging between the subnets by setting up FORWARD rules in IPTABLES. It was dropping the pings. However I still could not locate my NAS on the other subnet and my Virgimedia Tivo could not see my remote App on my phone.

So i spent £30 on a TP-link Wireless AP and plugged it into my switch. Now everything is on the same subnet and works fine.

Just want to say a big thank you for all your suggestions. I have certainly learned a lot about Linux in the few weeks since I started this. Next up, trying to set up a VPN. Will no doubt be back on the forum asking more questions when I get stuck:p 

Cheers,
Barry

---

