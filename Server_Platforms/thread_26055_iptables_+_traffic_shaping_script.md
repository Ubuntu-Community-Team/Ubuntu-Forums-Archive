---
title: "iptables + traffic shaping script"
date: 2005-04-11
forum: Server Platforms
---

### Post by ubuntu_demon on 2005-04-11
Hi,

I'm currently working on writing my own iptables script and integrating it with nice traffic shaping.

I have a combined internet gateway/server running :
amule,bittorrent,vncserver,ssh,samba

I also work on it from school occasionaly. So I need to be able to browse and stuff.

I have a 2560 / 520 connection ... I have experimented with using wondershaper a bit and  I have found 2400 520 work nicely.

my gateway has two nics. eth1 is the one connected to my modem and eth0 is the one connected to my lan.

here's the script I am working on (the tc part still misses) :

```

# Flushing all tables
iptables -F

### filter

iptables -t filter -P INPUT DROP
iptables -t filter -P OUTPUT ACCEPT
iptables -t filter -P FORWARD ACCEPT

# allow local loopback connections
iptables -t filter -A INPUT -i lo -j ACCEPT

# drop INVALID connections
iptables -t filter -A INPUT   -m state --state INVALID -j DROP
iptables -t filter -A OUTPUT  -m state --state INVALID -j DROP
iptables -t filter -A FORWARD -m state --state INVALID -j DROP

# allow all established and related
iptables -t filter -A INPUT   -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -t filter -A OUTPUT  -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -t filter -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

# allow connections to my ISP's DNS servers
iptables -t filter -A INPUT -s 213.73.255.52 -p tcp -m tcp ! --tcp-flags SYN,RST,ACK SYN -j ACCEPT 
iptables -t filter -A INPUT -s 213.73.255.52 -p udp -j ACCEPT 
iptables -t filter -A INPUT -s 213.132.189.250 -p tcp -m tcp ! --tcp-flags SYN,RST,ACK SYN -j ACCEPT 
iptables -t filter -A INPUT -s 213.132.189.250 -p udp -j ACCEPT 
iptables -t filter -A INPUT -s 213.73.255.53 -p tcp -m tcp ! --tcp-flags SYN,RST,ACK SYN -j ACCEPT 
iptables -t filter -A INPUT -s 213.73.255.53 -p udp -j ACCEPT 

#ping
iptables -t filter -A INPUT -p icmp --icmp-type echo-request -m limit --limit 10/sec -j ACCEPT

#open ports 4662,4672 = amule, 5900,5901 = vnc, 22 = ssh
iptables -t filter -A INPUT -p tcp -m tcp --dport 4662 -j ACCEPT 
iptables -t filter -A INPUT -p udp -m udp --dport 4672 -j ACCEPT
iptables -t filter -A INPUT -p tcp -m tcp --dport 5900 -j ACCEPT 
iptables -t filter -A INPUT -p tcp -m tcp --dport 5901 -j ACCEPT 
iptables -t filter -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT 

#bittorrent :
iptables -t filter -A INPUT -p tcp -m tcp --dport 6881:6889 -j ACCEPT 

#samba (only connections from lan are accepted)
iptables -t filter -A INPUT -o eth0 -s 192.168.0.0/255.255.255.0 -p tcp -m tcp --dport 137:139 -j ACCEPT 
iptables -t filter -A INPUT -o eth0 -s 192.168.0.0/255.255.255.0 -p udp -m udp --dport 137:139 -j ACCEPT 
iptables -t filter -A INPUT -o eth0 -s 192.168.0.0/255.255.255.0 -p tcp -m tcp --dport 445 -j ACCEPT 
iptables -t filter -A INPUT -o eth0 -s 192.168.0.0/255.255.255.0 -p udp -m udp --dport 445 -j ACCEPT 

# log all other attempted in going connections
iptables -t filter -A INPUT -o eth0 -j LOG

### nat

# set up IP forwarding and nat
iptables -t nat -P POSTROUTING ACCEPT
iptables -t nat -P PREROUTING ACCEPT

# 6891:6900 = msn filetransfers
# 192.168.0.1 = gateway
# 192.168.0.216 = client in network
iptables -t nat -A PREROUTING -i eth1 -p tcp -m tcp --dport 6891:6900 -j DNAT --to-destination 192.168.0.216:6891-6900 
iptables -t nat -A PREROUTING -i eth1 -p udp -m udp --dport 6891:6900 -j DNAT --to-destination 192.168.0.216:6891-6900 
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

```

I would like some input/tips. I haven't tested the script yet.

here are some resources that I used or am going to use :

[http://gentoo-wiki.com/HOWTO_Packet_Shaping](http://gentoo-wiki.com/HOWTO_Packet_Shaping)
[http://lartc.org/howto](http://lartc.org/howto) 
[http://linuxgazette.net/103/odonovan.html](http://linuxgazette.net/103/odonovan.html)
[http://www.netfilter.org/documentation/](http://www.netfilter.org/documentation/)
[http://www.knowplace.org/shaper/](http://www.knowplace.org/shaper/)
[http://linux-ip.net/articles/Traffic-Control-HOWTO/](http://linux-ip.net/articles/Traffic-Control-HOWTO/)
[http://howtos.linux.com/howtos/Traffic-Control-HOWTO/intro.shtml](http://howtos.linux.com/howtos/Traffic-Control-HOWTO/intro.shtml)
[http://andthatsjazz.org:8/lartc/](http://andthatsjazz.org:8/lartc/)

What do you think of this iptables script ? improvements ? Did I make any errors ?

Do you guys have any good resources on traffic shaping with tc ?

---

### Post by ubuntu_demon on 2005-04-12
here's the mangle part. I would especially like comments on this (and the tc part that follows later)

I have only 1 client pc of my gateway.

I don't prioritize incoming packages.  Because of the text from [http://www.knowplace.org/shaper/qdisc.html](http://www.knowplace.org/shaper/qdisc.html) quoted here  :

> 
[SIZE=1]All about the egress

A word about egress, traffic is ONLY shaped when it leaves a network interface. If you have only one network interface, the traffic shaping you do is on traffic leaving your machine. There is ~no way to control what packets people send you on your external interface or the order they might arrive. You can only control what you send out. Even though you can police inbound traffic on the external interface, it isn't abundantly clear that it makes much difference.

Lets say you have an external interface (eth0) and an internal interface (eth1), if you want to shape traffic coming into your network (ingress), it could be done on eth1. If you want to shape traffic leaving your network, the shaping is done on eth0.
Ingress, dammit!

No. Go read up on the resources section and knock yourself out.

By the time that the traffic has shown up at your box, there's not a whole lot you can do about it. You could of course delay or drop the packets, but there doesn't seem to be much of a point. From what I've seen, ingress policing gets you about the same result as if you've simply done nothing. Also, there's very little you can do on your ingress side that's going to change what's going to happen on my egress side. If we have different priorities, my egress will always win over your ingress. =)
[/SIZE]


edit : 
I removed the mangle part because it's still a work in progress

I found some other good resources but I'll sort them out after I've read most of them. Here's one already  :[http://talk.trekweb.com/~jasonb/articles/traffic_shaping/index.html](http://talk.trekweb.com/~jasonb/articles/traffic_shaping/index.html)

---

### Post by guysmiley25 on 2007-05-26
Have you had any luck with this script?

---

### Post by ubuntu_demon on 2007-05-26
> **guysmiley25 said:**
> Have you had any luck with this script?
yeah I use it for myself. It's not very userfriendly unless you know how it works.

---

### Post by guysmiley25 on 2007-05-29
I'm trying to make my own script, but finding really hard to understand. I have a similar setup as you.

Do you know if you can limit the speed on certain ports using IPTABLES or something else?

---

### Post by ubuntu_demon on 2007-05-29
> **guysmiley25 said:**
> I'm trying to make my own script, but finding really hard to understand. I have a similar setup as you.

Do you know if you can limit the speed on certain ports using IPTABLES or something else?
Yeah it takes a little bit of time to figure it out and understand it.

I'm using iptables to divide the traffic in groups and using tc to do the actual traffic shaping.

For more information about tc : 
$man tc
(or use google)

Feel free to ask any question though I'm no expert. I can share my script if you want.

---

### Post by guysmiley25 on 2007-05-30
I've got an interesting question.

Do you think it would be possible to limit your bandwidth inversely proportional to how much traffic your used for each month.

So in my case, I have a 20GB cap per month on my internet connection. Then I get charged per MB.

So I would want a function B(u). Where B denotes bandwidth, and u denotes amount used so far. Such that B(0)=infinity, and as B(u) apporches u=18GB, then limit off to 128.

I hope that makes sense, if not don't worry about it, I think I might start a thread.


Anyways thanks for all your help so far. So do you have a working script at the moment that blocks certain ports and opens certain ports to the internet, and uses tc to limit bandwidth? If so yes it would be very nice if I could have a look at that.

So what do you mean by using iptables to divide traffic into groups?

---

### Post by ubuntu_demon on 2007-05-31
> **guysmiley25 said:**
> I've got an interesting question.

Do you think it would be possible to limit your bandwidth inversely proportional to how much traffic your used for each month.

So in my case, I have a 20GB cap per month on my internet connection. Then I get charged per MB.

So I would want a function B(u). Where B denotes bandwidth, and u denotes amount used so far. Such that B(0)=infinity, and as B(u) apporches u=18GB, then limit off to 128.

I hope that makes sense, if not don't worry about it, I think I might start a thread.


Yes I think it's possible but you have to make it yourself :)

Maybe you can learn some stuff from monitor_tc_top.pl available at [http://www.docum.org/docum.org/monitor/](http://www.docum.org/docum.org/monitor/)

> **guysmiley25 said:**
> 
Anyways thanks for all your help so far. So do you have a working script at the moment that blocks certain ports and opens certain ports to the internet, and uses tc to limit bandwidth? If so yes it would be very nice if I could have a look at that.

So what do you mean by using iptables to divide traffic into groups?

tc calls it classes if that's more clear to you. See the source code of my script for more information. If you don't understand stuff start by reading :

[http://edseek.com/~jasonb/articles/traffic_shaping/](http://edseek.com/~jasonb/articles/traffic_shaping/)
[http://edseek.com/~jasonb/articles/traffic_shaping/scenarios.html](http://edseek.com/~jasonb/articles/traffic_shaping/scenarios.html)
[http://gentoo-wiki.com/HOWTO_Packet_Shaping](http://gentoo-wiki.com/HOWTO_Packet_Shaping)

Otherwise read up on the url's from my first post. Otherwise just ask :)

Regards,

ubuntu_demon

---

