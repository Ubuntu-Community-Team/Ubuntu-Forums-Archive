---
title: "Setting up ubuntu as a router, traffic shaper, and cache proxy"
date: 2008-10-10
forum: Server Platforms
---

### Post by Aeros84 on 2008-10-10
Hi guys,

Before I start: I know there are tutorials and how-to's out there for everything I listed in the subject, but given the fact that I'm dangerous around any Linux-related thing's I don't fully understand yet, I thought it best to get your input first :)

Ok, so, I have a server running Ubuntu for our office (about 6 pc's in the office). The only relevant daemon it's running at the moment is sshd, just so I can log on to it and do whatever else needs to be done still. We need this server to do the following:

- Act as a development webserver (apache, php, mysql).
- Act as a router between the LAN and the WAN (ADSL).
- Act as a cache proxy so as to cut total bandwidth usage, as our employees browse sites that can easily be cached.
- Act as a traffic shaper/limiter, so as to limit transfer rates per PC. (For instance, PC1 should be limited to a total transfer rate to the Internet of 10kbps, but unlimited transfer rate to the rest of the LAN. PC2 should be limited to Internet transfer rates of 15kbps, but also unlimited transfer rates to the rest of the LAN. And so on)

Now, the development webserver part of it I can get done on my own, have done it quite a few times before and shouldn't be a problem. However, the router, shaper and cacheproxy (and I suspect they are intertwined?) is a totally new thing to me. Since I'm the only sysadmin in the company, with experience in Windows servers but next to none in Linux, it falls to me to get it sorted out. Yay.

Just a few details first, to give you a better idea of the physical setup we have at the moment:

All the computer's have IP's in the 10.0.0.x range. They all plug directly into the ADSL router (well, via a switch, but still directly), and the ADSL router's IP is 10.0.0.2. It is setup in routed mode, so no one needs to establish the connection or dial in or anything. Plug & play, pretty much :P

The Linux box will now have to stand between the switch-hub and the ADSL router, I assume. It has two NIC's, so it's ready to be set up as a router/shaper/proxy, but aha! Now the fun starts... Here are a few things I'm clueless about:

1) Which card is eth0 and which is eth1? I tried testing it by setting the IP of eth0 to 10.0.0.1 (so it's on the same range as the LAN for now) and switching the cable between the 2 NIC's until I could ping it. But lo and behold, when I did the same test for eth1, it ended up being the same NIC. So what the heck then?

2) Will it be fine if the ADSL router is in routed mode, meaning the Linux box won't have to establish the ADSL connection? Surely it should be okay, since we're just bridging the gap between the LAN and the WAN (which is, in turn, also a LAN, if you consider that the ADSL router connects to the Linux box via ethernet cable). If this makes any sense...

3) Am I right in assuming that the PC's IP's can stay the same, e.g. 10.0.0.3, 4, etc. The internal interface on the Linux box should be 10.0.0.1, and the external interface 192.168.0.1, with the ADSL router's IP set to 192.168.0.2? (At the moment, like I mentioned, the ADSL router is set to be 10.0.0.2, with the PC's set to 10.0.3, t, 5, etc.)

4) I guess I can follow separate tutorials to set up a cache proxy (probably squid?), a router, and a traffic shaper. But since each of those will interact with iptables, and so on, in different ways, this would probably result in a nice conflicting mess in the iptables.

So as you can see, I clearly need a little assistance. I don't expect to be spoonfed, I'm more than willing to do some research and find tutorials for what I need done, but as I mentioned above in point #4, I'm a bit wary of just blindly following tutorials when I don't really understand the inner workings yet.

Thank you in advance, guys :)

---

### Post by NetSkay on 2008-10-10
for cacheproxy i would definately use squid proxy, i might be wrong as a new user, but i dont think squid uses IP tables, rather it uses rules based on its configuration file so no worries there...
for NAT and routing check this out
[http://www.aboutdebian.com/proxy.htm](http://www.aboutdebian.com/proxy.htm)
ubuntu us debian based so it shouldnt be a problem also
though i think to be on the safe side, for firewall and routing i would go with smoothwall, since its already preconfigured, unless you really want to do it yourself, and put the production server on the orange NIC of smoothwall so it has direct outside connection
also im sure if u google iptables and simply "confugirng linux as NAT" you would find plenty of tutorials and guides... if u need more help let me know, i would also be interested in setting up NAT routing and playing around...

---

### Post by Aeros84 on 2008-10-10
Thanks, will check it out :)

As for a firewall - I'm not really too worried about that, since the Linux box is behind the ADSL router, which won't let any traffic past it anyway.

EDIT: I went through that how-to, and here is my first obstacle:

> 
# If your external interface uses a static IP address

    * Uncomment the EXTIP line and enter your static IP address 

Section C
# If your external interface uses a dynamic IP address

    * Uncomment the EXTIP line 


and

> 
   #   If you specified a NIC (i.e. "eth0" or "eth1" for
   #   the external interface (EXTIF) variable above,
   #   AND if that external NIC is configured with a
   #   static, public IP address (assigned by your ISP),


The Linux external interface (eth1) just connects to the ADSL router via ethernet, and is therefore a fixed IP, **but NOT an ISP-assigned fixed IP** In other words, the external interface's IP would be 192.168.0.1, and the ADSL router would be 192.168.0.2... so how do you specify this? Do you just use 192.168.0.1 as the fixed IP?

---

### Post by Aeros84 on 2008-10-11
Guys, how about this:

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
iptables -t nat -A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 10.0.0.1:3128
iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128

To enable NAT between eth1 (internal) and eth0 (external), and ALSO to forward all port 80 traffic to the squid proxy (which is transparent).

Would that work?

If so, few questions:

1) Will this enable FULL traffic flow from eth1 to eth0 and beyond? On all ports, everything? Looks like it should. But will it at least prevent them from accessing devices on eth0's side of the box? Like the ADSL router, for instance, which is 192.168.0.2 (and the Linux box's eth0 is 192.168.0.1).

2) Would this effectively connect the LAN users to the Internet, considering they set 10.0.0.1 as their gateway? And considering that the Linux box's eth0 interface connects via ethernet to the ADSL router, which is always active and in routed mode?

3) Since this is a transparent proxy, and we're only forwarding port 80 to Squid on the linux box, I assume the Safe_ports directives in the squid.conf is now useless? Which I don't mind, just want to make sure.

4) How would squid know, once it has received the http traffic from the LAN, that it needs to interface to eth0 to find it on the Internet (WAN)? Instead of trying on eth1. This is probably a stupid question, come to think of it :P But seriously though. Consider the IPTABLES at the top. All traffic is routed to eth0, but port 80 traffic is routed to port 3128 internally. Then what?

---

### Post by vesord on 2010-01-26
Hi, I am a system administrator at an ISP company. We are using Ubuntu server distribution for constraining the download and upload speed for our clients. The system is using gugabyte LAN cards with a traffic going through it of approximately 800 MB/sec.
The number of clients reaches 3000, and the number of those who require shaping is up to 500. I am using tc.
I found it interesting that when using a system with a newer kernel, there is higher load average and consequenty delays (ping times > 20-30 ms). For example, when using 2.6.27, the average load is 0.3, while with 2.6.28 - it is 0.6. I tried with 2.6.31 - it gets even worse.
Could anybody give me advice for an optimal configuration of this type of system? What should be the value of CONFIG_HZ and of other important parameters?
The system is working with cpu Core I5 661 and it is being used only for shaping

---

