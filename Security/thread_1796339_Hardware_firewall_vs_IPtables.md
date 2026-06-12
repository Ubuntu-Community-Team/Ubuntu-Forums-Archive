---
title: "Hardware firewall vs IPtables"
date: 2011-07-03
forum: Security
---

### Post by Dry Lips on 2011-07-03
So I'm about to set up my own webserver at home. I do already have a host that I'll use for my site, but I've figured out that I also want my own server for development work, etc. Since it'll be open to the internet, I need to figure out what kind of firewall I need.
 

 Now, my router (jensen airlink 89300v3) already has a firewall:
  It is able to block some common hacker attacks (Ping of death, discard ping from WAN, port scan, sync flood); it supports port forwarding and DMZ.  
 

 Would the hardware firewall be good enough, or should I set up a DMZ and let iptables do the job? And is it possible to use both at the same time, in other words combine the router firewall with for instance iptables?

---

### Post by Dangertux on 2011-07-03
The first thing I would consider is not opening a development server to the entire Internet, at least not on a permanent basis. 

However if you choose to do that then you could use the two options in conjunction with eachother. You can forward only the ports you want then further filter them using iptables. 

Iptables will give you a much more robust feature set then a NAT firewall alone. Especially if you start getting into addons like xtables. Honestly though if it's a dedicated machine and is expecting any type of considerable traffic I would recommend dmz'ing the machine. Most home routers have issues with forwarding a large number of concurrent connections. 

Truth of the matter since you're running a server the minimal amount of protection given by port forwarding  will be negligible.

---

### Post by Dry Lips on 2011-07-03
Perhaps I was a bit unclear. Actually I've got two servers, one of them would be the offline development server. I want to use the other one for collaborative internet work, as well as a backup solution for my main hosted site. So it won't draw much traffic; that is, *unless* my host becomes unavailable and I need to use my own server.   

> Most home routers have issues with forwarding a large number of concurrent connections.  Your advice about port-forwarding is perhaps what tips the scales in favour of DMZ/iptables. If I ever should need to use my server for stuff that would draw more traffic, I guess it would be a great advantage to have DMZ/iptables set up beforehand.
 

 Thanks for your help mate! :)

---

### Post by doas777 on 2011-07-03
My advice is a little different.

For DMZ machines, your best bet is server-hardening, rather than firewalling (though the firewall does play an important role in protecting from IPStack attacks like malformed pings).

Generally the first step in hardening an DMZ machine, is to remove any services that are not required for public access. 

so, in light of the fact that you wish to develop on the machine (presumably exposing internal-only services) i recommend that you forward ports for the specific external services you wish to render, in addition to using iptab/ufw to allow internal services only to the lan network. you will experience a performance hit, but it should be negligible unless you are dealing with serious amounts of traffic. if you really have that many concurrent connections, then getting a second server for internal development is really your best bet anyway. if you have a home router/residential internet connection, your isp will probably complain before you have any problem with the router.

DMZ plays an important role, but it is all-or-nothing. if you want a-little-of-each, then forwarding is the way to go.

---

### Post by Dangertux on 2011-07-03
Now I am kind of confused is there only one machine that will be publicly accessible or 2?

In either case I only partially agree on what the above post says. IMO a lot can be accomplished through creative use of iptables. 

In terms of security benefits the obvious advantage of port forwarding would be that if a compromise were to for instance create a shell it would be much more difficult if there was a NAT device in front of the server, if not impossible. 

Also server hardening is absolutely not optional even with a firewall. If my original post implied that then I was conveying a very wrong message. As the above poster stated server hardening is your bread and butter. The reason being most exploits that will be anything other then a simple denial of service will capitalize on a flaw in the exposed applications. The primary concern is patching known vulnerabilities, and keeping on top of that. The second area of concern is reducing the attack surface which is done through a combination of removing unneeded public services and filtering. IE : filtering requests to public services based on ip/host information through iptables as well as through the services configuration itself. Redundancy can be very useful in this case.  Which is why ultimately depending on your needs port forwarding may still work for you, as it would add a third layer of protecion. However, balance is always needed it is up to you to determine where that balance comes in.

---

### Post by Dry Lips on 2011-07-03
> **Dangertux said:**
> Now I am kind of confused is there only one machine that will be publicly accessible or 2?
> **doas777 said:**
> if you really have that many concurrent  connections, then getting a second server for internal development is  really your best bet anyway. 
 
There'll be only one machine accessible to the outside! Sorry if I was unclear. The development I was talking about is the collaborative stuff. (Which I'll password protect) The other server will handle internal development.

> **doas777 said:**
> 
Generally the first step in hardening an DMZ machine, is to remove any services that are not required for public access.
> **Dangertux said:**
>  The second area of concern is reducing the attack surface which is done  through a combination of removing unneeded public services and  filtering. Could you be more specific? What kind of services are you referring to? Primarily I will have LAMP/SSH installed. At first I thought about having a mail server as well, but I know it'll complicate the whole thing a lot, so I think I'll skip that. But there aren't other ports besides 80/22 that will be open with LAMP/SSH, right?
(For the record: Of course I'll use keys with SSH)

> **doas777 said:**
> i recommend that you forward ports for the specific external services  you wish to render, in addition to using iptab/ufw to allow internal  services only to the lan network.
Well, say you only forward port 80... Would you then need any rules for port 22?
Wouldn't traffic on this port be restricted to the lan by default?

> **doas777 said:**
> 
if you have a home router/residential internet connection, your isp will probably complain before you have any problem with the router.
I've already had a chat with my ISP, and luckily this won't be a problem. (Fibre lines, overcapacity! :)) But hopefully traffic will be minimal anyway.

> **Dangertux said:**
> Also server hardening is absolutely not optional even with a firewall.  If my original post implied that then I was conveying a very wrong  message.
I didn't read your post that way. Server hardening is something I'm researching.

**Dangertux & Doas777**:
Thanks a lot guys!

---

### Post by Dangertux on 2011-07-03
There is a lot that goes into hardening a server. I am on my phone at the moment but when I get back around to my computer I will put up some more info.

---

### Post by psusi on 2011-07-03
Wow, ping of death?  I've not heard that one in a long time.  Nobody has given it any thought since they fixed that Windows bug like 10 years ago.  It was pretty fun though for about a month or two there.

---

### Post by Dry Lips on 2011-07-04
> **psusi said:**
> Wow, ping of death?  I've not heard that one in a long time.  Nobody has given it any thought since they fixed that Windows bug like 10 years ago.  It was pretty fun though for about a month or two there.

I didn't know that... But the router still blocks it! :)

---

