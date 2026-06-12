---
title: "DHCP and Static IP's dual NIC's"
date: 2010-08-28
forum: Server Platforms
---

### Post by dtoronto on 2010-08-28
I'm have a number of ubuntu servers that all have dual nics.  One interface is used to assign a static public ip and the other is used to assign a static internal IP that can be used on the internal network.  The interfaces pull IP's from completely separate gateways on different networks.  The problem I face now it that our internal network is moving everything to DHCP on the internal side.  I can configure my /etc/network/interfaces so that I can get a public static Ip and a private DCHP, but the problem is that the public IP no longer functions for any services.

here is an example of my interfaces

```
# The primary network interface
auto eth0
iface eth0 inet dhcp

# The secondary public network interface
auto eth1
iface eth1 inet static
address 184.65.224.65
netmask 255.255.255.248
network 184.65.224.64
broadcast 184.65.224.71
gateway 184.65.224.70

```

my internal dhcp pulls down 192.168.1.10 from gateway 192.168.1.1

I can access the servers services on the internal side, but I need to be able to have the services on the public side too.  Any help is greatly appreciated here.  

Also I have tried setting up a static route using 

```
sudo route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.1.10 dev eth1
```
but my outside interface still has no service

Also, both networks are connected to the internet, however I would like to force all network traffic on these servers out over the public interface (eth1).  I believe that the static routes should fix that though once i get both interfaces working.

---

### Post by anchise on 2010-08-28
The problem seems to be the config auf eth1.
Your netmask is 32bit. Change it to 24bit (255.255.255.0) and it should work IMHO.

---

### Post by dtoronto on 2010-08-28
Tried that, I've set it up as a 255.255.255.0, still no success, thanks for the input though

---

### Post by dtoronto on 2010-08-28
bump

---

### Post by Xipher on 2010-08-28
I don't know how to do this in Ubuntu, but you need to configure the dhcp client for eth0 to ignore the default route it gets from it's lease.

---

### Post by dtoronto on 2010-08-28
aah that makes sense.  If I only knew more about the iptables, I know ubuntu uses it's own interface to change iptables, but I guess I'll keep messing around with it some more.

---

### Post by BkkBonanza on 2010-08-28
See,
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

Your interface settings may be incorrect and this page should help get them right. You don't need to disable any default route. You may want to adjust the dhcp server to offer different routes though.

You will need to configure NAT functions in iptables for the outside network to get in. This is an example of mine,

```
WANIF=eth0
LANIF=eth1
WANIP="`/sbin/ifconfig $WANIF | grep 'inet addr' | awk '{print $LANIF}' | sed -e 's/.*://'`"

echo "1" > /proc/sys/net/ipv4/ip_forward

iptables -t nat -A POSTROUTING -o $WANIF -j MASQUERADE
iptables -t nat -A POSTROUTING -o $WANIF -j SNAT --to $WANIP
iptables -A FORWARD -i $WANIF -o $LANIF -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i $LANIF -o $WANIF -j ACCEPT
```

I put this in a file called /etc/init.d/routing
And then I link that in as a startup script.

ln -s /etc/init.d/routing /etc/rc2.d/S17routing

so it starts on boot. Be sure to use the correct runlevel though. Mine is 2 but typically it's 3 on servers.

And to test it before booting just run **sudo /etc/init.d/routing**

---

### Post by dtoronto on 2010-08-28
any additional insight into iptables for ubuntu would be incredibly helpful.

---

### Post by dtoronto on 2010-08-28
> **BkkBonaza said:**
> See,
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

Your interface settings are incorrect and this page should help get them right. You don't need to disable any default route.

Sorry about that, I just threw some dummy info into the post so as to avoid putting my own IP's up.  I went ahead and changed the post to more accurately reflect the type of network that I have.

---

### Post by dtoronto on 2010-08-28
also I don't know if this helps, but the router that I am using to assign the DHCP addresses on the internal side is a wrt-320 running dd-wrt with a static lease on the servers.

---

### Post by BkkBonanza on 2010-08-28
See my updated post above. I added iptables rules you need upon boot to allow the outside IF to get to network. You can adapt that with more rules if desired.

---

### Post by dtoronto on 2010-08-28
> See my updated post above. I added iptables rules you need upon boot to allow the outside If to get to network. You can adapt that with more rules if desired.
Last edited by BkkBonaza; 1 Minute Ago at 09:47 PM.. 

Do you know if I'm running UFW is it going to interfere with any changes i make to the IPtables?

---

### Post by BkkBonanza on 2010-08-28
It most likely won't since these rules are to the nat table (not the default table). I can't be sure though as I don't use ufw on my router. You may find that the rules need to be init'd after ufw does it's thing, so the startup script link may be slightly different.

It's possible ufw may flush everything when you update a setting and then you would need to re-add the rules. But it *ought* to play nice and only flush/manage the default table.

There may even be a way to put these rules into ufw. I don't use it so I'm just not sure.

---

### Post by dtoronto on 2010-08-29
OK, I tried running the script above to see if I could get anything to work.  I disabled UFW just to make sure and here is the output of my IPtables:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

The crazy thing is that I can't get ICMP or anything to work on that external interface.  When I take down the DHCP it pulls up the static IP very nice, but when I put that inside interface on DHCP it shuts down everything on the Static WAN side.  Am I missing something key here, because it almost seems that my box doesn't even register with the ISP to use the static IP on the WAN interface.  My IPtables don't seem to shed any light either, because it looks like there isn't anything blocked.  Just for fun I also tried both interfaces on a DHCP setup and I can get both to pull down fine with DHCP or Satic, but it seems like something isn't right about a DHCP and Static combo.

---

### Post by BkkBonanza on 2010-08-29
You would have to use **sudo iptables -t nat -L** to view the nat table. By default it only lists the default table.

In my case the WAN is DHCP (getting assigned by my ISP), and my LAN IF is static as I run dnsmasq on my router to give out IPs to my LAN. But it appears this machine is not the primary DHCP server on your LAN so you will have to work out how you want routing to be handled. Right now outgoing traffic is going to go to the gateway set by your DHCP server so trying to get out via the new WAN IF isn't going to fly. 

You can't really have both WAN routes be active unless you set up some form of load balancing. That can be done with some routing tables. But I'm not sure if that's what you want. Do you want outgoing traffic balanced over both WAN? Or do you just want to get traffic in from this new WAN to the network?

What you have now should allow traffic in but outgoing traffic will still go to your other gateway. And for now since the nat only accepts "related/established" traffic (inbound) it won't allow new connections coming in. You would have to alter the rules to enable an incoming port ("port forwarding") so specific traffic can come in and get routed to some IP.

Long story, short - the rules I gave you still leave the WANIF closed unless you open some ports.

---

### Post by dtoronto on 2010-08-29
basically what I'm trying to do is set up a few services (ie: web service, jabber) to be available over the WAN, static IP.  I can only get my ISP to give me static IP's.  For the internal LAN setup I would like to have the flexibility to open more ports (ie: ssh, ftp, etc.)  I currently cannot get response for web service or jabber on my WAN IP (static), but everything seems to work on the LAN side.  I'm going to eventually lock down everything from the WAN side with external hardware, but I can't get it to take the static IP with the whole interface on the outside.  I don't really care what side WAN/LAN the server forces bandwidth through, although ideally I would prefer to have all my bandwidth go out the WAN side while still allowing me ssh and ftp access on the LAN side. Hope this makes sense.

---

### Post by dtoronto on 2010-08-29
also it doesn't look like my IPtables are currently blocking anything at all

here is the output from:
```
sudo iptables -t nat -L
```


```
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
MASQUERADE  all  --  anywhere             anywhere
SNAT       all  --  anywhere             anywhere            to:*.*.*.*

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

---

### Post by BkkBonanza on 2010-08-29
Right now, your iptables rules for forwarding inbound is,

iptables -A FORWARD -i $WANIF -o $LANIF -m state --state ESTABLISHED,RELATED -j ACCEPT

This allows only traffic that is related to an already outbound conenction. So even though you don't block traffic inbound - it still isn't forwarded into the LAN. An example rule for forwarding inbound connections would be,

iptables -A FORWARD -i $WANIF -o $LANIF -p tcp -dport 22 -j ACCEPT
(you also may want to set dest ip as well)

---------
You don't have to forward traffic to your LAN if your ssh/web services are on this same machine and bound to the WAN IP. ie. in the web/ssh config you tell it to listen on WAN IP (not LAN IP which is typical).

If you don't need/want inbound connections to get to your other computers then the easiest approach would be to remove the forwarding and rules and just make sure web/ssh services are bound to the WAN IP. 

If you need access to ssh/web from LAN as well then you can config ssh/web to listen on both IPs, WAN IP and LAN IP.

------
Aside: In trying to ping to check conectivity you may find it useful to specify which interface to ping on. eg. ping -I eth1 x.x.x.x could be used to bypass routing rules and send it out on that interface.

---

### Post by dtoronto on 2010-08-30
I've tried everything suggested with no luck still.  I wonder if something in the dhcp3 is forcing a route that overrides anything in my interfaces.  Am I the only person to have this issue, I have 3 servers all with the exact same issue, 2 NICS one for DHCP and one for a Static Ip on separate networks.  When I enable the DHCP it blocks all incoming service on my static IP.  It looks like the outgoing service is unreliable too, but I assume it's because there are multiple gateways.  Any further help on this would be greatly appreciated.  Cheers!

---

### Post by dtoronto on 2010-08-30
Ok now I'm pretty sure dhclient3 is messing with me I found a config file for my static interface (eth1) in my var/lib/dhcp3/dhclient.eth1.leases.  So I ran 

```
sudo dhclient
```

from the command line just for giggles and it pulled a DHCP IP from the DHCP server on eth1.

---

### Post by BkkBonanza on 2010-08-30
I don't know why it would do that. Are you running something like network-manager as well? That would definately interfere with manual settings. What about a clean slate by restarting networking, **sudo service networking restart**, and then check output from **route** and **ifconfig** command to see how things end up.

dhclient shouldn't be aquiring an address for eth1 if it's marked as static in the interfaces file.

---

