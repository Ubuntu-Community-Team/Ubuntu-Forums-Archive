---
title: "Need help with routing"
date: 2015-05-06
forum: Server Platforms
---

### Post by amalgamas on 2015-05-06
I have two lans: lan1 (10.xxx.xxx.xxx) and lan2 (192.xxx.xxx.xxx)
lan1 is our work network, [COLOR=#000000]connected to a larger separate, secure network and the gateway is provided by this network (10.xxx.xxx.1)[/COLOR].  Lan2 is connected to the internet.
I have a ubuntuserver with two NICs (lan1 and lan2) and on the work PCs in lan1 we access the internet via this server in terminal windows. The ubuntuserver uses only the gateway for lan2 (192.xxx.xxx.1)
On lan2 there is a NAS-disk with a mediaserver.  It has only one NIC attached to lan2. We would like to establish a connection from the PC-s in lan1 to this mediaserver, routed through the ubuntuserver with two NICS.
I have googled and tried some suggestions already, but being a noob this is over my competence level.  Can anyone help or should I buy a new NAS with two NICs?

---

### Post by darkod on 2015-05-06
What serves as gateway for lan1? The ubuntu server?

---

### Post by amalgamas on 2015-05-06
Our lan1 is connected to a larger separate, secure network and the gateway is provided by this network (10.xxx.xxx.1).  Sorry for the incorrectness in my first entry.  I will edit now

---

### Post by darkod on 2015-05-06
Lets see then... from the top of my head.
You will have to enable packet forwarding on the ubuntu machine and then set a static route on 10.x.x.1 that will send all traffic for the nas 192.x address through the ubuntu's 10.x address.
Also you could set static route on each client on lan1, maybe by dhcp option. That way you don't need to make changes on the gw, each client will know to send the traffic destined for the nas to the ubuntu.
Once the traffic gets there, because ubuntu is in the lan2 also, it will know what to do with it.

---

### Post by amalgamas on 2015-05-06
Thank you for yourprompt answer!


As I said: I am notvery savvy at this.  However I think I will have to stick to thefirst option.  I don't want to touch the PCs on lan1. They arewindows Pcs which I know even less about and there are these securityconcerns.


I need ratherexplicit instructions to how to enable packet forwarding in aubuntuserver (can be googled, I guess), then how to set a staticroute.  As I said we need a route only to the NAS


Best regards

---

### Post by darkod on 2015-05-06
The 10.x.x.1 gw, is it a standalone router/gateway device or a computer configured to do routing?

The ubuntu box is in private networks (both lan1 and lan2 are private). Are you using any firewall on it? Like iptables for example?  If there is a firewall it can interfere with the routing. I can send you instructions for the ubuntu box once you let me know if you are already using iptables and when I get home...

---

### Post by The Cog on 2015-05-06
To save changing all the routing on net 10, it should be possible to configure the Ubuntu server to forward all the relevant NAS port numbers to the NAS, such that users on net 10 only talk to the Ubuntu server address. They treat the Ubuntu box as the NAS. This assumes the NAS uses different ports to the Ubuntu server.

So if your Ubuntu server is 10.1.2.3 and the NAS is 192.168.9.9, something like this in iptables would forward port 80 to the NAS:
```
sudo iptables -t nat -A PREROUTING -d 10.1.2.3 -p tcp --dport 80 -j DNAT --to-destination 192.168.9.9
```

The NAS still has to know the route back to net 10 via the 192.168 address of the Ubuntu server, 
The Ubuntu server still has to have ip forwarding enabled, [http://askubuntu.com/questions/311053/how-to-make-ip-forwarding-permanent](http://askubuntu.com/questions/311053/how-to-make-ip-forwarding-permanent)
The above iptables rule has to fit in with whatever other firewall rules you have in place, which could be tricky to configure depending on how the existing rules were configured.

EDIT
Corrected above command which erroneously tried to use the mangle table instead of the nat table

---

### Post by SeijiSensei on 2015-05-06
Some basics:
1) Edit as root with sudo the file /etc/sysctl.conf and remove the hash mark at the beginning of the line
```
#net.ipv4.ip_forward=1
```
That enables packets to be forwarded across network interfaces.  Forwarding is disabled by default for security reasons.

2) That will work upon reboot.  For now you can accomplish the same result with the command:
```
sudo echo '1' > /proc/sys/net/ipv4/ip_forward
```

3)  Check the machine's routing table with the command "route -n".  It should have a routes for 10.x and 192.168.x via the appropriate interfaces.  It should also have a route for 0.0.0.0 which points the gateway.  Something like this:
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.x.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
10.x.y.0        0.0.0.0         255.255.255.0   UG    0      0        0 eth0
0.0.0.0         10.x.y.1        0.0.0.0         UG    0      0        0 eth0

```
The mask for the 10 network may be different depending on how it is subnetted.  For instance, the network 10.1.0.0 will have a 255.255.0.0 network mask.

With forwarding enabled and routing correct, see if you can ping machines in one subnet from the other and vice versa.

---

### Post by amalgamas on 2015-05-06
To** The Cog:**
This gave the following response: > iptables: Invalid argument. Run `dmesg' for more information. Last line in dmesg: > x_tables: ip_tables: DNAT target: only valid in nat table, not mangle

To **SeijiSensei**:
I activated packet forwarding by removing the hash mark and reboot the ubuntuserver.  Tried to ping from 10.xxx network to ubuntuserver address 10.xxx  but this did not work. I checked route -n and got a similar table but in another order.

---

### Post by darkod on 2015-05-06
How you decide to do it, is your choice. But I still support a simple static route as best option.

The suggestion by The Cog will work (maybe slightly modified), but you need rules for every port you need to pass through, and you also need to watch out which ports and services you will have active on the ubuntu box and on the nas box (if any). Also, if you decide to change a standard port with a non-standard one, the client will have to take this into account when doing the connection. IMHO, too much administration as opposed to a simple static route.

I asked you if you are using a firewall or iptables on the ubuntu box to be sure the commands I give will not mess it up. Usually a box on internal network has no need of firewall, but some people do have it.

@Sensei, enabling routing on the ubuntu box will not make ping available between lan1 and lan2 simply because that box is not the GW of lan1. And he doesn't want to use it as GW. The GW is a separate device. So by enabling the routing my idea was to make the static route possible, and it will be used only for traffic to the nas, as he wants it to be. In all other cases the default GW stays the same.

Also, apart from the ip_forward enabling, doesn't he need a MASQUERADE too? Only ip_forward does not make routing possible because return traffic can't get through. Right?

---

### Post by The Cog on 2015-05-06
I have corrected my port forwarding command posted above. My bad.

I agree with darkod that if you can get whoever "owns" the corporate router to add a static route for your NAS, this might be easier than using port forwarding on the Ubuntu box. 
Whether you use port forwarding or a static route, you will probably have to modify your firewall rules to allow the NAS traffic through.

@darkod: You are right about the need to worry about routing the return traffic. A static route in the NAS box or on the internet router would be one solution. Configuring NAT masquerade on the Ubuntu server's internet interface would be another way.

---

### Post by SeijiSensei on 2015-05-06
I vote for adding the route to the gateway as well.  It's really the best solution.  Otherwise you'd have to make the Ubuntu box be the LAN clients' default gateway by changing the DHCP server settings.  Then you can manage the internal routing on the Ubuntu box and just hand off outbound traffic to the upstream router.  I don't think you'd need masquerading with such a configuration either.

---

### Post by MAFoElffen on 2015-05-07
My suggestion? Draw out a basic topology so all are talking about the same thing... Because from my perspective, if using ICMP... a router is a path from one subnet to another. A gateway is just an IP that connects to that router path the outside of that subnet, That router path could be outside to another subnet or outside from intranet to internet. (most commonly the default path to the outside world...)

So if: 
```

OutsideWorld <-- gateway (10.0.0.1) <--+--> NetID 10.0.0.0 <-- (10.0.0.2)  ( Router path to a subnet (192.169.0.1) --> 192.168.0.0 NetID

```
And either router-rip to let the nets/subnet see the other sides of the jumps see each other, a preferred hop list or a static path. Cause if you port forward straight from 192.168.0.1 to 10.0.0.1, then anything on NID 192.168.0.0 cannot see anything on NID 10.0.0.0... right? (It will go straight out through 10.0.0.1?)

But you know that you could have subneted the heck out of your 10.x.x.x x class "A" private network right? (such as a NetId of the next subnet as 10.1.x.x). Then again, you would need to understand how to subnet, use subnet masks and assign IP's from those subnets.

---

### Post by 1clue on 2015-05-07
I have several questions and some concerns regarding the nature of these networks:
[LIST=1]
[*]Ubuntu Server is part of lan1 or lan2?
[*]Are these lans on the same physical site?  In other words, is this pipe traveling over the Internet?
[*]You keep saying 'secure' with respect to lan1.
[LIST=1]
[*]Does the owner of lan1 know you're doing this?
[*]How big is lan1?
[*]If this is a corporate network, you may have huge security concerns.
[*]I deal with large companies and security policies, doing this sort of thing without the proper cooperation from the powers that be could lead not only to loss of employment, but also to legal action and/or loss of certifications for the corporation.
[*]If these lans are hooked through a non-secure network then I would strongly recommend a VPN.  And coordination with the manager of lan1.
[/LIST]
[/LIST]

I'm not trying to rain on your parade, but there are some inconsistencies in the discussion.  It's best to get those ironed out.

For example, you said lan1 has the gateway but your diagram shows lan2 has the gateway.

---

### Post by The Cog on 2015-05-08
I agree 1clue about "secure". If you connect the corporate network to the internet without the agreement of the folk who own/operate the network, you could find yourself in big trouble when they find out. It could be a big security risk, and companies take that very seriously these days.

---

