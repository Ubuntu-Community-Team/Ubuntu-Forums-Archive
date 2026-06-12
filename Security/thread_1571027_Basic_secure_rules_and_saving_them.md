---
title: "Basic secure rules and saving them"
date: 2010-09-09
forum: Security
---

### Post by linuxuser64 on 2010-09-09
Hello,

My question has probably been answered somewhere but I'm new to this so please forgive me if this is a duplicate post of someone else's.

What I would like to do is create a good firewall and have it saved so it doesn't get lost through reboots. I have read the iptables document and the ufw document but it's still a bit confusing.

What I would like to do is be able to browse the web so I need to have rules for that as well as https. I'm not sure what rule I need for DNS for DHCP. Other than those basics I don't want anything else to happen save for updates. When I get more used to it I will add more rules if I need them. I also want IPv6 off, for incoming, outgoing and forwarding, and my guess is that I do not need any forwarding for IPv4. Ah yes and I need the loopback working.

I've seen some suggestions and I was wondering if this is a good secure firewall:

iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

iptables -A INPUT -m state --state RELATED,ESTABLISHED -j accept
iptables -A INPUT -i lo -j accept

iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j accept
iptables -A OUTPUT -i lo -j accept

# Something here for just what I need

# fallback in case using UDP for DHCP
iptables -A OUTPUT -p UDP --dport 53 -m state --state NEW -j accept


Cheers, and thanks for any help!
linuxuser64

---

### Post by BkkBonanza on 2010-09-09
You're doing this because you want to learn about iptables... to become a master of your machine, right?
Otherwise just use **gufw** for an easy to use gui interface to iptables.

don't use the line for OUTPUT with state ESTABLISHED,RELATED because that won't allow you to connect out. 

iptables -A INPUT -m state --state RELATED,ESTABLISHED -j accept
iptables -A OUTPUT -j accept

You may as well set policy ACCEPT for output and then deny specific traffic because you'll probably always have to adjust it as you use different programs.

There's a million versions of what's a good firewall though. All in all, it's not much of a worry on Ubuntu desktop. If you don't have a router between you and the net then it's more of an issue.

As for saving/restoring - you can use iptables-save filename
And then add iptables-restore filename to your interfaces file or make a script and put in /etc/network/if-up.d (files in that dir get run when the if is brought up).

I prefer to make a script so I can manually modify it and put other config steps together in the same place. In that case I use the reduced format like this,
```

#!/bin/bash

/sbin/iptables-restore <<-EOF;

*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]

-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

#... more ...

COMMIT
EOF
```

Put this in /etc/network/if-up.d/firewall and chmod 700

---

### Post by linuxuser64 on 2010-09-09
> **BkkBonaza said:**
> You're doing this because you want to learn about iptables... to become a master of your machine, right?

That's right, I'd like to learn as much as I can, and when I know a bit about it see if others want to join me in writing a little booklet on iptables for others new to it (put in other networking stuff as needed). Most books, even the big ones, just gloss over the important topic of firewalls. I suppose there's good reason for it because there's no one-size-fits-all.

> **BkkBonaza said:**
> Otherwise just use **gufw** for an easy to use gui interface to iptables.

Thanks... I'll check that out in the mean time while I try and learn as much of the gritty details of iptables as I possibly can.

> **BkkBonaza said:**
> don't use the line for OUTPUT with state ESTABLISHED,RELATED because that won't allow you to connect out. 

iptables -A INPUT -m state --state RELATED,ESTABLISHED -j accept
iptables -A OUTPUT -j accept

You may as well set policy ACCEPT for output and then deny specific traffic because you'll probably always have to adjust it as you use different programs.

Thank you again.

> **BkkBonaza said:**
> There's a million versions of what's a good firewall though. All in all, it's not much of a worry on Ubuntu desktop. If you don't have a router between you and the net then it's more of an issue.

I do have a four port modem router and I had awful problems with others I've had in the past being attacked. I managed so save some of the logs (interesting reading...) and people even put in remote admin privileges for themselves. Doesn't seem to be the case with my current modem/router though, thank goodness. I was in a pickle for a while and whoever was attacking my machine just didn't want to give up.

> **BkkBonaza said:**
> As for saving/restoring - you can use iptables-save filename
And then add iptables-restore filename to your interfaces file or make a script and put in /etc/network/if-up.d (files in that dir get run when the if is brought up).

I prefer to make a script so I can manually modify it and put other config steps together in the same place. In that case I use the reduced format like this,

<snip>

Sounds good, I'll go with the /etc/network/if-up-d option I think.

> **BkkBonaza said:**
> Put this in /etc/network/if-up.d/firewall and chmod 700

Thanks for all your help, much appreciated.

---

### Post by BkkBonanza on 2010-09-09
Routers do vary quite a bit. I had an SMC one once that had telnet open to the net with a default password. It was a while before I even realized that, fixed it and sent off a complaint email to the company.

The ones that are supported by open source after market firmwares were best. I had a Linksys WRT54GL that gave me no trouble with DD-WRT and it had heaps of nifty options.

Now I run my own Ubuntu based router which I put together myself. It's GBit LAN and an Atheros Wifi adapter for that side. I did all the firewall/routing rules in iptables and it's working well so far. I can run pretty much any services on it I want.

---

### Post by linuxuser64 on 2010-09-09
That's an interesting story there with the telnet open and default password. With my problems I was locked out my BIOS as well. I was told by the manufacturer that it was impossible to flash the BIOS unless you were physically at the machine. I also suspect something was replaced with the disk driver or the drive's firmware was fiddled with. Now I have to pay nearly as much as half the cost of a basic new laptop to get the BIOS re-flashed and the disk replaced if I need to. I'm just going to get a new laptop and cut my losses.

You obviously have a great deal of knowledge and thanks for sharing. I certainly wish I had the level of skill you have. Maybe in time if I stay with Ubuntu and read and experiment (safely though) for as long as it takes.

All the best.

---

### Post by CharlesA on 2010-09-09
> **linuxuser64 said:**
> That's an interesting story there with the telnet open and default password. With my problems I was locked out my BIOS as well. I was told by the manufacturer that it was impossible to flash the BIOS unless you were physically at the machine. I also suspect something was replaced with the disk driver or the drive's firmware was fiddled with. Now I have to pay nearly as much as half the cost of a basic new laptop to get the BIOS re-flashed and the disk replaced if I need to. I'm just going to get a new laptop and cut my losses.

Huh? The laptop was bricked because of a problem getting into the BIOS? What sort of laptop was it?

---

