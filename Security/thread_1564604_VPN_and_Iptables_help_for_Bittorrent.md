---
title: "VPN and Iptables help for Bittorrent"
date: 2010-08-30
forum: Security
---

### Post by ssc351 on 2010-08-30
Hey guys,

Im using a vpn service (like Ipredator or BTguard) for bittorrents and I can't get the iptables to work with the VPN. It uses a pptp.  I've looked all over google and this site and I can't get the thing to work.  I have no idea when it comes to programming the stuff, I just cut and paste until something works.  Anyway, if I turn off iptables I connect to the VPN no problem and bittorrents upload/download no problem.  But with Iptables up and connected to the VPN, I cant get any internet traffic.  

I really don't want to turn off my firewall anytime i need to download some torrents.  Please Help. Thanks!

Here is my script, mainly taken from the beginners tutorial that frodon? made:

#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 
modprobe ip_conntrack_irc
modprobe ip_conntrack_ftp

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

#Allow SSH
iptables -A TRUSTED -i eth1 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
iptables -A TRUSTED -i eth1 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 8 --rttl --name SSH -j DROP


#Allow printing from Virtualbox
iptables -A TRUSTED -i eth1 -p tcp -m tcp --dport 631 -j ACCEPT

#Allow printing from Virtualbox
iptables -A TRUSTED -i eth1 -p tcp -m tcp --dport 9100 -j ACCEPT

# Allow vuze
iptables -A TRUSTED -i eth1 -p tcp -m tcp --dport 27555 -j ACCEPT


# End message
echo " [End iptables rules setting]"

---

### Post by ssc351 on 2010-09-01
bump

---

### Post by spynappels on 2010-09-02
I'm not terribly familiar with the PPTP VPN protocol, but does it create a pseudo network interface? If so, you may need to reference that pseudo interface in your IPTables script. 

I only have experience with OpenVPN which is a tunnelled VPN and that's how it works.

---

### Post by ssc351 on 2010-09-03
ya it does ppp0 i believe...i tried messing around with it but I couldn't get it to work...im assuming i have to route it through eth0 or1 then thru ppp0 and back the other way...but I have no idea how to do that.

I can't believe Im the only one that has this issue...anyone? anyone?

---

### Post by ssc351 on 2010-09-08
bump again for some help...

---

### Post by BkkBonanza on 2010-09-09
Please post output from **iptables -L** and **route** commands when it is in a working state.
(Not with your firewall but with the VPN functioning correctly).

This gives us a base point for what works.
Your firewall obviously breaks the routing/forwarding between interfaces so we need to include that config in the firewall.

---

### Post by ssc351 on 2010-09-09
> **BkkBonaza said:**
> Please post output from **iptables -L** and **route** commands when it is in a working state.
(Not with your firewall but with the VPN functioning correctly).

This gives us a base point for what works.
Your firewall obviously breaks the routing/forwarding between interfaces so we need to include that config in the firewall.


Not exactly sure what you mean by the first command...I have to pull the iptables down to get the vpn to connect...

here is iptables -L w/IPtables stopped:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

Here is iptables -L after connected to vpn then starting iptables back up...note cannot connect to the internet with iptables up:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
FIREWALL   all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FIREWALL (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
TRUSTED    all  --  anywhere             anywhere            
DROP       all  --  anywhere             anywhere            

Chain TRUSTED (1 references)
target     prot opt source               destination         
           tcp  --  anywhere             anywhere            tcp dpt:ssh state NEW recent: SET name: SSH side: source 
DROP       tcp  --  anywhere             anywhere            tcp dpt:ssh state NEW recent: UPDATE seconds: 60 hit_count: 8 TTL-Match name: SSH side: source 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ipp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:9100 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:29992

route: (w/iptables down)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
net0.sth.se.vpn *               255.255.255.255 UH    0      0        0 ppp0
four.sth.se.vpn 192.168.168.168 255.255.255.255 UGH   0      0        0 eth1
192.168.168.0   *               255.255.255.0   U     2      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         *               0.0.0.0         U     0      0        0 ppp0

route: (w/iptables up)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
188.126.80.0    *               255.255.255.255 UH    0      0        0 ppp0
80.67.2.69      192.168.168.168 255.255.255.255 UGH   0      0        0 eth1
192.168.168.0   *               255.255.255.0   U     2      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         *               0.0.0.0         U     0      0        0 ppp0

---

### Post by BkkBonanza on 2010-09-09
Your iptables rules are all written with eth0, but your default route is ppp0.
No wonder nothing gets anywhere.
The default route says send anything we don't know about to ppp0.
Your rules say accept these special case on eth0 but drop anything else.
So it drops everything on ppp0.
Change your rules so that the cases you accept are on ppp0.

Also this machine acts as gateway to ppp0 as far as I can make out.
So if you want anything from the LAN to pass thru it, to ppp0, then you can't set FORWARD to DROP. It has to ACCEPT, and if you want NAT, which likely you do then you will need a rule in PREROUTING too.

Do you want the LAN to pass thru the VPN -> ppp0? 
Or is it just for this single machine to use? 

I'm not sure why there is two VPN IPs in the routing table though?
Is there two VPNs active?

---

### Post by ssc351 on 2010-09-09
> **BkkBonaza said:**
> Your iptables rules are all written with eth0, but your default route is ppp0.
No wonder nothing gets anywhere.
The default route says send anything we don't know about to ppp0.
Your rules say accept these special case on eth0 but drop anything else.
So it drops everything on ppp0.
Change your rules so that the cases you accept are on ppp0.

Also this machine acts as gateway to ppp0 as far as I can make out.
So if you want anything from the LAN to pass thru it, to ppp0, then you can't set FORWARD to DROP. It has to ACCEPT, and if you want NAT, which likely you do then you will need a rule in PREROUTING too.

Do you want the LAN to pass thru the VPN -> ppp0? 
Or is it just for this single machine to use? 

I'm not sure why there is two VPN IPs in the routing table though?
Is there two VPNs active?

Sorry, I forgot to update the interface on the 1st post...thats at least correct now :)

This is only for a single machine...not sure why 2 vpn ip's popped up either.

I tried something like this, but couldnt get it to work:
iptables -N pptp
iptables -A pptp -p tcp --dport 1723 --dst $vpnserver -j ACCEPT
iptables -A pptp -p 47 --dst $vpnserver -j ACCEPT
iptables -I FORWARD -j pptp
iptables -t nat -N pptp
iptables -t nat -A pptp -i ppp0 -p tcp --dport 1723 -j DNAT --to $vpnserver:1723
iptables -t nat -A pptp -i ppp0 -p 47 -j DNAT --to $vpnserver
iptables -t nat -A PREROUTING -j pptp

Not sure if I have the vpnserver ip wrong or the script wrong or what...like I said, I don't really know what Im doing.

---

### Post by BkkBonanza on 2010-09-09
> iptables -N pptp
iptables -A pptp -p tcp --dport 1723 --dst $vpnserver -j ACCEPT
iptables -A pptp -p 47 --dst $vpnserver -j ACCEPT
iptables -I FORWARD -j pptp
iptables -t nat -N pptp
iptables -t nat -A pptp -i ppp0 -p tcp --dport 1723 -j DNAT --to $vpnserver:1723
iptables -t nat -A pptp -i ppp0 -p 47 -j DNAT --to $vpnserver
iptables -t nat -A PREROUTING -j pptp

Well, that definitely won't work. I don't know if you left parts out or that's all of it but what is there has errors. 

I would stop using custom chains and just keep it simple. For a few rules like this the extra chains just get confusing and take away from a simple flow.

HOW TO BUILD A FIREWALL, STEP BY STEP...

I've done a [quick sketch]("http://img1.optimalseller.com/tx/iptables-flowchart.jpg") here hoping this would make the flow of packets more clear. You can print it out to remind you how the packets flow thru iptables.

Understanding the flow is the only way to get what you want here.

Add a rule to INPUT if the data is coming into your programs.
-A INPUT ...

Add a rule to OUTPUT if the data is going out from your programs.
-A OUTPUT ...

Add a rule to FORWARD to control data going thru your machine.
-A FORWARD ...

Add a rule to PREROUTING - to translate DEST IP on incoming packets
(When data coming in needs to forward to a fixed server)
(On the way in so that other filtering is based on where it will go)

-t nat -A PREROUTING -i $WANIF -p tcp --dport xxxx -j DNAT --to x.x.x.x:xxx

Add a rule to POSTROUTING - to translate SRC IP on outgoing packets
(When data going out needs to hide it's IP on the internet)
(On the way out because other change are done and it's the last stop)

-t nat -A POSTROUTING -o $WANIF -j SNAT --to $WANIP

-------- SYNTAX MUST BE CORRECT --------
Matching tcp packets going to some port,
-p tcp --dport xxxx 

Matching udp packets going to some port,
-p udp --dport xxxx 

Matching a source port, --sport xxxx
Matching a source ip, -s x.x.x.x
Matching a source network, -s x.x.x.x/x

Matching a state meaning "replies to our outgoing traffic",
-m state --state ESTABLISHED,RELATED

Once a match occurs, set the target,
-j ACCEPT 
-j DROP (no reply to sender)
-j REJECT (reply with error to sender)

If you need to forward packets thru the machine (ie. use the forward chain) then you also need this kernel setting,

echo 1 > /proc/sys/net/ipv4/ip_forward

Build the firewall rule by rule and test in pieces.
Use a debug script like this, eg. test-fw  (chmod 700 test-fw)
```
#!/bin/bash

iptables-save >fw.bak

...my test rules here...

sleep 30
iptables-restore <fw.bak
```

Run like this,

sudo test-fw &

will set rules and give you 30 seconds to test before reverting back to what it was. Have the script in another window so you can edit and test, back and forth. When it finally works, remove the save/sleep/restore statements and copy to /etc/network/if-up.d/firewall

---

### Post by ssc351 on 2010-09-11
Will give this a try...thanks.

EDIT:  Started working on this...1st question (of probably many):

Do I need to specify how the computer routes the traffic through either or both of eth1 and ppp0?  On your cool little sketch you have eth0(1) and ppp0 going thru the NAT...so do I set-it up for both interfaces?  Or do I need to specify when it is connected via eth1, do this...and when connected via ppp0, do this...(of course, I guess it always is connected via eth1 so only when it is/is not connected via ppp0?)

This question is confusing myself :)

Basically, what Im asking is if Im at home just connected to my router via eth1 without the VPN do I need to tell iptables to do something different if im connected to the VPN say at the airport and its routed thru ppp0?  Or does it matter since both eth1 and ppp0 are being routed together and inputing/outputing thru the postroute?

---

### Post by ssc351 on 2010-09-11
On to the next question...I contacted the VPN company and they use multiple ip addresses for their servers..in other words, I could connect anyone of these for any given time I try to connect:

**.**.1.64
**.**.1.65
**.**.1.66
**.**.1.67
**.**.1.etc 

up to 30 different in a row

I tried doing something along the lines of:
iptables -A INPUT -p tcp --sport 1723 -s **.**.1.64/30

But it seems like iptables doesn't like that...do I have to write redundant rules for every IP address that I may connect to?

---

### Post by BkkBonanza on 2010-09-11
For your VPN traffic you should probably write rules in iptables that reference by interface rather than IP address. It will be easier and just as good unless you want to filter specific IPs on the VPN. Probably not.

So instead of using,

-s x.x.x.x/x format of matching, you would use,

-i ppp0  (which says match if input from interface ppp0), or
-o ppp0  (match if output on ppp0)

My diagram was intending to show that both eth1 and ppp0 traffic is handled by iptables in the same way. You decide what you want to do with the packets depending on the matching rules.
----------
You won't need it now but just for future knowledge, the way you wrote,

-s **.**.1.64/30  wasn't accepted by iptables because it is not correct. It requires an address in  proper [CIDR]("http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing") notation. You can't use stars there, 30 doesn't mean "how many IPs". 

So for example let's say your VPN network addresses are, 

80.67.1.1 - 80.67.1.255  

The first three quads are the same, which represents 24 bits of addresses that remain the same in all the network. So we write,

80.67.1.0/24  but for a smaller range, let's say 

80.67.1.64 - 80.67.1.95

you have a more limited range of 32 addresses. In binary 32 = 2*2*2*2*2 = 2^5 or 5 bits of address range, which means out of 32 bits (total) only 32-5 = 27 stay the same for this network. Hence,

80.67.1.64/27 

would be correct. The first 27 bits define the network, the last 5 bits are unique IPs possible in the network. In CIDR notation networks are always a size in multiples of 2. 1,2,4,8,16,32,64,128,256 and not irregular.

Usually with gateways you don't worry about the IP range thru it but just match to the interface ppp0, or eth1.

Match -i ppp0 for inbound traffic from the VPN, and -i eth1 for LAN traffic, or
-o ppp0 for outbound to the VPN, -o eth1 outbound to the LAN.

---

### Post by BkkBonanza on 2010-09-11
You'll want to write rules that make sense whether each network is connected or not. So maybe, in English,

All traffic out to ppp0 is allowed.

-A OUTPUT -o ppp0 -j ACCEPT

All traffic out to my LAN is allowed,

-A OUTPUT -o eth1 -j ACCEPT

All traffic from my LAN is allowed if I connected to it first,

-A INPUT -i eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT

but also please let my router do DHCP with me too,

-A INPUT -i eth1 -p udp --dport 68 -j ACCEPT

etc etc. Until you've covered the traffic you want to allow.

Allow Joe (192.168.1.45) from my LAN to get pop3 mail (25) via the VPN,

-A FORWARD -i eth1 -s 192.168.1.45 --dport 25 -o ppp0 -j ACCEPT

but otherwise nobody on the LAN can use my VPN gateway,

-A FORWARD -i eth1 -o ppp0 -j REJECT

and the VPN guys can't see my other machines either (unless replies to Joe's mail),

-A FORWARD -i ppp0 -o eth1 -m state --state ESTABLISHED, RELATED -j ACCEPT

etc etc.

So if you write out an English version of what you want to happen then it shouldn't be too hard to convert it to iptableese.

---

### Post by ssc351 on 2010-09-11
> **BkkBonaza said:**
> 
So if you write out an English version of what you want to happen then it shouldn't be too hard to convert it to iptableese.

Ha! Easy for you to say...just kidding...at least im learning something.  Will give your tips a try and see if I can move on and get this thing working. Thanks again for the help.

---

### Post by ssc351 on 2010-09-11
oh man, im getting in over my head quick...next questions, do I need to write complete separate rules for both interfaces or can I do a iptables -i ppp0 -i eth1 

IE
# hide computers behind the firewall one for vpn and eth1
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE 

or just do
iptables -t nat -A POSTROUTING -o eth1 -o ppp0 -j MASQUERADE 

Next,

Similar question, Do I need to forward the ports twice also for bittorrents?
# Allow vuze
iptables -A TRUSTED -i eth1 -p tcp -m tcp --dport 29992 -j ACCEPT
# Allow vuze
iptables -A TRUSTED -i ppp0 -p tcp -m tcp --dport 29992 -j ACCEPT

It seems like I could just forward all internet traffic coming from ppp0 to eth1 so I don't have to write redundant rules...maybe I just answered my own question :0
EDIT: in other words, since eth1 is doing all the "firewall work" I don't need to write rules for the ppp0 interface.  Sorry, this is get a bit confusing.

---

### Post by BkkBonanza on 2010-09-11
First question,
you have to write separate rules. You can not match both interfaces in one rule because a packet only enters thru one interface. But you can write a rule with no interface, meaning ANY interface, which works as long as you don't have other interfaces like a wifi one.

Second,
when using -p tcp (protocol is tcp) you don't need to use -m tcp since -p tcp already indicates use the tcp module. (-m is module).

If you wish to accept bittorrent for both networks then you need both rules, or leave the interface out if ALL networks is ok, (only have two here right?)

iptables -A TRUSTED -p tcp --dport 29992 -j ACCEPT

Third,
forwarding ppp0 to eth1 bypasses the computer with iptables (this computer). See diagram, a rule in FORWARD is for traffic thru the computer no into/out of the computer.

Remember these are different paths, rules in FORWARD do not affect packets **into** the programs on your computer, only traffic passing **between** the two networks. It may seem counter intuitive but refer to the diagram for pathways.

---

### Post by ssc351 on 2010-09-12
Alright Im a bit stuck,(lets be honest, i have no idea what Im doing), I've gotten the firewall to connect and do what it supposed to do (I think) without connecting to the VPN.  However, Ive tried all sorts of variations and I can't get the VPN to connect (note connects fine with firewall off)...one things i keep getting stuck on is the vpn server ip...

IE
iptables -t nat -A PREROUTING -i ppp0 -p 47 -j DNAT --to 80.67.2.64-80.67.2.95

Is there a way to clean this up?  And if this is incorrect, how do I get the ppp0 interface to connect to the vpn server ip(s)?

Also, Im still a bit confused on the flow...
is eth1 or ppp0 connecting to the vpn server (or both?)? Im assuming ppp0 connects to the vpn server then that traffic needs to be forwarded to the eth1 interface via postrouting...right?

still not quite sure how source and destination work...do they need to match up for every port and interface?  

Here is somewhat of a run down of what I tried or at least what I understand for pptp vpn:
#Port Forward Protocal 47
iptables -t nat -A PREROUTING -i ppp0 -p 47 -j DNAT --to 80.67.2.64-80.67.2.95
iptables -A FORWARD -i ppp0 -p 47 -s 80.67.2.64-80.67.2.95 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i ppp0 -p 47 -d 80.67.2.64-80.67.2.95 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
#Port forward 1723 to local machine
iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 1723 -j DNAT --to 80.67.2.64-80.67.2.95
iptables -A FORWARD -i ppp0 -p tcp --sport 1723 --dport 1024: -s 80.67.2.64-80.67.2.95 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i ppp0 -p tcp --dport 1723 -d 80.67.2.64-80.67.2.95 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
#PostRouting
iptables -t nat -A POSTROUTING -o ppp0 -p tcp --sport 1723 -s 80.67.2.64-80.67.2.95 -d ! -i eth1 -j SNAT --to 80.67.2.64-80.67.2.95

Other stuff Ive tried in various combinations with the above:
#Allow incoming VPN connections
iptables -A INPUT -i ppp0 -p 47 -m state --state ESTABLISHED -j ACCEPT
iptables -A INPUT -i ppp0 -p tcp --sport 1723 -m state --state ESTABLISHED -j ACCEPT
#Allow outgoing VPN connections
iptables -I OUTPUT -o ppp0 -p 47 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -I OUTPUT -o ppp0 -p tcp --dport 1723 -m state --state NEW,ESTABLISHED -j ACCEPT

---

### Post by BkkBonanza on 2010-09-12
> **ssc351 said:**
> I've gotten the firewall to connect and do what it supposed to do (I think) without connecting to the VPN.  However, Ive tried all sorts of variations and I can't get the VPN to connect (note connects fine with firewall off)...one things i keep getting stuck on is the vpn server ip...
I need to clarify terminology here. Programs (clients/servers) "connect" to each other, their packets flow thru various routing, thru interfaces, and thru iptables. But iptables doesn't "connect", nor do the interfaces "connect". Except in the sense that the wires run from one to another.

Since you have ppp0 and eth1 working fine without the firewall, we'll assume that traffic can get where it needs to when not "blocked" by iptables. If this isn't a valid assumption then first you need to set up routing before working in iptables. From what you've said so far, I think you are fine as far as basic routing of traffic. We're now using iptables to put restricts in. What I'm trying to say is that iptables doesn't connect things it just restricts or allows traffic.

> **ssc351 said:**
> 
IE
iptables -t nat -A PREROUTING -i ppp0 -p 47 -j DNAT --to 80.67.2.64-80.67.2.95
This is a NAT rule. It rewrites a destination address based on a rule. If things are fine before iptables is in place then you don't need it after. So far I haven't seen a reason you want to "port forward". Do you have a server on the VPN you want to be listening locally on the LAN, so that users locally can connect to the server? That is what this rule would be for.
> **ssc351 said:**
> 
Is there a way to clean this up?  And if this is incorrect, how do I get the ppp0 interface to connect to the vpn server ip(s)?
Again, ppp0 is already your route to the VPN, just don't block stuff, and it will get there, as seen when no iptables rules.
> **ssc351 said:**
> 
Also, Im still a bit confused on the flow...
is eth1 or ppp0 connecting to the vpn server (or both?)? Im assuming ppp0 connects to the vpn server then that traffic needs to be forwarded to the eth1 interface via postrouting...right?
```

LAN -> eth1 -> [INPUT] -> [apps on machine] -> [OUTPUT] -> eth1 -> LAN
                [^ v FORWARD]                 [^ v FORWARD]
VPN -> ppp0 -> [INPUT] -> [apps on machine] -> [OUTPUT] -> ppp0 -> VPN

```
Notice how this is like a cross-over between the two networks.
> **ssc351 said:**
> 
still not quite sure how source and destination work...do they need to match up for every port and interface?  
I wish I could make this clear, but I think you have some basic networking terms to learn. Each packet of data has values inside that indicate SRC (where it came from), DEST (where it's going). Your rules are intended to match against the packet and decide what to do - DROP, ACCEPT, ALTER (NAT/REDIRECT). If things are working fine without the firewall then you will not need to ALTER any packets. They are already going to where they need to. You just want to add enough rules so they continue but other stuff doesn't also get thru. 

With DROP policy you are starting from a position of nothing passing and adding rules until just the traffic you want passes.

> **ssc351 said:**
> 
Here is somewhat of a run down of what I tried or at least what I understand for pptp vpn:
#Port Forward Protocal 47
iptables -t nat -A PREROUTING -i ppp0 -p 47 -j DNAT --to 80.67.2.64-80.67.2.95
Bad syntax: -p means protocol not port, you mean --dport.
You cannot forward a port to a network. You can only forward a port to a specific server. You don't want this rule at all. 
> **ssc351 said:**
> 
iptables -A FORWARD -i ppp0 -p 47 -s 80.67.2.64-80.67.2.95 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
Again -p means protocol not port.
This is allowing ALL traffic, except for INVALID states, to that network. You can write this more concisely as 80.67.2.64/27
> **ssc351 said:**
> 
iptables -A FORWARD -i ppp0 -p 47 -d 80.67.2.64-80.67.2.95 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
You shouldn't be getting traffic destined for this network into ppp0. I think you mean -o ppp0 (going out thru ppp0). Again fix -p to --dport.
> **ssc351 said:**
> 
#Port forward 1723 to local machine
iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 1723 -j DNAT --to 80.67.2.64-80.67.2.95

Same as above, you don't want to port forward and do DNAT. You would want this if some traffic isn't getting to it's destination even when the firewall was down. eg. If you had a server that couldn't be reached from the internet when you want it to be.
> **ssc351 said:**
> 
iptables -A FORWARD -i ppp0 -p tcp --sport 1723 --dport 1024: -s 80.67.2.64-80.67.2.95 -m state --state ESTABLISHED,RELATED -j ACCEPT

Syntax error: the colon after 1024. This rules says allow packets going to port 1024 on any machine in our LAN when it's from these src IPs in the VPN, but only if we already have a connection the machine to that IP.

I think you are still confused about what FORWARD means. It doesn't mean "send data from this machine to dest", it means "allow data to pass thru without touching down in this machine".
> **ssc351 said:**
> 
iptables -A FORWARD -i ppp0 -p tcp --dport 1723 -d 80.67.2.64-80.67.2.95 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
Same issues as mentioned above.
> **ssc351 said:**
> 
#PostRouting
iptables -t nat -A POSTROUTING -o ppp0 -p tcp --sport 1723 -s 80.67.2.64-80.67.2.95 -d ! -i eth1 -j SNAT --to 80.67.2.64-80.67.2.95

I'm baffled by what you wanted here. You're saying "not interface eth1", why not just say -i ppp0 (you only have two interfaces). This rules makes absolutely no sense. You're saying translate addresses for any traffic coming from the VPN and going to the VPN. Such traffic won't even be coming to your machine as the router in the VPN will be sending it directly to where it should go, not to this machine.
> **ssc351 said:**
> 
Other stuff Ive tried in various combinations with the above:
#Allow incoming VPN connections
iptables -A INPUT -i ppp0 -p 47 -m state --state ESTABLISHED -j ACCEPT
iptables -A INPUT -i ppp0 -p tcp --sport 1723 -m state --state ESTABLISHED -j ACCEPT

Again -p is protocol. These don't allow incoming connections, they allow ESTABLISHED traffic only. That specifically means not NEW connections.
> **ssc351 said:**
> 
#Allow outgoing VPN connections
iptables -I OUTPUT -o ppp0 -p 47 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -I OUTPUT -o ppp0 -p tcp --dport 1723 -m state --state NEW,ESTABLISHED -j ACCEPT
Is there a reason you chose not to allow RELATED here? You may not need it but I wonder if you know why? Other than -p 47, these seem reasonable for allowing traffic to ports 47 and 1723 anywhere in the VPN network.

---

### Post by BkkBonanza on 2010-09-12
I'm sure this is frustrating for you. But it's clear you're still wanting to plug in rules without being clear what they do.

I'd suggest posting me a list in English, as I did a couple posts up, describing what you need to happen here. I can reply with the correct rules to match. Just think of it terms of "I want to allow data from here to here". Be specific so I don't have to guess what you mean.

I want data from the VPN to my Torrent client on port 1723.
I want data from my Torrent client, any port out to VPN.
I want data from the VPN to my mail server on my LAN at 192.168.2.21 port 25.
I want to allow DNS lookups via the VPN.
I want to browse any web sites on the VPN.
etc. 

Do you access the internet via the VPN? 
Or do you want to restrict internet access via the VPN to only some programs?

I would have posted rules for you some time back except I don't know exactly what you want and rules have to be precise and correct or you end up with the wrong results.

---

### Post by ssc351 on 2010-09-12
Ok your explanations of some of the terminology is making more sense. The little diagram I understand a bit better 

One thing I need to clear up...from what I've read on google VPN via PPTP needs to use Protocol 47 (GRE) and then forward Port 1723. I guess this is a Microsoft thing since microsoft came up with the PPTP? Not sure.  Anyway, I think I have the Protocol vs Port part correct (again based on what others say)

 
"I wish I could make this clear, but I think you have some basic networking terms to learn. Each packet of data has values inside that indicate SRC (where it came from), DEST (where it's going). Your rules are intended to match against the packet and decide what to do - DROP, ACCEPT, ALTER (NAT/REDIRECT). If things are working fine without the firewall then you will not need to ALTER any packets. They are already going to where they need to. You just want to add enough rules so they continue but other stuff doesn't also get thru."

So Here is my next try that didn't work, I cleaned it up a bit (I hope)...and then "#" out the pre and post routing rules since I dont need to alter the traffic because I connect fine with the firewall down...im a bit confused on this, isn't the traffic coming in and out from the vpn encrypted so it has to be altered for the eth1?  Or is it taken care of in the pptp protocal in network manager? 
Do I need to open port 1723 on eth1 and open protocal 47 on eth1 as well.

#Allow incoming VPN connections and PreRouting(not needed since I can connect without firewall down?) for Protocal 47 and Port 1723
#iptables -t nat -A PREROUTING -i ppp0 -p 47 -j DNAT --to 80.67.2.64/27
iptables -A INPUT -i ppp0 -p 47 -m state --state NEW,ESTABLISHED -j ACCEPT
#iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 1723 -j DNAT --to 80.67.2.64/27
iptables -A INPUT -i ppp0 -p tcp --sport 1723 -m state --state NEW,ESTABLISHED -j ACCEPT
#Allow outgoing VPN connections and PostRouting (not needed since I can connect without firewall down?) for Protocal 47 and Port 1723
iptables -I OUTPUT -o ppp0 -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -I OUTPUT -o ppp0 -p tcp --dport 1723 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
#iptables -t nat -A POSTROUTING -o ppp0 -j SNAT --to 80.67.2.64/27

#Allow traffic back and forth between eth1 and ppp0 networks
iptables -A FORWARD -o ppp0 -p tcp --dport 1723 -d 80.67.2.64/24 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i ppp0 -p 47 -s 80.67.2.64/24 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i eth1 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

Im not really sure what I want to do in english so its hard for me to write it out, but something like this..just starting with the basics of getting to the internet with the VPN.

1.- I want to be able to connect to the VPN with the firewall up
2.- I want to be able to get all incoming internet traffic "normally" like I would as if I was not connected to the VPN
3.- I want to be able to send all traffic out "normally" as if not connected to the VPN

Thats about as basic as I can get...once I start adding specifics I get lost :)

---

### Post by BkkBonanza on 2010-09-13
Oh, my apologies. I had never heard of or used "protocol 47". A bit of googling and it appears to be right for pptp and some Microsoft thing.

Presumably your VPN has to go through whatever VPN service is running on your system before traffic will be unencrypted for local use. So I don't think you would want to just forward data across your system. I would expect that when it enters port 1723 to your VPN software, that it decrypts and chooses where to send it on to. If that is correct then no forwarding need be done - data enters the VPN service (INPUT) and gets relayed on (OUTPUT) to any LAN users. So any rules would only have to affect those chains.

My idea with the English was to get you to narrow down and understand what you need because iptables rules have to be specific and if you don't know yet what you need specificly then you can't possibly write the rules. While I've done a fair bit of work generally with iptables I don't know the VPN software and what it needs. It's starting to sound like all it needs is port 1723 open but really this info should be available in detail in the VPN software support docs.

---

