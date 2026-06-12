---
title: "proxy server port forwarding question"
date: 2010-05-13
forum: Server Platforms
---

### Post by Nessaja on 2010-05-13
Hi all, I'm new to linux, but enjoy using it very much, especially without a GUI, console is fun!

I need some help setting up port forwarding.
We have 3 servers, 1x running  Ubuntu server 8.04 (used as transparent proxy), 1x server 2003, 1x windows  xp.

The linux box has the following ips:
eth0 (internal)  192.168.1.5
eth1 (external) 192.168.0.7

Windows server  2003:
192.168.1.6

Windows  XP:
192.168.1.9

Router:
192.168.0.1

The router automatically  forwards spesific ports to 196.168.0.7 (Linux eth0)
From there I want to  forward port 8585 to 192.168.1.6 and 3000 to 192.168.1.9
is there a way that  I can do this using iptables?
The commands that I think I'm gonna use look  like this:
iptables -A FORWARD -s 192.168.0.0/24 -p tcp --dport 8585 -d  192.168.1.6 -j ACCEPT
iptables -A FORWARD -s 192.168.0.0/24 -p tcp --dport  3000 -d 192.168.1.9 -j ACCEPT

Would this be a correct way of doing  it?
My biggest problem is that I can't test it without going live, and if I go live and something doesn't work, the entire building will be left without internet, people will hate me...

Also, The proxy captures all data on port 80 and forwards it to 3128  so that the proxy can monitor the usage, and a few systems runs fine with it,  others however can ping websites, and internet explorer says "website found,  waiting for reply" but the webpages cannot be displayed :-/
I can post the  entire routing script should it be needed..

---

### Post by benderisgreat on 2010-05-13
> iptables -A FORWARD -s 192.168.0.0/24 -p tcp --dport 8585 -d 192.168.1.6 -j ACCEPT
iptables -A FORWARD -s 192.168.0.0/24 -p tcp --dport 3000 -d 192.168.1.9 -j ACCEPTThose rules will allow traffic originating from the 192.168.0.0/24 subnet directed at port 8585 of 192.168.1.6 and port 3000 of 192.168.1.9 to be forwarded by (traverse the forwarding chain of) your ubuntu server.
They will not make traffic directed at port 8585 and 3000 of 192.168.0.7 (your server) to be redirected to your windows boxes. To do that you need to do network address translation for which you have to add rules to the 'nat' table. You need to add rules like these:
```
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 8585 -j DNAT --to-destination 192.168.1.6
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 3000 -j DNAT --to-destination 192.168.1.9
```

Normally any traffic directed at the ip of your ubuntu server would enter the INPUT chain. By adding the rules to the PREROUTING chain in the nat table you change the destination ip and the packets will enter the FORWARD chain. Then of course they will have to be accepted to traverse that chain which is what the rules you wrote will do.

N.B. If you want those ports to be reachable over the internet you should probably lose the '-s 192.168.0.0/24' part from your FORWARD accept rules.

You should have a catch all LOG rule under your rules in the FORWARD chain and i suggest you carefully look at any messages that produces in /var/log/messages or whatever log you have them directed.

I'm not quite sure what you mean by going live, but none of the iptables rules discussed will break internet connectivity for anyone behind your ubuntu server.

---

### Post by Nessaja on 2010-05-14
> **benderisgreat said:**
> 

I'm not quite sure what you mean by going live, but none of the iptables rules discussed will break internet connectivity for anyone behind your ubuntu server.

Thanks a lot for your reply!

By "going live" I mean that the windows 2003 is currently the internet gateway, the ubuntu system has internet connectivity but is not the gateway yet, to go live would be to change the gateway and dns adresses in DHCP to 192.168.1.5 instead of 192.168.1.6

The problem that I have is, if I change my pc's gateway and dns to 192.168.1.5, everything still works, but my traffic now goes through the transparent proxy, but other "random" PC's cannot connect to the internet anymore after their gateway and dns adresses are changed to 192.168.1.5, very weird.

I found a transparent proxy how-to, this is the daitls that I put in rc.local in order to get the proxy transparent:

```

echo "Settings server rules..."
echo "Setting up port forwarding"
SQUID_SERVER="192.168.1.5"
INTERNET="eth0"
LAN_IN="eth1"
SQUID_PORT="3128"
iptables -F
iptables -X
echo "Setting up NAT"
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
modprobe ip_conntrack
modprobe ip_conntrack_ftp
modprobe ip_nat_ftp
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "Setting up IPTABLES..."
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
iptables -A INPUT -i $INTERNET -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables --table nat --append POSTROUTING --out-interface $INTERNET -j MASQUERADE
iptables --append FORWARD --in-interface $LAN_IN -j ACCEPT
iptables -A INPUT -i $LAN_IN -j ACCEPT
iptables -A OUTPUT -o $LAN_IN -j ACCEPT

iptables -t nat -A PREROUTING -i $LAN_IN -p tcp --dport 80 -j DNAT --to $SQUID_SERVER:$SQUID_PORT
iptables -t nat -A PREROUTING -i $INTERNET -p tcp --dport 80 -j REDIRECT --to-port $SQUID_PORT

iptables -A INPUT -j LOG
iptables -A INPUT -j DROP

iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o ppp0 -j MASQUERADE
ACCEPT


// Thanks to benderisgreat:
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 8585 -j DNAT --to-destination 192.168.1.6
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 3000 -j DNAT --to-destination 192.168.1.9


```

---

### Post by benderisgreat on 2010-05-14
it looks like you switched up the eth0 and eth1 interfaces in your script. If you connect to the internet through the router at 192.168.0.1 and you connect to that router over your eth1 interface (192.168.0.7) then it should be ```
INTERNET="eth1"
LAN_IN="eth0"
```

> iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o ppp0 -j MASQUERADE
Are you really using a ppp tunnel for something? Perhaps you read an old manual that supposed a dial-up connection. If your router is connected via ethernet and you intend to forward all traffic (except port 80) from your lan to your router then you should replace that line with:
```
iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o $INTERNET -j SNAT --to-source 192.168.0.7
```

Where is "my pc" on the network? > .. and dns adresses are changed to 192.168.1.5 ..

The dns shouldn't necessarily point to the same ip as the gateway. Some routers have built in caching dns servers. You should only point the dns at your ubuntu server if you are actually running a dns server on it. Else you should find out what the ip of your isp's dns servers is or point it at the router or whatever device was working before.

On the subject of going live; you could at first just have all traffic be forwarded normally, that is not through the proxy. Then setup your pc/laptop with a static ip and only PREROUTE traffic from your ip only through to the proxy until you have that working.

---

### Post by benderisgreat on 2010-05-14
I read your script a little quickly.

I see you had this in there.
> iptables --table nat --append POSTROUTING --out-interface $INTERNET -j MASQUERADE
Masquerade is an SNAT rule for when you don't have a static ip, which you do.

There are some forwarding rules missing.
> iptables --append FORWARD --in-interface $LAN_IN -j ACCEPT
This will allow packets coming from your lan to go out, but the reply can't come back unless the policy on the FORWARD chain is accept. There is no policy line for the FORWARD chain in your script.
You can make use of state matching capabilities to only allow connections initiated from the lan.
```
iptables -P FORWARD DROP
iptables -A FORWARD -i $INTERNET -m state --state ESTABLISHED -j ACCEPT
iptables -A FORWARD -i $INTERNET -p icmp -m state --state RELATED -j ACCEPT
iptables -A FORWARD -i $LAN_IN -j ACCEPT
```

Also to allow the prerouted port 8585 and 3000 traffic through you do also need rules in the forwarding chain:
```
iptables -A FORWARD -i $INTERNET -p tcp --dport 8585 -d 192.168.1.6 -m state --state NEW -j ACCEPT
iptables -A FORWARD -i $INTERNET -p tcp --dport 3000 -d 192.168.1.9 -m state --state NEW -j ACCEPT
```

---

### Post by Nessaja on 2010-05-14
Thanks a lot benderisawesome!!

The tests that I did with my pc worked so far! You should get a promotion!

This is what the (working) script looks like at this moment:

```

#!/bin/sh
echo "Settings server rules..."
echo "Setting up port forwarding"
SQUID_SERVER="192.168.1.5"
INTERNET="eth0"
LAN_IN="eth1"
SQUID_PORT="3128"
iptables -F
iptables -X
echo "Setting up NAT"
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
modprobe ip_conntrack
modprobe ip_conntrack_ftp
modprobe ip_nat_ftp
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "Setting up IPTABLES..."
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
iptables -A INPUT -i $INTERNET -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables --table nat --append POSTROUTING --out-interface $INTERNET -j MASQUERADE
iptables --append FORWARD --in-interface $LAN_IN -j ACCEPT
iptables -A INPUT -i $LAN_IN -j ACCEPT
iptables -A OUTPUT -o $LAN_IN -j ACCEPT
iptables -t nat -A PREROUTING -i $LAN_IN -p tcp --dport 80 -j DNAT --to $SQUID_SERVER:$SQUID_PORT
iptables -t nat -A PREROUTING -i $INTERNET -p tcp --dport 80 -j REDIRECT --to-port $SQUID_PORT
iptables -A INPUT -j LOG
iptables -A INPUT -j DROP
echo "Benderisgreat additions:"
iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o $INTERNET -j SNAT --to-source 192.168.0.123 #change to 192.168.0.7 when live
iptables -P FORWARD DROP
iptables -A FORWARD -i $INTERNET -m state --state ESTABLISHED -j ACCEPT
iptables -A FORWARD -i $INTERNET -p icmp -m state --state RELATED -j ACCEPT
iptables -A FORWARD -i $LAN_IN -j ACCEPT
iptables -A FORWARD -i $INTERNET -p tcp --dport 8181 -d 192.168.1.6 -m state --state NEW -j ACCEPT #change back to 8585 when live
iptables -A FORWARD -i $INTERNET -p tcp --dport 3000:4000 -d 192.168.1.9 -m state --state NEW -j ACCEPT #change back to 3000 when live
echo "Special thanks to Benderisgreat from ubuntuforums.org for help setting up this script, thanks Bender!"
echo "IPTABLES configured..."
echo "Squid up and running :-)"



```

I'll keep you posted when the current gateway is replaced with squid :-)

Thanks again!

---

### Post by Nessaja on 2010-05-17
Hi, just 2 more questions,

If I removes these two lines in my script :
```

iptables -t nat -A PREROUTING -i $LAN_IN -p tcp --dport 80 -j DNAT --to $SQUID_SERVER:$SQUID_PORT
iptables -t nat -A PREROUTING -i $INTERNET -p tcp --dport 80 -j REDIRECT --to-port $SQUID_PORT

```
the internet works on all the pc's, but it's not being routed to port 3128, but if I put these lines back, all the computers on the network says: "Website foud, waiting for reply..." but nothing else happens, after a very long time it will display the Diagnose network problems page, what could cause this? It pings fine and outlook and skype works on all pc's except internet explorer... It looks like the data is correctly routed to 3128 (dansguardian) then to 3129 (squid) and then out, but all replies coming back from the internet somehow get's lost in the route :-/

$LAN_IN = "eth1" (192.168.1.5) 
$INTERNET = "eth0" (192.168.0.7) (gateway is 192.168.0.1)

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:19:5b:fe:cc:0f
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:5bff:fefe:cc0f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58866 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:47469453 (45.2 MB)  TX bytes:12290100 (11.7 MB)
          Interrupt:21 Base address:0x4000

eth1      Link encap:Ethernet  HWaddr 00:19:5b:6a:5c:52
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:5bff:fe6a:5c52/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13664333 (13.0 MB)  TX bytes:47846546 (45.6 MB)
          Interrupt:22 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12373 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12373 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3665921 (3.4 MB)  TX bytes:3665921 (3.4 MB)



```

One more thing, I must add a forwarding rule for 192.168.1.9 port 3308, but the outgoing port must be 3389, how can I achieve this?

---

### Post by Nessaja on 2010-05-17
Okay, I think I've fixed the port 80 redirect issue. The problem was that 192.168.1.9 is a web server on port 80, so I added the rule

```

iptables -A FORWARD -i $INTERNET -p tcp --dport 80 -d 192.168.1.9 -m state --state NEW -j ACCEPT

```

and re-enabled port redirection to 3128
```

iptables -t nat -A PREROUTING -i $LAN_IN -p tcp --dport 80 -j DNAT --to $SQUID_SERVER:$SQUID_PORT
iptables -t nat -A PREROUTING -i $INTERNET -p tcp --dport 80 -j REDIRECT --to-port $SQUID_PORT


```

So far it's working, I'm not sure if the web server works anymore though, will have to test it from an external ip,

I still need to know if there is any "special" settings that I should change to be able to route incomming traffic on port 3308 to 192.168.1.9 and outgoing traffic to 3389.

I'm not sure why this network was set up this way, it was before my time...

---

### Post by benderisgreat on 2010-05-18
for all your forwarding rules you also need to accept ESTABLISHED connections. NEW will only match the first packet in a connection. Since your pc's are able to connect to the internet you either already have an ESTABLISHED rule or your policy on the FORWARD chain is set to accept. An accept policy allows for less configuration but you're not filtering the traffic. If you do not accept as a policy your > iptables -A FORWARD -i $INTERNET -p tcp --dport 80 -d 192.168.1.9 -m state --state NEW -j ACCEPT rule will not suffice. You can either have one rule to accept all established connecions:```
iptables -A FORWARD -m state --state ESTABLISHED -j ACCEPT

# allow outgoing connections from your lan:
iptables -A FORWARD -i $LAN_IN -j ACCEPT

# allow incoming connections to your server:
iptables -A FORWARD -i $INTERNET -p tcp --dport 80 -d 192.168.1.9 -m state --state NEW -j ACCEPT
``` or you can create pairs of rules like this:
```
iptables -A FORWARD -i $INTERNET -p tcp --dport 80 -d 192.168.1.9 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A FORWARD -o $INTERNET -p tcp --sport 80 -s 192.168.1.9 -m state --state ESTABLISHED
```

Before any traffic will be forwarded to 192.168.1.9 you need a prerouting rule so you'll get something like this:
```
iptables -t nat -A PREROUTING -i $INTERNET -p tcp --dport 80 -j DNAT --to-destination 192.168.1.9
iptables -A FORWARD -p tcp --dport 80 -d 192.168.1.9 -m state --state NEW -j ACCEPT
```
This rule conflicts with the above however:
> iptables -t nat -A PREROUTING -i $INTERNET -p tcp --dport 80 -j REDIRECT --to-port $SQUID_PORT
as it matches traffic coming in on the $INTERNET interface destined to port 80. You don't need this rule to have web traffic from your lan redirected to squid. REDIRECT can be used as an alternative to DNAT, but your DNAT rule:> iptables -t nat -A PREROUTING -i $LAN_IN -p tcp --dport 80 -j DNAT --to $SQUID_SERVER:$SQUID_PORTshould suffice.
> [..] a forwarding rule for 192.168.1.9 port 3308, but the outgoing port must be 3389 [..]
to be able to route incomming traffic on port 3308 to 192.168.1.9 and outgoing traffic to 3389.
Do you mean by this that your server needs to receive traffic on port 3308 but with a source port of 3389? If so you can use:
```
iptables -t nat -A PREROUTING -i $INTERNET -p tcp --dport 3308 -j DNAT --to-destination 192.168.1.9
iptables -t nat -A POSTROUTING -i $INTERNET -p tcp --dport 3308 -j SNAT --to-source :3389
iptables -A FORWARD -p tcp --sport 3389 --dport 3308 -d 192.168.1.9 -m state --state NEW -j ACCEPT
```

---

### Post by Nessaja on 2010-05-19
Thanks alot bender, it looks like it works now,

One thing, I get an error message - iptables v1.3.8: Can;t use -i with Postrouting, but this doesn't seem to affect anything, since the internet now works on all computers, I'll have to test the website (on 192.168.1.9) from an external ip though, will keep you posted on that.

> 
Do you mean by this that your server needs to receive traffic on port  3308 but with a source port of 3389? If so you can use:

What I mean by that is, this is how it's set up in Windows 2003 :

[IMG]http://s848.photobucket.com/albums/ab45/Nessaja1024/?action=view&current=portforwarding.jpg[/IMG][IMG]http://i848.photobucket.com/albums/ab45/Nessaja1024/portforwarding.jpg[/IMG]

I basically want the same setup than in Windows 2003 nut this Linux. Is this how you understood it?

Do you work with linux for a living? You're the only person that was able to help me with iptables, and I've posted my question on numerous forums, no one else was able to help me...

---

