---
title: "ip table questions"
date: 2008-11-09
forum: Server Platforms
---

### Post by paulus4605 on 2008-11-09
Hi 
I have the following script [http://paste.ubuntu.com/68985/](http://paste.ubuntu.com/68985/) coming from this website [http://rocky.eld.leidenuniv.nl/](http://rocky.eld.leidenuniv.nl/)

current network setup is this ISP => router => server and that needs to be adapted for learning purposes to ISP => server =Router.

I run on my server dhcp, bind dns, webserver, ftp, ssh, ntp, and samba.

how do I need to adapt the following script to redirect ports to make sure that I can access my server from the outside since all the ports under the port 1024 are closed. example ssh [email]paul@my.doma[/email]in -p22222 which is redirected to internal 22.

I also want to make sure that a range of ips are just have limited access to the internet with no access to download sites or p2p downloads.

since the support on this side is very poor I'm trying my luck here.

my server has 2 interfaces on the lan interface I have 1 switch for wireless and wired access and a second ap just wireless. 

do I need to have in my nat also wlan enabled?

thanks for your help.


Paul

---

### Post by paulus4605 on 2008-11-10
isn't there anybody that can help me out here ?

---

### Post by koenn on 2008-11-10
hm,  more than 1 day, 52 views, and still no replies ... 

Here are a couple of things to get you started :

First off, I don't think it's such a good idea to connect a server directly to the internet,  It would be better to use a dedicated PC for this purpose, especially while you still don't know how to set up iptables properly. But it's your server, so it's your call.

Secondly, that script you posted is way too complex, it's practically a program. You can't really expect someone else to work trough 1000+ lines of code just to explain to you what you have to do, can you ?  
Besides that, it's not going to help you learn iptables. 
Also, what you posted looks incomplete.


If I were you, i'd start from scratch : set up routing and masquerading (NAT), then start adding rules untill you have what you need.

1- routing is easy.
configure both NICs, 
execute
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
Your computer will now route between the (directly) connected networks.
You can veryfy this by running
```
route -n
```
the route command is also usefull to add routes should you need them.

2- set up masquerading
This is needed to let all hosts on the private network share the same public IP address.
```
IF_WAN=$( ifconfig eth0 | grep "inet addr" | cut -d: -f2 | cut -d' ' -f1 - )
iptables -t nat -A POSTROUTING -o $IF_WAN -j MASQUERADE

```

3- iptables
iptables has 3 'chains'
INPUT and OUTPUT govern traffic to and from your router (the machine running iptables)
FORWARD governs traffic going through the router (eg from your private network to the internet, or the other way around.)

you allow or deny traffic to by appending (-A) rules to the appropriate chain, e.g
```

#this is a classic : allow connections from private LAN to WAN (internet)
#assuming eth0 = WAN, eth1 = LAN
iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
iptables -A FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT

```

4- the "port forwarding" you describe is called Destination NAT (DNAT), and the rules look something like this;
eg redirecting traffic (public addres: )port 2222 -> 192.168.1.1 port 22/tcp

```

iptables -t nat -A PREROUTING -p tcp -i eth0 1 --dport 2222 -j DNAT --to 192.168.1.1:22
iptables -A FORWARD -p tcp -i eth0 -d 192.168.1.1 --dport 80 -j ACCEPT

```


Here's a good example with lots of explanations : [http://oceanpark.com/notes/firewall_example.html](http://oceanpark.com/notes/firewall_example.html)

This one has some interesting additional kernel configuration that may be suitable for a firewall: [http://www.sentry.net/~obsid/IPTables/rc.scripts.dir/current/rc.firewall.iptables.dual](http://www.sentry.net/~obsid/IPTables/rc.scripts.dir/current/rc.firewall.iptables.dual)

There are tons of iptables examples, on these forums and on the rest of the internet (google !)
'man iptables' is useful for looking up command syntax etc.

---

### Post by paulus4605 on 2008-11-10
koen
thanks for your remarks

I will look into them and try to do something usefull with them

Paul

---

