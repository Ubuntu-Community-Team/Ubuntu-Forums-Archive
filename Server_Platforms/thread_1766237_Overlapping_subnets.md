---
title: "Overlapping subnets"
date: 2011-05-24
forum: Server Platforms
---

### Post by tapi0n on 2011-05-24
I'm setting up a nagios monitoring system. Most of the hosts I got to monitor are on private networks. 

When they set up these networks they didn't take into account the fact that some of them (the older networks) were overlapping. Now since there are like 3-4 networks which overlap I can't just add them to a routing table.

This is how I worked so far. Using management-pptp package to create the vpn. Activate the vpn (pon) and then

```
route add -net ....
```

to get to the private network behind the firwall/router.

Now this works fine for the networks which don't overlap and for one of the overlapping networks. But obviously when adding two different networks which have the same subnet this won't work.

I was wondering if there are any alternatives?

Someone mentioned port forwarding on the firewall. But I don't quite know how that would work (kind of new to all of these things).

Anyway, any help would be appreciated.

Cheers,

---

### Post by spynappels on 2011-05-24
Not much help to you I'm afraid, but it seems unfair of the course administrators to set a task which is made unecessarily difficult by the network, unless the idea is to test your problem solving skills directly.

Get them to look up Variable Length Subnet Masking to avoid wasting space and overlapping subnets.

Just a thought, could you initiate a tunnelled peer to peer connection between the (problem) remote hosts and the Nagios machine?

---

### Post by tapi0n on 2011-05-24
Well it's like this. The last couple of months of my education (don't know the correct word for it) we are required to do an internship at an external company. So the person above me is actually the head of sysadmins over at this company. I already suggested changing those few networks so that they wouldn't have this problem. But seeing how those networks are actual customers you can't just go and start changing things, because it will have an effect on actual people and their job. Things like these require them to set up contracts and what not (out of the scope of my knowledge).

They know this problem excists but they realised too late. Which to be honost is quite a big flaw.


> Just a thought, could you initiate a tunnelled peer to peer connection  between the (problem) remote hosts and the Nagios machine?     At the moment I'm monitoring a 192.168.x.x network with nagios (which is working like it's supposed to). To monitor this network I put up a vpn on xxx.xxx.xxx.xxx, being the external (provided by the ISP) IP.

Now the second network which requires monitoring is also on a 192.168.x.x network (with the same netmask). I set up a vpn with the firewall/router and I'm able to ping to the internal IP of that host. At least I think it's that host because when dissabling the vpn I'm no longer able to ping the same IP. But I can't ping any of the hosts behind that (with vpn up).

I  hope this was a relevant answer to your question?

---

### Post by spynappels on 2011-05-24
Can you just tell me what the subnet mask in question is? I'm sure you know your subnetting, but if the address is 192.168.x.x/24 (subnet mask 255.255.255.0) the third octet is also important, so 192.168.1.x/24 is different to 192.168.2.x/24.

Or is the subnet mask different? (Much bigger problems if it is) Or is the third octet the same for both subnets?

I'm sorry, but I'm not familiar with pptp VPNs, I use OpenVPN. I just want to understand the topology before doing anything else.

You certainly seem to be learning a ton of stuff on the forums though, and practice makes perfect.

EDIT: A diagram of the topologies may help if you can get one.

---

### Post by tapi0n on 2011-05-24
They're both on a 192.168.0.x network with a subnetmask of 255.255.255.0 .

Seeing how I'm not allowed (company polecy) to make stuff like the topology public I'll just try to sketch it.


this is the first network (this is the network I'm succesfully monitoring)

```

Firewall 192.168.0.9
         |
         |__ ESXi server 192.168.0.249
         |              |
         |              |__ Windows Server 192.168.0.250
         |              |
         |              |__ Windows Server 192.168.0.251
         |
         |__ Some other host which is not yet installed at the site (so no ip yet)

```

this is the second network

```

Firewall 192.168.0.2
         |
         |__Windows server 192.168.0.5
         |
         |__ Windows server 192.168.0.6
         |
         |__ Linux server 192.168.0.20
         

```

I know it's not much but it's the  best I could do with my keyboardskills.

---

### Post by spynappels on 2011-05-24
Ok, I get it now, sorry had a brain freeze. The remote LANs both have the same subnet and you need to monitor hosts on both LANs.

Got it.

Hmmm, is it possible to create individual VPN tunnels from each host to be monitored back to your own LAN and use the VPN IPs to communicate with the monitored hosts? this is exactly how I overcome the same issue, monitoring multiple servers on a variety of different (separate) subnets. I could give you a walkthrough using OpenVPN, but you are using pptp, right?

---

### Post by tapi0n on 2011-05-24
Yes I am using pptp since that is already being used.

Anyway, I do understand where you are comming from with the individual vpns, but how could that be achieved? You can't set up a vpn using a private ip can you? 

Or do you mean start the tunnel on the host side and make the nagios server operate as vpn server?

---

### Post by spynappels on 2011-05-24
We have a VPN server in our infrastructure, which all our remote servers connect to by default for our remote admin. So all of our remote servers have a LAN IP, set by their local environment, and a tun0 IP, handed out by our VPN server. I have the routing set up so my Nagios box, which is also set up as a VPN client, can connect to  all our remote boxes using their VPN IP.

I'll try to sketch it:

**Internal Infrastructure**

VPN Server + Router (LAN:192,168.1.1, VPN:10.18.0.1)
    |
    |
    |------Nagios Server (LAN:192.168.1.x, VPN:10.18.0.5)
    |
    |
Rest of LAN




**Remote subnet 1**

Router
   |
   |---- Remote Server 1 (LAN:192.168.1.50, VPN:10.18.0.9)
   |
Rest of LAN


**Remote Subnet X**

Router
   |
   |---- Remote Server X (LAN:192.168.1.50, VPN:10.18.0.Y)
   |
Rest of LAN

So the Nagios server polls all the remote machines using their VPN IPs (10.18.0.x/24 subnet)

Does that make sense?

---

### Post by tapi0n on 2011-05-24
It does make sense. I mean I follow you in what you're saying. 

I do however have no idea how I would implement this in this infrastructure. I'll suggest this to my mentor tomorrow (I hope he's comming in tomorrow) and see what he thinks about it.

So I'm just gonna summ up to see if I'm getting it right.

The vpn server on 'my side' should hand out IP's (including an ip for my nagios box) to every host I wish to monitor. I'm assuming the original vpn should still exist to achieve that? After configuring that, Nagios should be monitoring on the IP addresses provided by the vpn server, and not the addresses on the local network.

So this would mean I would (the addresses are from your examples) change an existing nagios host from
```

define host {
...
address 192.168.1.50
...
}
```

to

```

define host {
...
address 10.18.0.9
...
}

```

---

### Post by Grenage on 2011-05-24
How many servers are there per network, many?  What would stop you from adding routes per server?  I've not had to do it myself.

This obviously would not work if the two servers had the same private IP.

---

### Post by tapi0n on 2011-05-24
> **Grenage said:**
> How many servers are there per network, many?  What would stop you from adding routes per server?  I've not had to do it myself.

This obviously would not work if the two servers had the same private IP.


I could do that actually, just for the 'presentation' of it all. And mention on a side note I did it like that because of the fact they didn't distribute ip ranges correctly. I actually didn't think of that.

But in the end it would be quite a sloppy thing and not really a flexible set up. But still I can't help it if they didn't think decently about their installation.

---

### Post by Grenage on 2011-05-24
> **tapi0n said:**
> I could do that actually, just for the 'presentation' of it all. And mention on a side note I did it like that because of the fact they didn't distribute ip ranges correctly. I actually didn't think of that.

But in the end it would be quite a sloppy thing and not really a flexible set up. But still I can't help it if they didn't think decently about their installation.

It would be a horrendous hack, but it should work.  How does the company currently manage communication with the other sites, or is this the first instance?

---

### Post by tapi0n on 2011-05-24
They make a tunnel and connect to the servers with rdcp. 

Why would that be considered a hack?

---

### Post by Grenage on 2011-05-24
> **tapi0n said:**
> They make a tunnel and connect to the servers with rdcp. 

Why would that be considered a hack?

Gotcha.  Hack might be the wrong word, but it's not an elegant workaround.  Desperate times, and all that!

---

### Post by spynappels on 2011-05-24
> **Grenage said:**
> How many servers are there per network, many?  What would stop you from adding routes per server?  I've not had to do it myself.

This obviously would not work if the two servers had the same private IP.

I guess that is why I did not do it that way then, most of my servers are set up to use 192.168.1.50 on their local LAN! Just from an ease of deployment point of view and because while we do not control the remote subnets, most use the default subnet in their ADSL or cable routers, which is generally 192.168.1.0/24

That way also does not scale well past the stage where you have to have a routing tables with more than one page! But for the purposes of your assignment, it may be the better option.

---

### Post by tapi0n on 2011-05-24
Well ok cheers for the input guys,  I'll do some tinkering with both ideas tomorrow and see which one works. Gonna try  spynappels' idea first because of the elegancy of it all. And if that doesn't work I guess I'll have to talk to my mentor.

---

