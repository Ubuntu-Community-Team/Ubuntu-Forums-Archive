---
title: "IP addresses (IntRAnet Vs IntERnet)"
date: 2008-09-12
forum: The Cafe
---

### Post by serpentine_bull on 2008-09-12
So, I've been poking around with my home network, setting up DNLA servers to stream video to the PS3, putting 3rd party firmware on the good ol' wrt54g, etc, etc, and as I was assigning static IP's to some stuff, I noticed that the whole network had the subnet mask of (192.168.1). 

I figure that range of 255 IPs was reserved by linksys so as to make those 255 (or less) nodes only viewable to computers on the same network (IntRAnet, I think it's called.)

Also, each computer has a different IP address reported when some test is run on the internet. I figure there that each computer (or node) has a public IP as well as a private IP, and that 192.168.1.x is on the 'blacklist' of public IPs, like nodes on the intERnet can't be assigned those IPs, since it would confuse computers looking to vnc or ssh into nodes on their own intRAnets.

This brings up a question for me, how do you access computers on your home network (intranet) while outside of it (internet)?

Or, am I mistaken on the fundamentals of networking?

---

### Post by revleo on 2008-09-12
you are mistaken and not  it gets complicated and you have to do some binary and or bit math to make it work but you came close when you brought up "public" & "private" addressing i would explain but that part of the cisco curriculim always gave me a headache for the public part you don,t just have one addy but several like your gate way and your subnet mask in modes of 
class A
class B
class C 

and then it gets interesting cause it all changes as we switch over to the new IPV6 protocols and get into hexadecimal addressing

---

### Post by JetskiDude911 on 2008-09-12
If I need to access my computers at home remotely, I'll either create a rule in my firewall, or just establish a VPN connection. I haven't done this in a long time seeing as my only computer is now a laptop that I take with me everywhere.

---

### Post by revleo on 2008-09-12
192.168.1.1. and its brother addys like 127.0.0.1 are private addy speak for home address

---

### Post by doas777 on 2008-09-12
ok heres the way it works.
IP addresses are 4bytes long (32bit). each of the numbers separated by .s are each 1 byte. so the ipaddress range is from 0.0.0.0 - 255.255.255.255.

there are lots of symbolic constants in this address range however. not every address is available for use. some of these constants take the form of private IP address ranges. 

the 3 private ranges are:
10.0.0.0 - 10.255.255.255 (class A net: 16,7777,216 (2^24) hosts),
172.16.0.0 - 172.16.255.255 (class b net: 65535 hosts (2^16) hosts),
and 192.168.0.0 - 192.168.255.255 (255 class C nets with 255 hosts each).

these ranges are defined in [RFC1918]("http://www.faqs.org/rfcs/rfc1918.html")

ok. in terms of routing in and out of a private network, you use a technology called NAT (or PAT). basically you only have one IP address, but every connection you send is on a different port as it passes through your nat router, so the router just tracks what internal address is associated with the external connection, and routs the traffic in to the correct host. look [here]("http://en.wikipedia.org/wiki/Network_address_translation") for more info.

on to subnet masks. addresses have differant classes, determine by their first number, which imply a default net mask. the ranges are:
1-126 => class A . default mask of 255.0.0.0
128-191 => class b default mask of 255.255.0.0
192-224 => class C default mask of 255.255.255.0
the rest of the ranges are used for other things, not standard addresses (like multicast groups).

subnetting (and IP itself) is an advanced topic and the reasons for it are a lot bigger than just linksys. look into it. just be prepared to count binary on your fingers, and memorize a few constants, and you'll do fine.

so now to answer your question you need to look into [port forwarding]("http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/"). once you have forwarded a port, you can connect to your service remotely, just connect to your public address, at the port specified.

let me know if you have any questions,
franklin

---

### Post by revleo on 2008-09-12
if this upload works this might help

---

### Post by doas777 on 2008-09-12
nothing to see here.

---

### Post by serpentine_bull on 2008-09-12
Awesome, thanks for the help. I'll be poking around with VNC, SSH and such over the next couple of days.

---

### Post by revleo on 2008-09-12
sorry bout that didna mean to cause trouble but sometimes easier to look at a subject like this over a period of time a few snippets of conversation are not gonna teach about networking i was in class for three months before i got  the binary counts down meself

---

### Post by doas777 on 2008-09-13
> **revleo said:**
> sorry bout that didna mean to cause trouble but sometimes easier to look at a subject like this over a period of time a few snippets of conversation are not gonna teach about networking i was in class for three months before i got  the binary counts down meself

I'm with ya man. I wish the world was a freer place, and information could flow as it wills. but if wishes were horses....

have fun,
Franklin

---

