---
title: "Port fowarding help?"
date: 2006-08-25
forum: Server Platforms
---

### Post by backu on 2006-08-25
I'm not real savvy with linux stuff, especially iptables. My problem is this. I play some online games through my PS2 which require 1001 ports open to it, and it seems that Ubuntu is blocking them all cause I cannot get my voice service working.

My Ubuntu system has 2 NIC's, eth0 is dynamically assigned by my ISP, and eth1 is static to 10.10.0.1. My network runs off DHCP in the 10.10.10.x range. I need to foward udp ports 6000-7000 to my ps2 which never has the same IP at any given time. I also have 2 systems on my network, so they both have to be able to get the data on those ports. I was plotting to forward the ports to 10.10.10.255 hopeing broadcast would work, but I also thought about sending them to 10.10.0.0/8 or /16.. Is this possible? And how so? Any and all help is greatly appreciated.

---

### Post by Woei on 2006-08-25
> **backu said:**
> I'm not real savvy with linux stuff, especially iptables. My problem is this. I play some online games through my PS2 which require 1001 ports open to it, and it seems that Ubuntu is blocking them all cause I cannot get my voice service working.

My Ubuntu system has 2 NIC's, eth0 is dynamically assigned by my ISP, and eth1 is static to 10.10.0.1. My network runs off DHCP in the 10.10.10.x range. I need to foward udp ports 6000-7000 to my ps2 which never has the same IP at any given time. I also have 2 systems on my network, so they both have to be able to get the data on those ports. I was plotting to forward the ports to 10.10.10.255 hopeing broadcast would work, but I also thought about sending them to 10.10.0.0/8 or /16.. Is this possible? And how so? Any and all help is greatly appreciated.

A tad confusing.

The problem with forwarding is that you generally need to know the IP address of the system you're interested in forwarding ports to. You cannot forward to a broadcast or network address, as the kernels of other systems on the network would simply send a TCP RST to kill the connection, as they have no programs listening on those ports.

I have no experience configuring PS2 consoles, but either you configure your PS2 to use a *static* address, or you configure your DHCP server running on the gateway to give a very specific IP address to your PS2 based on it's ethernet MAC address (sniff it if you have to). Configuring your DHCP server to do something like that is server dependent, but is generally something along the lines of the following stanza:

```

hardware ethernet 00:11:33:44:55:66;
fixed-address 10.1.2.3;

```

But really, limiting the range of your DHCP server to say 50 addresses, and picking a static address for your PS2 is probably easier.

Once you know the IP address of your PS2, forwarding the correct ports becomes childs play:
```

# Do address translation/NAT
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
# Allow packets that are going to be relayed to the internet from the internal LAN to pass through
sudo iptables -t filter -A FORWARD -o eth0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
# Allow packets related to connections iniated *from* the lan to get back in
sudo iptables -t filter -A FORWARD -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow connections from the internet to port 6000-7000 through and forward 
# it to the internal PS2
iptables -t filter -A FORWARD -p udp -i eth0 -d ip.of.ps.2 -m multiport --dports 6000-7000 -j ACCEPT
# Finally, translate the destination address for packets arriving at the public IP to the
# IP address of the internal PS2
iptables -t nat -A PREROUTING -i eth0 -p udp -m multiport --dports 6000-7000 -j DNAT --to-destination ip.of.ps.2

```

I don't understand what you want those other 2 systems to be able to do. Do they have to be able to send packets to the PS2 ? (They can, even without a gateway). Do they just need to get on the net ? (They can with the above). Something else ?

---

### Post by backu on 2006-08-25
I don't care about the other systems and those ports, just the 2 ps2's ( I can't forward to just one IP as I have 2 PS2's requiring those ports )

---

### Post by backu on 2006-08-25
Lemme try to clarify. Hardware routers, and even Win2k3 Ent routed packets from the internet on ports 6000-7000 to the network, and my (2) PS2's picked them up just fine. I can't figure out how to get Ubuntu to do that exact same thing (No, I'm not switching to a hardware router, or Win2k3 Ent (More than just the PS2's plug into the network port, as I have CAT5 ran from both PS2's and my computer down to my switch/server/modem, and they get swapped out with computer connections that need to be behind the server))

---

### Post by Woei on 2006-08-26
> **backu said:**
> I don't care about the other systems and those ports, just the 2 ps2's ( I can't forward to just one IP as I have 2 PS2's requiring those ports )

> **backu said:**
> Lemme try to clarify. Hardware routers, and even Win2k3 Ent routed packets from the internet on ports 6000-7000 to the network, and my (2) PS2's picked them up just fine. I can't figure out how to get Ubuntu to do that exact same thing (No, I'm not switching to a hardware router, or Win2k3 Ent (More than just the PS2's plug into the network port, as I have CAT5 ran from both PS2's and my computer down to my switch/server/modem, and they get swapped out with computer connections that need to be behind the server))


Well, if you're doing NAT, you can generally only forward ports to a certain machine. You can however, forward to a range of machines in round-robin style, but that's more for HTTP servers and the like, not for applications that need multiple ports to be forwarded to them simultaniously.

If it used to work with other NAT setups, that probably means the PS2 initiates connections to the outside. Once a connection is initiated, the netfilter code in the kernel will keep track of this established 'connection' (yes, even in the case of UDP, a connectionless protocol). Once packets arive back from the internet cloud, the netfilter code will look in its connection tracking table, and forward the packets back to the correct PS2. So try dropping the last two rules from the previous script, and try again.

If that doesn't work, try adding the last two rules back, and changing them to something like
```

iptables -t filter -A FORWARD -p udp -i eth0 -m multiport --dports 6000-7000 -j ACCEPT

iptables -t nat -A PREROUTING -i eth0 -p udp -m multiport --dports 6000-7000 -j DNAT --to-destination ip.of.ps.2-ip.of.ps.2

```

Both PS2's will need to have IP's next to eachother then though.

---

### Post by backu on 2006-08-28
Okay, tried all 3 ways now.. even gave the ps2 a static address.. still does not work.

Ports 6000 - 7000 & 10070 come from/go to a Server held by Sony. I cannot, in any manner through Ubuntu, get the data to work right. There are other ports being used, I'm sure are tcp, that work fine since I can login and play, but the voice runs on those ports, and it's dead air, even the game says no connection to voice server.. *sigh* I'm clueless.

---

### Post by Ptero-4 on 2006-08-28
Backu. It might be (since you said that it's a server held by sony) that there's a special app that traps the OS name and blocks or limits core functionality if the OS is not Windoze, (that might explain why the procedure that works on Windoze and the hardware router won't work on linux).

---

### Post by Woei on 2006-08-29
> **backu said:**
> Okay, tried all 3 ways now.. even gave the ps2 a static address.. still does not work.

Ports 6000 - 7000 & 10070 come from/go to a Server held by Sony. I cannot, in any manner through Ubuntu, get the data to work right. There are other ports being used, I'm sure are tcp, that work fine since I can login and play, but the voice runs on those ports, and it's dead air, even the game says no connection to voice server.. *sigh* I'm clueless.

Well, that's the problem really with most games, they specify a range of ports they use, completely against IETF policy of only using a single port (FTP is bad enough already). It would help if you could state the name of the game that is having problems. My guess is that there's still some number of other ports you have to open and forward to your PS2. Also, paste the output of iptables -L -v and iptables -t nat -L -v here.

Would it also be feasible to make the network silent, and attach the output of tcpdump (package has the same name) here ? Run something like
```

sudo tcpdump host ip.of.ps.2 and udp > snifflog

```

BTW, there is no such thing as routing packets from your gateway to your internal LAN for all machines to see. The best you can do with NAT is forward certain ports to a specific machine or a range of machines in round robin style.

---

### Post by jimm on 2006-08-29
Hi,

Is the PS2 traffic the only stuff going via your Ubuntu box? 

Don't want to state the obvious, but have you checked your machine is configured to forward between interfaces?

i.e. check /proc/sys/net/ipv4/ip_forward has a 1 in it and not a 0

I would assume your firewall config or whatever has already done this, but worth a check none the less!

Otherwise I suggest you have a look at the tcpdump output (as already suggested) and try and work out at what stage the packets are getting blocked.

Thanks,
James

Thanks,
James

---

### Post by backu on 2006-08-29
Firewall is disabled, Socom 3 is the game.

My network is setup like this:
               
Cable <-> Ubuntu eth0 <> eth1 <-> HUB <-> PS2(1) + PS2(2) + 3 Desktops + 1 WAP / 1 Laptop

I have other things to add to the network yet, and I have friends so my network changes in size quite frequently.

As for the outputs, I'll get back to you with those since I use my Win2k machine for the forum, and Xwin to connect to the server.

---

