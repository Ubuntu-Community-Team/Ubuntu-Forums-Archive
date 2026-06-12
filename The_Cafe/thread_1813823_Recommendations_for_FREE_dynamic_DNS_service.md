---
title: "Recommendations for FREE dynamic DNS service?"
date: 2011-07-28
forum: The Cafe
---

### Post by mips on 2011-07-28
As per the title what do you recommend and why?

EDIT: It must work behind a natted router.

---

### Post by k10wn on 2011-07-28
DynDns - because it works. I have it running in DDWRT on my Linksys WRT320N.

---

### Post by Paqman on 2011-07-28
+1 for DynDNS. OpenDNS is good too, but DynDNS seems to be pretty much universally supported by hardware.

---

### Post by 3Miro on 2011-07-28
I use DynDNS and it works just like I want it to.

---

### Post by mips on 2011-07-28
Ok so when I sign up for DynDNS what IP address do I specify as it sees my routers IP address?

---

### Post by koenn on 2011-07-28
not sure what you mean here.
what are you trying to do ?

---

### Post by mips on 2011-07-28
> **koenn said:**
> not sure what you mean here.
what are you trying to do ?

Internet---->ADSL router(NAT)---->LAN(192.168.0.0) with 2x computers.

I would like to SSH into these from a public network (internet) or from behind another natted network connected to the internet.

EDIT: ISP allocates a dynamic IP to my router which changes often. I cannot load custom firmware on my router so all changes will have to be on the clients.

---

### Post by Majorix on 2011-07-28
If you still haven't made up your mind, OpenDNS is free and I have had no problems with it in the last few years I have been using it.

---

### Post by Shpongle on 2011-07-28
I haven't tried dyndns but opendns has lots of extra features in the dashboard.

---

### Post by k10wn on 2011-07-28
> **mips said:**
> Internet---->ADSL router(NAT)---->LAN(192.168.0.0) with 2x computers.

I would like to SSH into these from a public network (internet) or from behind another natted network connected to the internet.

EDIT: ISP allocates a dynamic IP to my router which changes often.

Mine doesn't change often, but DynDNS will check and update.  In DDWRT you can specify how often it should check, but I don't recommend daily.

---

### Post by mips on 2011-07-28
I just checked & I already have a OpenDNS account.

How do I get host names assigned to my individual PCs as currently OpenDNS is seeing my routers IP address which is public while my LAN uses private addresses.

---

### Post by Dry Lips on 2011-07-28
> **mips said:**
> I just checked & I already have a OpenDNS account.
How do I get host names assigned to my individual PCs as currently OpenDNS is seeing my routers IP address which is public while my LAN uses private addresses.

An idea: You could forward SSH on different ports, so that each machine has an unique port. 
In that way you wont need two specific host names, you just specify the port when you SSH
in.

About assigning host names to specific computers behind your NAT. I simply don't know.... Anyone!?

---

### Post by Seq on 2011-07-28
> **mips said:**
> I just checked & I already have a OpenDNS account.

How do I get host names assigned to my individual PCs as currently OpenDNS is seeing my routers IP address which is public while my LAN uses private addresses.

You can't get public DNS to resolve to a private IP address and expect it to be routable. A private IP address is private, no matter how you refer to it.

You will need to set up the DNS alias to point to your router's public IP address, then set up some port forwarding on your router to your private hosts. So you would SSH to mips.dyndns.com:22 for the first machine, and mips.dyndns.com:222 for the second host (or whatever ports you decide to use. It doesn't matter).

---

### Post by Dry Lips on 2011-07-28
DynDNS has a nice howto:
[http://www.dyndns.com/support/kb/dyndns.html#howto](http://www.dyndns.com/support/kb/dyndns.html#howto)

---

### Post by mips on 2011-07-28
> **Seq said:**
> You can't get public DNS to resolve to a private IP address and expect it to be routable. A private IP address is private, no matter how you refer to it.


*sigh* I know that and not completely clueless.

I was looking at OpenDNS to assign a host name for my adsl router which gets a dynamic public IP. After that it's a matter of port forwarding on the router to the natted private addresses. The clients would then update the dynamic dns provider with the routers public IP at X intervals.

Maybe you misunderstood my post.

My query was about opendns and I still don't see them offering a service like dyndns or no-ip unless I'm looking in the wrong place.

Anyway, I have signed up with no-ip.org, I'll look at setting up the port forwarding part tomorrow.

---

### Post by k10wn on 2011-07-28
Let us know how it goes ^_^

---

### Post by Dry Lips on 2011-07-28
> **mips said:**
> *sigh* I know that and not completely clueless.

I was looking at OpenDNS to assign a host name for my adsl router which gets a dynamic public IP. After that it's a matter of port forwarding on the router to the natted private addresses. The clients would then update the dynamic dns provider with the routers public IP at X intervals.

Maybe you misunderstood my post.

My query was about opendns and I still don't see them offering a service like dyndns or no-ip unless I'm looking in the wrong place.

Anyway, I have signed up with no-ip.org, I'll look at setting up the port forwarding part tomorrow.

I don't know what Seq meant, but I certainly for a minute thought that OpenDNS was a provider of
dynamic ip... :P Oh, but it's like a parental control kind of thing?

---

### Post by koenn on 2011-07-28
OpenDNS provides dns service that you can use as a forwarder for your own 'LAN' DNS servers or DNS server for your computers, with some extras such as redirect you away from malicious sites etc
AFAIK they don't do the "DNS names for dynamic addresses" thing

You're on the right track with no-ip : you assign a name to your router's public address (as that's the only adress you can use from the internet side of things), and handle the rest by forwarding ports to the appropriate servers on your LAN.

I'd recommended DynDNS but for no other reason than I'd heard of it before i heard of no-ip, I use it, and it works. I haven't tried no-ip.

DynDNS has a client that makes sure your DNS record gets updated if your IP address changes. You can run it on one of your servers and set it up so it will still report the public IP address (of the router) to the DNS server. It's pretty much set-and-forget, so i forgot the actual details.

I don't know if no-ip's client can do that to, but I'd expect it does. 

Have fun.

---

### Post by mips on 2011-07-28
> **koenn said:**
> 
I don't know if no-ip's client can do that to, but I'd expect it does. 

Have fun.

I just installed the noip package from the repos, it asked me for my username & password and then I added it as a daemon.

I will have a look at dyndns as well.

---

### Post by Paqman on 2011-07-29
> **koenn said:**
> 
DynDNS has a client that makes sure your DNS record gets updated if your IP address changes. You can run it on one of your servers

A lot of routers have this built-in, too.

---

### Post by mips on 2011-07-29
> **Paqman said:**
> A lot of routers have this built-in, too.

Unfortunately my router is very old old and does not have this feature but on the other hand it is extremely reliable and rock solid.

I will check at some stage if this conexant based router can handle a custom firmware of sorts but somehow I doubt it.

---

### Post by mips on 2011-07-29
> **k10wn said:**
> Let us know how it goes ^_^

Working just fine using no-ip after I did the port forwarding on my router ;)

Thanks everybody for you help.

---

