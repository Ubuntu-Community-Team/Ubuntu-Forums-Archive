---
title: "How do I make the server route between"
date: 2010-11-09
forum: Server Platforms
---

### Post by mattegeniet on 2010-11-09
Hello everyone!

Sorry for writing this really long post, but don't want to miss anything. The important stuff is in the bottom though, so if you don't want to read all the background, then feel free to jump directly to the end.

For the last couple of days I've been building on a server built from an old (well, not too old) computer. My goal is to use it for multiple purposes like a webserver, home automation, and possibly a future media center (if I get my TV card to work). But perhaps the main reason is to get wireless access to the internet for my laptop, and to connect it to my other (stationary) computer. When I'm done I'm also planning on writing a guide for setting up an access point with the rt61 chipset, as there seems to be many people looking for this. First I just need to get through this problem though :(.

For this I use two wired NICs, **eth0** for the local interface to my computer, and eth1 as an external interface for the internet. Moreover I use a wireless NIC (DWL-G510 using the **rt61pci** driver) in conjunction with the daemon hostapd to provide a wireless interface for portable computers to connect to. **eth1** gets its IP through DHCP from my ISP, while **eth0** and **wlan0** have static IPs on two different subnets like this (copied from /etc/network/interfaces):

```
auto eth0
iface eth0 inet static
        address 192.168.1.1
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255

#wireless interface
auto wlan0
iface wlan0 inet static
        address 192.168.2.1
        network 192.168.2.0
        netmask 255.255.255.0
        broadcast 192.168.2.255

```

Dnsmasq is used as a simple dhcp-server and to get NAT functionality and a firewall I use the excellent arno-iptables-firewall script, which does almost everything I need. 

Now here's my problem: I want the two computers to be able to access each other over the network (mostly for file sharing through samba), but it seems that no data is able to travel between the subnets. Both computers are able to ping the server, but not each other (the server can ping both of them though). The obvious solution would be to bridge the interfaces with each other, and I tried it, and it worked. Unfortunately there seems to be a bug in the rt61pci driver that makes wireless computers drop the connection every 30 seconds or so, rendering it unusable, if encryption is used together with a bridge interface. It doesn't make sense, since it works with encryption when it's not bridged, and with the bridge if encryption is turned off.

To combat this I simply have to use two separate subnets (turned off encrytion is not an option living in a student dorm), but as I see it, it shouldn't be too hard to get the server to route everything that comes from eth0 to wlan0 and the other way around. And running **route -n** gives me that it knows everything it needs to know to route it correctly. To make sure it's not stopped by the firewall I also added this to /etc/arno-iptables-firewall/custom-rules :
```

iptables -t filter -I FORWARD 1 -i eth0 -o wlan0 -j ACCEPT
iptables -t filter -I FORWARD 1 -i wlan0 -o eth0 -j ACCEPT

```

However, the computers still can't ping eachother. By above rule being there, there shouldn't be anything in the firewall that stops this from happening, also I can't find anything in the logs, making me believe that it hasn't fully understood that it should not only route from the internal network to the external, but also inside the internal network itself. Is this done by iptables, or in some other exotic fashion? I read somewhere about ip_forward, does that have something to do with this?

Would be really grateful if someone could clear things up for me, since I've now spent several days trying to get this to work..

EDIT:
An other interesting observation: When I ping a computer that is there, the gateway seems to drop the request somewhere since I just get timeouts, but if I try to ping an IP without any host connected to it, but on another subnet, i get the response "reply from 192.168.1.1: Destination host unreachable". Does this suggest that it actually forwards my packets but then drops the replys? What I don't understand is why it would do that when I'm pingin internal computers, since I can ping for example google.com without any problems at all from all the computers on the network...

EDIT2:
Even more interesting! I seem to be able took the old game age of empires 2 and started a network game, to see if that worked, and it did! Hence my gateway actually does execute routing functionality. Still can't ping neither of the hosts though, and samba still doesn't work.. 

By the way, is there any way to make broadcasts be forwarded too, as they would have been with a bridge? For example, if I changed the broadcast address of both my interfaces to 192.168.255.255, and did the same thing in my dhcp, what would then happen?

---

### Post by WinstonChurchill on 2010-11-09
Have you done this? (as root)
```
echo "1" > /proc/sys/net/ipv4/ip_forward
```
Or, alternatively, add to /etc/sysctl.conf:
```
net.ipv4.ip_forward=1
```

If that's not it, post the output of the following commands:
```

iptables -L -v -n
ip route
ifconfig -a

```

---

### Post by mattegeniet on 2010-11-10
net.ipv4.ip_forward=1 was outcommented in /etc/sysctl.conf, and now after restart I have a single 1 in /proc/sys/net/ipv4/ip_forward. However it still doesn't work, and since I can play age of empires 2 over the network if I manually enter the IP address, that's probably not it. I also got the output from iptables, and it's attached to this post. Apparantly the file is to big to upload, so I divided it in 2 parts. I included the ones from the nat and mangle tables too, in case it's valuable too.

I've tried to look through the ruleset, and as I see it, packets going from one computer to the other should immediatly hit the accept rule, and thereby bypass the chain. My knowledge of iptables is very limited though, as all I know is what I read this weekend. However, i noticed the output also showed the number of packets to hit every rule, and tested it. I checked the output, then pinged one of the cumputers from the other with 4 pings, and when I checked again, the counter had increased exactly 4 steps. However, I didn't see any new packets hitting the rule for the other direction, which I think there should have been, for the replies from the ping. I'm just getting more and more confused...:confused:

---

### Post by WinstonChurchill on 2010-11-10
That has to be the most confusing iptables setup I've ever seen; something in your iptables is probably causing your issues, and I'm not about to try and go through that and figure it out... I would advise that you ditch that pre-made script you're using and just learn iptables yourself - it's really not that difficult, and there are several excellent tutorials to be found about the internet.

And also, I'd use the real dhcp3-server for DHCP - it's a good thing to know how to use.

I've attached an iptables script that I use on my server to give you some idea of where I'm coming from.

---

### Post by mattegeniet on 2010-11-11
Yeah, I suppose there are a lot of chains in the script, and maybe I should try to make my own ruleset, since I think I've understood most ibtables already. I just thought that a script that has been around for several years and used by many people would be better tested and hence more secure. But on the other hand I could look at this script and enter some rules at a time, and then see where the problem arises :). I'll take a look at it when I get time (probably this weekend) and if I find something, I'll post it here, in case someone else is in the same situation.

thanks for your help!

---

