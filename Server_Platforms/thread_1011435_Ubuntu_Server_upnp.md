---
title: "Ubuntu Server upnp?"
date: 2008-12-14
forum: Server Platforms
---

### Post by abandonedthe_mulletator on 2008-12-14
I have a home network set up as follows:
Internet <--> Ubuntu Server <--> Router <--> Computers & XBOX

Everything works great on the computers but the XBOX can't connect to XBOX live.  It says my NAT is moderate and it needs to be open.  I searched on Google and found several sites on the subject.  The most relevant one that I found was published in 2006 and it said I need upnp on my server to use XBOX live properly.  Does anyone know how to get the XBOX live working on my server?

---

### Post by gtdaqua on 2008-12-14
why are you using a ubuntu server between router and internet?  cant you connect straight from the router to internet.

Internet <--> Router <---> Switch <---> Computers & XBOX.

Simpler the above way. Enable upnp on the router (most routers support this these days) and you should be good to go.

---

### Post by abandonedthe_mulletator on 2008-12-15
I'm using the server for a web based torrent client as well as a file server and a squid proxy server.

XBOX live works fine if I remove the server.

---

### Post by gtdaqua on 2008-12-15
Of course XBOX will work. Forcing the Ubuntu to filter traffic is going to be difficult. 

UPNP is nothing but a simple port forwarding mechanism - only that it requires no manual input from the user. The App that requests UPNP will automatically configure rules on the gateway device that supports UPNP. 

Check what is exactly required by the XBOX and manually forward it by Squid.

---

### Post by abandonedthe_mulletator on 2008-12-15
I found this on a post at another forum:
```
 
   $IPTABLES -t nat -A PREROUTING -i $WAN_IF -p tcp --dport 3074 -j DNAT --to-destination $XBOX_IP
   $IPTABLES -t nat -A PREROUTING -i $WAN_IF -p udp -m multiport --dports 88,3074 -j DNAT --to-destination $XBOX_IP
   $IPTABLES -A FORWARD -i $WAN_IF -d $XBOX_IP -p tcp --dport 3074 -j ACCEPT
   $IPTABLES -A FORWARD -i $WAN_IF -d $XBOX_IP -p udp -m multiport --dports 88,3074 -j ACCEPT
```

The guy on that forum was trying to share a conection with a desktop PC running ubuntu and a wireless connection.  Like this:
Wireless <--> Desktop <--> XBOX

He had it all set up but had the same NAT problem and he said that these mods to his iptables fixed it in his application.

I don't really understand the $WAN_IF part.  If I fill in my XBOX IP and whatever should go in the $WAN_IF spot will it work?  I disabled squid for now to simplify things.

---

### Post by Robstarusa on 2008-12-15
You do not need upnp to get xbox to work.  UPNP actually should be disabled.  It is seriousl the worst idea, EVER, with respect to networking security.

Google "xbox live tcp udp ports" and you should quickly figoure out which ports to open.

---

### Post by abandonedthe_mulletator on 2008-12-15
Thanks.  You guys are right I don't need upnp.
I found the ports that I need open from the microsoft website:

The following ports must be available to your Xbox 360 console for Xbox LIVE to operate correctly:

    * TCP 80
    * UDP 88
    * UDP 3074
    * TCP 3074
    * UDP 53
    * TCP 53

I don't really understand what ports are or how to open them.  I know it will be some kind of iptables command but that is all I know.

---

### Post by gtdaqua on 2008-12-16
> **the_mulletator said:**
> I found this on a post at another forum:
```
 
   $IPTABLES -t nat -A PREROUTING -i $WAN_IF -p tcp --dport 3074 -j DNAT --to-destination $XBOX_IP
   $IPTABLES -t nat -A PREROUTING -i $WAN_IF -p udp -m multiport --dports 88,3074 -j DNAT --to-destination $XBOX_IP
   $IPTABLES -A FORWARD -i $WAN_IF -d $XBOX_IP -p tcp --dport 3074 -j ACCEPT
   $IPTABLES -A FORWARD -i $WAN_IF -d $XBOX_IP -p udp -m multiport --dports 88,3074 -j ACCEPT
```

The guy on that forum was trying to share a conection with a desktop PC running ubuntu and a wireless connection.  Like this:
Wireless <--> Desktop <--> XBOX

He had it all set up but had the same NAT problem and he said that these mods to his iptables fixed it in his application.

I don't really understand the $WAN_IF part.  If I fill in my XBOX IP and whatever should go in the $WAN_IF spot will it work?  I disabled squid for now to simplify things.

That's a script. Anything that begins with $ is a symbolic reference. I grabbed that post from: [url="http://www.linuxquestions.org/linux/answers/Networking/Connecting_to_XBox_Live_through_a_linux_computer_connected_to_a_wireless_LAN"]
Connecting to XBox Live through a linux computer connected to a wireless LAN[/url].

$IPTABLES will be either be iptables or squid equivalent. $WAN_IF is the wan interface of the squid server. $XBOX_IP will be the IP of XBOX.

So for e.g. this command:
```

$IPTABLES -A FORWARD -i $WAN_IF -d $XBOX_IP -p udp -m multiport --dports 88,3074 -j ACCEPT

```

is actually:

```

iptables -A FORWARD -i eth0 -d 192.168.1.50 -p udp -m multiport --dports 88,3074 -j ACCEPT

```

where "iptables" is the command; eth0 is the interface of the squid server connected to the internet-router; and 192.168.1.50 is the IP of the XBOX.

---

### Post by abandonedthe_mulletator on 2008-12-17
I tried the following commands:
```

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 3074 -j DNAT --to-destination 192.168.0.39
iptables -t nat -A PREROUTING -i eth0 -p udp -m multiport --dports 88,3074 -j DNAT --to-destination 192.168.0.39
iptables -A FORWARD -i eth0 -d 192.168.0.39 -p tcp --dport 3074 -j ACCEPT
iptables -A FORWARD -i eth0 -d 192.168.0.39 -p udp -m multiport --dports 88,3074 -j ACCEPT
sudo /sbin/ifconfig eth1 mtu 1500
sudo /sbin/ifconfig eth0 mtu 1500
```


eht0 is my network card to my LAN
eth1 is my network card to the internet
192.168.0.39 is my XBOX's IP

the XBOX still says I have a moderate NAT:confused:

What do I need to do?

---

### Post by gtdaqua on 2008-12-17
> **the_mulletator said:**
> I tried the following commands:
```

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 3074 -j DNAT --to-destination 192.168.0.39
iptables -t nat -A PREROUTING -i eth0 -p udp -m multiport --dports 88,3074 -j DNAT --to-destination 192.168.0.39
iptables -A FORWARD -i eth0 -d 192.168.0.39 -p tcp --dport 3074 -j ACCEPT
iptables -A FORWARD -i eth0 -d 192.168.0.39 -p udp -m multiport --dports 88,3074 -j ACCEPT
sudo /sbin/ifconfig eth1 mtu 1500
sudo /sbin/ifconfig eth0 mtu 1500
```


eht0 is my network card to my LAN
eth1 is my network card to the internet
192.168.0.39 is my XBOX's IP

the XBOX still says I have a moderate NAT:confused:

What do I need to do?

I forgot to give you one important detail. You need to forward all traffic from eth0 (local interface) to eth1 (internet interface). Based on your setup, the command will be:

```

iptables -t nat -A POSTROUTING -o eth1 -s 192.168.0.0/24 -j MASQUERADE

```

This is assuming that 192.168.0.0/24 is the network used by eth0 and XBOX.


In your commmands, you have given the wrong values. 
All your commands are referring to eth0 while they should refer to eth1. Your eth1 which is connected to the Internet is the WAN interface. Replace all your eth0 with eth1 in the commands.

Before doing all this, clear all your iptable rules and start from scratch.

---

### Post by fatbastard spice on 2008-12-17
Are you actually trying to control the ports that your local computers/xbox can use? If not,  i just use a few general rules to give lan machines relatively unfettered access.

```
iptables --append INPUT --in-interface $INSIDEWORLD -j ACCEPT
iptables --append OUTPUT --out-interface $INSIDEWORLD -j ACCEPT
iptables --append FORWARD --in-interface $INSIDEWORLD -j ACCEPT
iptables --table nat --append OUTPUT -s $LANRANGE -j ACCEPT
iptables --table nat --append POSTROUTING --out-interface $INSIDEWORLD -j ACCEPT
iptables --table nat --append PREROUTING -s $LANRANGE -j ACCEPT
```

$INSIDEWORLD the lan interface (eth1 for me)
$LANRANGE the lan addresses i'm dolling out

Couple that with a rule to allow established and related connections and as long as they don't want a port actively forwarded i can forget about their networking needs. This also works for the xbox here which is in a similar position to yours.

Of course if they download trojans (and they have - bloody kids) they've got pretty unfettered access to the wide world.

---

### Post by abandonedthe_mulletator on 2008-12-17
> 
Replace all your eth0 with eth1 in the commands.

Before doing all this, clear all your iptable rules and start from scratch.

I did that and it still didn't work.  The XBOX says my MTU setting is too low.  I changed the MTU setting on both my network cards to 1500 suing ifconfig.  The XBOX still says my MTU setting is too low:mad:.  I tried fatbastard spice's suggestion with the following script:
```
#! /bin/bash

## Reset rules
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -F
sudo iptables -X
echo "Rules Reset"

sudo /sbin/ifconfig eth1 mtu 1500
sudo /sbin/ifconfig eth0 mtu 1500

sudo iptables --append INPUT --in-interface eth1 -j ACCEPT
sudo iptables --append OUTPUT --out-interface eth1 -j ACCEPT
sudo iptables --append FORWARD --in-interface eth1 -j ACCEPT
sudo iptables --table nat --append OUTPUT -s 192.168.1.0 -j ACCEPT
sudo iptables --table nat --append POSTROUTING --out-interface eth1 -j ACCEPT
sudo iptables --table nat --append PREROUTING -s 192.168.1.0 -j ACCEPT
echo "New Rules set"

```

I still have the MTU problem.  I confirmed that the MTU settings are 1500 by running ifconfig.  I also know that there is no problem with my router or modem because I was playing online with the server disconnected earlier today.

---

### Post by abandonedthe_mulletator on 2008-12-19
No replies?

What could be causing my MTU problem?

---

### Post by badm0nk3y369 on 2009-05-19
> **the_mulletator said:**
> No replies?

What could be causing my MTU problem?

Hey there. 
Just found this thread.
You could try setting your MTU values to 1492.
Some ISPs max out at that value, and not 1500.

---

