---
title: "Grr.  Almost there with nat..."
date: 2015-04-26
forum: Server Platforms
---

### Post by fizgig on 2015-04-26
I have an asterisk server#1 (privateIP1) behind a plain old wifi access point (PublicIP1) in one city and another asterisk server#2 (privateIP2) behind an ubuntu server (acting as a gateway with PublicIP2) in another city.

So, both asterisk servers are hidden behind routers using NAT but port forwards are activated on both sides to port udp 4569 to each respective asterisk server.  I watch the communication between them as such:

tcpdump for port 4569 on privateIP1 (asterisk#1):

(PrivateIP1) > (PublicIP2)  (asterisk#1 trying to get out to the internet to where PublicIP2 is)
(PublicIP2) > (PrivateIP1)  (asterisk#1 receiving a packet from the internet)

That looks great.  PrivateIP1 thinks it's having a conversation with PublicIP2 because it sends packets there and the packets return from there.  It doesn't know that the packets are forwarded by PublicIP2 to PrivateIP2 and then reversed on the way back.  It never sees PublicIP1 or PrivateIP2 on the packets.  Great.

Now, tcpdump on privateIP2 (asterisk#2):
(PrivateIP2) > (PublicIP1)  (asterisk#2 trying to get out to the internet where PublicIP1 is)
(PublicIP2) > (PrivateIP2)  (asterisk#2 receiving a packet from the internet)

Do you see what's wrong there?  PrivateIP2 knows to reach out to PublicIP1 but the responding packets aren't coming back from PublicIP1, they're coming back from PublicIP2 which is the ubuntu server gateway in front of PrivateIP2.  That's not good.  I want the same idea as the first scenario.

Here are my iptables rules on the ubuntu server.  The first two rules let anyone in the PrivateIP2 network out: (everyone is a 192.168.1.* IP including the asterisk server and they all come in on iface p1p1 and leave on iface em1)

```
-t nat -A POSTROUTING -s 192.168.1.0/24 -o em1 -j SNAT --to (PublicIP2)
-A FORWARD -i em1 -o p1p1 -m state --state RELATED,ESTABLISHED -j ACCEPT

```

Those seem to work fine.  Everyone on the inside can get out to the internet.  In fact, I can even make outgoing calls on my asterisk server through its trunk on port 4569 to PublicIP1.

Here are the specific rules for the port forward:

```
IPTABLES -t nat -A PREROUTING -s (PublicIP1) -d (PublicIP2) -p udp --dport 4569 -j DNAT --to-destination (PrivateIP2)
IPTABLES -A FORWARD -s (PublicIP1) -p udp --dport 4569 -j ACCEPT
```

That nat rule should be leaving the source IP address of the incoming packet alone and only changing the destination.  The source should stay as PublicIP1.  For some reason, the packet is being changed before it reaches asterisk#2 to have originated from PublicIP2.

Anyone have any idea what's going on?  This was all going well before I replaced the walmart router in front of asterisk#2 with the ubuntu server.  It's got to be something with my iptable rules.

---

### Post by volkswagner on 2015-04-26
I'm no expert on iptables, but I believe you need some masquerading.

On your Ubuntu/gateway/firewall you need to masquerade your lan pbx, basically renames it/aliases it to your public ip.

I think if you search, "iptables, NAT, asterisk, masquerade" you'll find some help.


I have a standalone server with one public ip and running openVPN for some sip clients + Asterisk on the public interface, I have a postrouting rule for the sip clients
and allow server to run from 10.8.0.1.
```
-A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
```

---

### Post by Doug S on 2015-04-26
> **volkswagner said:**
> I'm no expert on iptables, but I believe you need some masquerading.

On your Ubuntu/gateway/firewall you need to masquerade your lan pbx, basically renames it/aliases it to your public ip.

I think if you search, "iptables, NAT, asterisk, masquerade" you'll find some help.


I have a standalone server with one public ip and running openVPN for some sip clients + Asterisk on the public interface, I have a postrouting rule for the sip clients
and allow server to run from 10.8.0.1.
```
-A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
```He is using SNAT instead of MASQUERADE. He has to [for other reasons]("http://ubuntuforums.org/showthread.php?t=2273650").

Edit: Note that I only use SNAT in my own iptables rule set, but I often test using MASQUERADE instead. SNAT is just a more rigorous form of MASQUERADE, but one does need to know the IP address.

---

### Post by Doug S on 2015-04-26
I can only suggest to be as rigorous as possible and to use all available debug information. You already have tcpdump running on the two asterisk computers, but also put two tcpdump sessions running on your Unubutu server, one monitoring em1 port 4569 and one monitoring p1p1 port 4569. Also monitor the iptables counters, as they are very useful for debugging. Add log statements to your iptables rules for additional debug information.  Further constrain and refine your rules by adding whatever additional conditions you can. Example, change this:```
IPTABLES -A FORWARD -s (PublicIP1) -p udp --dport 4569 -j ACCEPT
```to this:```
IPTABLES -A FORWARD -i em1 -o p1p1 -s (PublicIP1) -p udp --dport 4569 -j ACCEPT
```(I didn't test the suggested new rule).

Edit: Oh, I forgot. You might be able to learn something my monitoring the connection tracking table:```
sudo cat /proc/net/ip_conntrack | grep udp
```(or grep by port number), but note that UDP connections do not persist for very long.

---

### Post by volkswagner on 2015-04-26
Combining info from both threads, I'd suggest sticking with the SNAT, but also create sub network interfaces
for each of the public ip addresses. You might need/want to create a bridged interface for the gateway first then sub interfaces.

You could then have something like this:
```
-A POSTROUTING -s 192.168.5.0/24 -j SNAT --to-source xx.xxx.201.30
-A POSTROUTING -s 192.168.6.0/24 -j SNAT --to-source xx.xxx.201.31
-A POSTROUTING -s 192.168.7.0/24 -j SNAT --to-source xx.xxx.201.32
-A POSTROUTING -s 192.168.8.0/24 -j SNAT --to-source xx.xxx.201.33
```

no?

Again, I'm no expert ;)

---

### Post by fizgig on 2015-04-26
Well, I'd like to stay with SNAT and DNAT as I've read all over the internet they're less CPU-intensive than masquerade.  Also, they should work fine if all IP addresses are known.  As you can see, I have a bit more going on that masquerade might also mess up anyway.

I'm sitting here watching tcpdump in three places and here's what I see in the packet header fields for a packet from Asterisk#1 to Asterisk#2

(On the asterisk#1 server)
From: PrivateIP1
To:     PublicIP2

(on the ubuntu gateway that has PublicIP2)
From: PublicIP1  (This has been changed which is exactly what the walmart router in front of Asterisk#1 server should have done so all good)
To:     PublicIP2  (No change here as expected)

(On the asterisk#2 server)
From: PublicIP2  (This has been changed when it should not have been.  It should still be PublicIP1)
To:     PrivateIP2  (This has been changed by the ubuntu gateway which is what it should have done)

---

### Post by fizgig on 2015-04-26
What I described above was for when asterisk#1 is initiating contact with asterisk#2.  When it's the other way around, it's even weirder.  I decided to run tcpdump on two different interfaces of the ubuntu gateway: em1 which faces the internet and p1p1 which faces the local network asterisk#2 is part of.  I found something interesting.

So, when asterisk#2 tries to make contact with asterisk #1, it generates the following packet according to tcpdump running on the asterisk#2 server:

From: PrivateIP2
To:     PublicIP1

Looks good.  On the interface p1p1 that faces the asterisk#2 system, I see:
From: PrivateIP2
To:     PublicIP1

No change yet which I guess is expected.  All the SNAT and DNAT should occur after the packet arrives on p1p1 and before it is sent out em1.  But, guess what, nothing shows on em1.  Further, nothing shows up on Asterisk#1 tcpdump.  Asterisk#1 never gets the packet.  What I see is that the ubuntu gateway (with PublicIP2) decides to send a couple of packets back to asterisk#2 and have their own odd conversation.  Check out the two attached pictures to see what I mean.

---

### Post by fizgig on 2015-04-27
Thinking about it some more, it seems like each packet being sent from asterisk#2 is being reflected back to it by the ubuntu gateway.  That's why you see 6 packets in that conversation but only 3 packets when asterisk#1 initiates.  Bizarre.

---

### Post by fizgig on 2015-04-27
By adding an "-i em1" to my prerouting rule, I get a clean communication from asterisk#1 to asterisk#2:

```
$IPT -t nat -A PREROUTING -i em1 -s (asterisk#1publicIP) -d (asterisk#2publicIP) -p udp --dport 4569 -j DNAT --to-destination (asterisk#2privateIP)
```

Still trying to figure out the packet reflection when asterisk#2 talks to asterisk#1.  I'm thinking there's a nat conflict of some kind here.

---

### Post by volkswagner on 2015-04-27
NAT can be fun with Asterisk. I haven't run Asterisk without FreePBX, so I'm not certain on specific config files.

Do you have your local networks and public networks configured?

```
localnet=192.168.7.0/255.255.255.0
externhost=xx.xxx.12.102
nat=yes
```

I think the above should be set in both sip.conf and iax.conf. FreePBX adds the configs to sip_general_additional.conf. I don't use iax so
there's no ip info in iax_general_additional.conf on my system.

---

### Post by fizgig on 2015-04-27
Well, I'm not sure asterisk has anything to do with it.  The packet leaves the asterisk computer and is bounced back by the firewall with both the sender and receiver address changed.  I can see that change occuring at the firewall - outside the control of asterisk which is on another computer.

Anyhow, I have a workaround going that I think might get me to the finish line.  I use port 4569 going from Asterisk#1 to Asterisk#2 and 4570 when going the reverse way.   In this manner, there doesn't seem to be any confusion and the packets reach the other side ok no matter which direction we're talking abuout.  I don't like this because I shouldn't have to do this but I'll go with it for now while I keep researching it.

Basically, I think there is a conflict between the prerouting and postrouting nat rules.  They seem to be incompatible.  Obviously, you should be able to port forward to a host inside a nat'd network (any commercial router I've used can do that) but I just can't do so with iptables.

---

