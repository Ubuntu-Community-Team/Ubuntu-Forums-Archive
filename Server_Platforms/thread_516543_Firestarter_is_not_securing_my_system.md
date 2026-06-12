---
title: "Firestarter is not securing my system"
date: 2007-08-03
forum: Server Platforms
---

### Post by mr_niceguy on 2007-08-03
For a program designed for simplicity I cannot believe there can be such an absolute security failure and yet it is not treated as a priority for Ubuntu. Searching these forums it is clear that several people have noticed the same thing. Sometimes it works. Sometimes it doesn't.

I can set Firestarter to block all incoming requests and yet everything IS allowed. How is that possible and how is this not raising alarm bells when Linux uses security as an evangelism point? 

From what I can tell on these forums the answer is to learn iptables. I certainly will and in the mean time am using a router with a built in firewall.

But as someone who has converted people to Linux, often because of security, this really blows me away. Red Hat would NEVER let something like this fly under the radar. (to be fair they need to have a working firewall as they generally have listening ports by default)

---

### Post by silent1643 on 2007-08-03
linux in general is very safe, why are you so eager to put your system in a security shutdown.
i have been using ubuntu with no security issues since my first install.

---

### Post by eentonig on 2007-08-03
I don't use firestarter, because it's too damn simple. (But I never had the works/don't work situation you describe)

What I can recommend, is fwbuilder. It gives you a flexible GUI to build you policy. And then installs it on the fw (doesn't have to be the same machine).

One thing to remember, is to save your new policy on the firewall (iptables-save) if you want the rules to be active when the firewall/pc reboots

---

### Post by bodhi.zazen on 2007-08-03
> **mr_niceguy said:**
> For a program designed for simplicity I cannot believe there can be such an absolute security failure and yet it is not treated as a priority for Ubuntu. Searching these forums it is clear that several people have noticed the same thing. Sometimes it works. Sometimes it doesn't.

I can set Firestarter to block all incoming requests and yet everything IS allowed. How is that possible and how is this not raising alarm bells when Linux uses security as an evangelism point? 

From what I can tell on these forums the answer is to learn iptables. I certainly will and in the mean time am using a router with a built in firewall.

But as someone who has converted people to Linux, often because of security, this really blows me away. Red Hat would NEVER let something like this fly under the radar. (to be fair they need to have a working firewall as they generally have listening ports by default)

Discussions about firewalls are often, IMO very opinionated.

With a default install there are no open ports so, in the opinion of the Ubuntu developers, a firewall is not necessary.

You can configure your firewall with firestarter. If firestarter is "not working" that means it is not configured the way you like.

I suggest you read up on firestarter :

[http://doc.gwos.org/index.php/Firestarter_Guide](http://doc.gwos.org/index.php/Firestarter_Guide)

[http://www.techotopia.com/index.php/Using_Firestarter_to_Configure_an_Ubuntu_Linux_Firewall](http://www.techotopia.com/index.php/Using_Firestarter_to_Configure_an_Ubuntu_Linux_Firewall)

[http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html)

See Firestarter section :  [http://www.linuxforums.org/security/locking_down_ubuntu.html](http://www.linuxforums.org/security/locking_down_ubuntu.html)

---

### Post by dannyboy79 on 2007-08-03
with all the perl/bash/python scripts out there that build iptables rules and whatnot, I don't ever see a need for Firestarter. You download the script, then make it executable (make sure you trust the source of the code or at least review it. with a tiny amount of knowledge of iptables one can see if the code is what it says it is), then simply run it. It'll ask you if you want access for web  server, pop server, samba, ssh, ftp, etc etc etc you just answer n and y and then it does it's job. DONE.

---

### Post by koenn on 2007-08-03
> **mr_niceguy said:**
> For a program designed for simplicity I cannot believe there can be such an absolute security failure and yet it is not treated as a priority for Ubuntu. Searching these forums it is clear that several people have noticed the same thing. Sometimes it works. Sometimes it doesn't.

I can set Firestarter to block all incoming requests and yet everything IS allowed. How is that possible and how is this not raising alarm bells when Linux uses security as an evangelism point? 

you're making a lot of noice, but you're not offering any proof for your accusetions and allegations, other than a vague reference to "several people have noticed the same thing". 

It's fairly simple. Firestarter is a front-e,d to iptables. Therefore, configuration made in firestartershould be reflected in iptables config. 

To me it is. I've set firestarter to be permissive OUTBOUND, and block everything inbound. I see the same thing in the underlying iptables. 
```

~$ sudo iptables --list
Password:
Chain INBOUND (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
LSI        all  --  anywhere             anywhere

Chain INPUT (policy DROP)
target     prot opt source               destination
INBOUND    all  --  anywhere             anywhere

Chain FORWARD (policy DROP)
target     prot opt source               destination

[...]

Chain OUTPUT (policy DROP)

[...]

```

To me, that suggests you (and the "several others") are experiencing a problem between keyboard and chair, unless you can come up with something substantial.

---

### Post by mr_niceguy on 2007-08-03
First, thanks for the replies.

One of the things I like better about Ubuntu than Redhat (and derivatives) is that there are no listening services by default and no need for a firewall. But when you implicitly set up a firewall using the ***default tool from the official repositories*** it should either work or tell you that it doesn't. We're not talking about some annoying little glitch on a user interface - we're talking fundamental security. 

If you are given the impression you have a working firewall you are being led to believe you can configure your system rather differently than if you didn't. In my case that involves local services on ports which are not to be accessible to the WWW most of the time.

I am seeing that the problem comes when configuring a static IP to my ethernet card. Firestarter is silently configuring input acceptance to any request stemming from my ISP. (Yikes! that's everything from the WWW) Conversely if I use my router to accept the static IP and use DHCP to connect my ethernet to the router Firestarter seems to work like a charm. (even though I don't need it then as the router has a firewall)

I will check out some of the other tools you people have been kind enough to mention and learn more about iptables. But I am wondering if there needs to be some kind of warning concerning Firestarter?

---

### Post by bodhi.zazen on 2007-08-03
> **mr_niceguy said:**
> First, thanks for the replies.

One of the things I like better about Ubuntu than Redhat (and derivatives) is that there are no listening services by default and no need for a firewall. But when you implicitly set up a firewall using the ***default tool from the official repositories*** it should either work or tell you that it doesn't. We're not talking about some annoying little glitch on a user interface - we're talking fundamental security. 

Security is more then a single program and there are many ways to configure Firestarter.

I happen to like the way firestarter is setup, but that is me.

In terms of security, I read the documentation and adapted my system to my needs. This is also the Fedora way.

You input and suggestions I am sure would be welcomed, feel free to leave them here ...

[http://ubuntuforums.org/forumdisplay.php?f=238](http://ubuntuforums.org/forumdisplay.php?f=238)

One thing about Ubuntu, it is easy to become involved so I wouls encourage you to do so.

---

### Post by mr_niceguy on 2007-08-04
> **koenn said:**
> To me, that suggests you (and the "several others") are experiencing a problem between keyboard and chair, unless you can come up with something substantial.

To me that suggests you think Firestarter consistently generates the same policies.

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  nsc1.isp.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  nsc1.isp.net  anywhere            
ACCEPT     tcp  --  nsc2.isp.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  nsc2.isp.net  anywhere            
ACCEPT     0    --  anywhere             anywhere            
LSI        udp  --  anywhere             anywhere            udp dpt:33434 
LSI        icmp --  anywhere             anywhere            
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  anywhere             24.79.135.255       
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

```

Not quite the same but I would be lying if I said I understand it. What I do know is that I do not have any services or ports listed in the "Inbound traffic policy". If I connect from my router the firewall blocks inbound traffic which I did not initiate. (yes, I did open the firewall on the router to check) If I connect directly from my ethernet card it allows everything.

---

### Post by koenn on 2007-08-04
> **mr_niceguy said:**
> To me that suggests you think Firestarter consistently generates the same policies.

it's a program. What else can it do ? generate policies at random ? 

> **mr_niceguy said:**
> 
If I connect directly from my ethernet card it allows everything.
where in the output you've posted do you see that ? 
what I see is that, a.o., 
tcp and udp packets that do not have their FIN,SYN,RST,ACK/SYN flag set are accepted - those are replies on connections initiated FROM your computer, so it's quite normal to accept them - you wouldn't be able to do anything usefull without it.

There's also
```
INBOUND    0    --  anywhere             anywhere 
``` but that does not mean "everything is allowed" - it means that packets that did not matchget accepted or dropped due to rules earlier in the INPUT chain, are sent to the INBOUND chain, and threated wuth the rules in that chain : 
```
ACCEPT     tcp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED
LSI        all  --  any    any     anywhere             anywhere

```
so again, only tcp or udp packets that are part of a conversation you initiated, are accepted.

Also note that the -L or --list option does not show the complete rules. If you make it verbose (-v) you'll see that some of the ACCEPT anywhere - anywhere rules only apply to the loopback interface, to allow processes on your computer to talk to eachother. EG.
```

Chain INPUT
target        prot   opt   in     out     source               destination
ACCEPT   all      --     lo      any     anywhere             anywhere
DROP       icmp  --    any    any     anywhere             anywhere            
DROP       all      --    eth0   any     anywhere             255.255.255.255

```

And so on. 

I agree that the Firestarter GUI hides a lot of detail (that's probably what it was made for, to protect the user from the ugly technicalities) and that Firestarter's use of custom chains requires some tracking to see the path a packet is send through before it's eventually ACCEPTed or DROPped - combined with some knowledge of the TCP/IP protocols to understand the significance of !SYN and "ESTABLISHED" etc. 

Still, I'd be interested to know what makes you say "It allows everything". Where do you see that ? In the iptables ? Or can you/someone else  actually connect to a port from the outside while you're firewall is on ?
Can you post output that supports your claim that Firestarter's rules depend on whether you use a static or dynamically assigned IP address ? That Firestarter is silently configuring input acceptance to any request stemming from my ISP ?

---

### Post by mr_niceguy on 2007-08-04
> **koenn said:**
> Still, I'd be interested to know what makes you say "It allows everything". Where do you see that ? In the iptables ? Or can you/someone else  actually connect to a port from the outside while you're firewall is on ?

The latter. I don't understand iptables so I cannot make any claims from what I see there.

The iptables I posted is the current one with the router in front. I should really check to see if it is different when connecting directly from the ethernet card. Unfortunately it takes several hours before my ISP flushes its ARP records so I will wait for a time when I can be offline for a bit.

I appreciate that you've taken the time to explain and go through some of this stuff.

---

### Post by dannyboy79 on 2007-08-05
whether you connect a router in between you and the modem (or isp connection) or not has nothing to do with iptables rules.

---

### Post by mr_niceguy on 2007-09-25
I do not know why but I am no longer having these issues. Firestarter is working exactly as expected.

---

