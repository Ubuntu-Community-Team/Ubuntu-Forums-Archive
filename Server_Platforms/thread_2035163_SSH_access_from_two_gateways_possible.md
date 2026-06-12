---
title: "SSH access from two gateways possible?"
date: 2012-07-30
forum: Server Platforms
---

### Post by continuous on 2012-07-30
I would like to access my server externally over ssh using a second gateway on our internal private c class network. 

Using the default gateway, the server  is reachable from outside over SSH ok but then using SSH to the other gateway I get no response.

I have port forwards on each firewall and ssh works on either gateway when that gateway is the default for the server. 

What I want is to be able to reach the server from either gateway regardless of which is the default. 

Can this be done? (If so, how?)

I have tried having sshd listen on two different ports and port forwarded each gateway to one of the two ports, but that doesn't work either.
What is curious (which means I don't understand SSH) is that any internal IP can SSH to the server fine?? Why - where does it say that only one external address can get to the sshd and all the internal private c class addresses, but none other?

I haven't touched iptables or anything like that - i.e default configs here.

My sshd_config allows access from anywhere : 0.0.0.0

# What ports, IPs and protocols we listen for
Port 22
Port 12222
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
ListenAddress 0.0.0.0

Cheers, and thanks!

---

### Post by continuous on 2012-07-30
Not getting much joy...perhaps I need to move this to networks? (Moderators - please help)

---

### Post by BkkBonanza on 2012-07-30
I doubt ssh is the problem. More likely you have routing issues getting from one place to the other and it's not really clear exactly what your setup is. I'd look at your routing tables and try to figure out the path from one to the other. 

**route -n** will show where your login attempts should be directed. You may need to add a route on one gateway to ensure you cross to the correct network rather than getting sent out to the internet.

Also the mtr command can give you some real time view of pathways. Though not installed by default it's easy to get.

sudo apt-get install mtr
mtr -t ssh_server_ip

If that doesn't help then try to paint a more exact picture here of what is connected to what and IPs they have. Output of the route -n on various machines also helps. If one machine isn't the default gateway it may need some kind of static route to be reachable.

---

### Post by continuous on 2012-07-30
Thanks for the help - from your pointers, I may have worked out a solution, but I am not at all confident in it at all.

First, here is the current route table as requested.

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
0.0.0.0         192.168.100.1   0.0.0.0         UG    0      0        0 eth0

And second here is an attempt to clarify my network a little:

[LIST]
[*]The private network is 192.168.100.0/24 and the server address is 192.168.100.2
[*]One gateway (Firewall(a) -> ADSL(a) -> Internet) is 192.168.100.1
[*]The other gateway (Firewall(b)->ADSL(b)->Internet) is 192.168.100.254
[*]Port forwards are setup on each firewall to forward port 12222 from anywhere to port 22 on 192.168.100.2 - the server.
[/LIST]
Here is what happens:

[LIST]
[*]I can access the server via ssh from any internal machine with an ip address in the private network regardless of the servers gateway address.
[*] I can access the server using ssh from outside via the ADSL gateway firewalls providing the server is configured for that gateway. All external ssh attempts from the other gateway fail.
[/LIST]
So it seems to me that setting the gateway address limits SSH to respond to external connections providing they come via the configured gateway address.

It occurs to me that the culprit may be the servers netmask set in interfaces. Should I set that to be 0.0.0.0 instead? Here is my current /etc/network/interfaces:[INDENT]allow-hotplug eth0
auto eth0
iface eth0 inet static
address 192.168.100.2
** netmask 255.255.255.0**
#gateway 192.168.100.254
gateway 192.168.100.1
[/INDENT]and I am proposing to change it to:[INDENT]allow-hotplug eth0
auto eth0
iface eth0 inet static
address 192.168.100.2
** netmask 0.0.0.0**
#gateway 192.168.100.254
gateway 192.168.100.1
[/INDENT](I can't afford to just "try" this as the server is a long way away and hard to get to if I lose SSH connectivity).

Cheers, and thanks again.

---

### Post by BkkBonanza on 2012-07-30
I wouldn't change that netmask. I'm pretty sure that's not the issue.
Your problem is likely the return route.

You can send packets in thru the second gateway but when ssh responds the current routing will send them back via the default gateway not the gateway they came in. So they will appear to come from another IP at your external location and be dropped (no NAT record exists).

You can likely fix this with some iptables entries on the server. I'd have to think more about what to put there but something that makes sure packets go back the route they came from. Or there may be some better way but I'd don't have it off the top of my head. Research req'd.

...
One way might be to use different ports on each route, and then add a filter entry in iptables that directs traffic depending on port.

Regarding being far away you should probably make a cron job that restores default files that work every 5 minutes. That way if you alter something and it doesn't work then the cron will reset things to a working state. So you'd have 5 minutes for each dangerous config trial.

---

### Post by miegiel on 2012-07-30
Assuming your firewall is a linux machine with iptables, you need 1 rule to forward the port and 1 rule to allow it through the filter.

In the *nat* table of the firewall you'll need a rule like:
```
-A PREROUTING -i eth1 -p tcp -m tcp --dport 12222 -j DNAT --to-destination 192.168.100.2:22 
```
And in the *filter* table of the firewall you'll need a rule like:
```
-A FORWARD -d 192.168.100.2/32 -i eth1 ! -o eth1 -p tcp -m tcp --dport 22 -m conntrack --ctstate NEW -j ACCEPT
```
Where *eth1* is the internet interface. And keep in mind that incoming address/port translations (NAT) happen before the filtering.

---

### Post by The Cog on 2012-07-30
I suspect that the issue is that you are using NAT. When a call comes in from the internet, the router handling that call has to set up a translation entry, converting between the public address that it is forwarding (e.g. 1.2.3.4:22<->192.168.100.2:22). This router knows that the reply packets from 192.168.100.2 must be re-written to appear to come from the public address. Now, if the default gateway for the internal server is a different router, that other router will knwo nothing about the required address translation for the reverse trip.

---

### Post by BkkBonanza on 2012-07-30
> **The Cog said:**
> I suspect that the issue is that you are using NAT. When a call comes in from the internet, the router handling that call has to set up a translation entry, converting between the public address that it is forwarding (e.g. 1.2.3.4:22<->192.168.100.2:22). This router knows that the reply packets from 192.168.100.2 must be re-written to appear to come from the public address. Now, if the default gateway for the internal server is a different router, that other router will knwo nothing about the required address translation for the reverse trip.
You have the right general idea but not quite. On the way in gateway2 doesn't do NAT. Only on the way out. 

But the server is sending packets out gateway1 (default route) not gateway2 even though it originated from gateway2. So any return packets appear to be coming from a different IP when they get to the outside destination. The router where he's accessing from is doing NAT and when it sees a reply from a different source IP than what was sent out (by ssh) it doesn't know who its for. So it drops it as junk data.

Adding some iptables rules on the server itself could likely fix it up so it doesn't use a single default route but feeds packets to where they came from. One thing is on each gateway you could mark the packets to indicate where they came from and then filter on the server using the marks to get them back properly. Or something. I figured using different ports would be easy to filter on.

---

### Post by continuous on 2012-07-30
> **BkkBonanza said:**
> I wouldn't change that netmask. I'm pretty sure that's not the issue.
Your problem is likely the return route.

You can send packets in thru the second gateway but when ssh responds the current routing will send them back via the default gateway not the gateway they came in. So they will appear to come from another IP at your external location and be dropped (no NAT record exists).

You can likely fix this with some iptables entries on the server. I'd have to think more about what to put there but something that makes sure packets go back the route they came from. Or there may be some better way but I'd don't have it off the top of my head. Research req'd.

...
One way might be to use different ports on each route, and then add a filter entry in iptables that directs traffic depending on port.

Regarding being far away you should probably make a cron job that restores default files that work every 5 minutes. That way if you alter something and it doesn't work then the cron will reset things to a working state. So you'd have 5 minutes for each dangerous config trial.

Oh! that is excellent! I am getting my head around this - I wasn't considering that ssh is a two way street!

---

### Post by continuous on 2012-07-30
Yes, thanks - I am not sure how to go about redirecting so the two way packet stream ends up in the right gateway, but I get it!!! **Thanks all for pitching in**!!!
I'm a bit slow in the take up sometimes, so I need to mull it over and understand the flow clearly, then come up with a solution to suit the setup. 
I will use cron to restore a working config too - that is an excellent idea and one that I hadn't considered.  
I'll post back what I do....but I may be back for more help. Again thanks - I'm so grateful to you all.

---

### Post by BkkBonanza on 2012-07-30
See here for nice elegant solution,

[http://unix.stackexchange.com/questions/4420/reply-on-same-interface-as-incoming](http://unix.stackexchange.com/questions/4420/reply-on-same-interface-as-incoming)

Something like this, (assuming default route is on eth0 as above),

```

echo 200 isp2 >> /etc/iproute2/rt_tables
ip rule add from <eth1_ip> dev eth1 table isp2
ip route add default via <other_gateway_IP> dev eth1 table isp2

```
(substituting your values for <eth1_ip> and <other_gateway_ip> above)

Some docs here,
[http://linux-ip.net/html/routing-tables.html](http://linux-ip.net/html/routing-tables.html)

Here's what this does, in English,
1. create a new routing table called isp2
2. if a packet is from the IP assigned to eth1 (because it came in on that IP) then send it to isp2 routing table (ie. not the main routing table)
3. add a default route on isp2 table that goes to here via eth1

Pretty nice, I hope it works...

If it does then add it to the interfaces file as post-up commands so it gets added when eth1 is brought up. 

edit: You don't want to run the echo command more than once. Only to setup the table initially.

---

### Post by The Cog on 2012-07-30
I think you will have to settle on one gateway or the other. Asymmetric routing is the problem - you need to have both traffic directions of the same conversation going through the same gateway so the NAT can operate on both directions.

If your ssh client shows up with the same IP address to the server then this could be difficult to arrange.

---

### Post by redmk2 on 2012-07-30
Admittedly I've only skimmed this thread, but I believe [**_[COLOR="DarkSlateGray"]this solution[/COLOR]_**]("http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/") could help the understanding of the problem

---

