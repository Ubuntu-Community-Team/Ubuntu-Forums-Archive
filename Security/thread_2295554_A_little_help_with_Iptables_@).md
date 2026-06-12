---
title: "A little help with Iptables :@)"
date: 2015-09-19
forum: Security
---

### Post by mr-woof on 2015-09-19
Hi all,

I've been messing around today setting up an SSH server so I can use it with SSH tunnel on my android phone to SSH proxy everything, when joining unknown or public wifi networks. I've done the security basis regarding SSH, no root login, keys, changed the port etc and I'm happy with that. That is unless, someone can recommend something that I've missed?

The next thing I want to do is use Iptables and really lock down the server, this is were this post comes in as I've only started learning Iptables for this task. 

I did a bit of googling around and I found a basic script that someone posted online, which only allows port 22 in and out. This works fine, I can connect via ssh in and out and I understand what the rules are doing. 

The problem comes when I use ssh tunnel, it'll connect but then I can't do anything. Now, I understand the rules below wont let anything else in/out of the server except ssh, this is the bit I'm stuck at. 

I'm not sure what needs to get out, would it be http, https and dns? 

I've tried amending the OUTPUT rule to ACCEPT and removed the last two rules and I'm not getting anywhere, apart from locking myself out of the server lol.

Anyone got any ideas? :@) Any iptables gods handy?

----------------------------------------------------------
very, very basic script

server_IP="x"

iptables -F
iptables -X

iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

iptables -A INPUT -p tcp -s 0/0 -d $SERVER_IP --sport 513:65535 --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp -s $SERVER_IP -d 0/0 --sport 22 --dport 513:65535 -m state --state ESTABLISHED -j ACCEPT

iptables -A INPUT -j DROP
iptables -A OUTPUT -j DROP

---

### Post by QDR06VV9 on 2015-09-19
With not knowing what you have already read and seen this always a good reference [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
And maybe a VPN [http://gizmodo.com/5990192/vpns-what-they-do-how-they-work-and-why-youre-dumb-for-not-using-one](http://gizmodo.com/5990192/vpns-what-they-do-how-they-work-and-why-youre-dumb-for-not-using-one)
If you do decide a VPN is a good choice make sure you understand their workings, as some are harder to configure correctly on servers.
Kind Regards

---

### Post by mr-woof on 2015-09-19
Hi,

thanks for the link, looks great I'll get reading

---

### Post by CharlesA on 2015-09-20
Oldish thread, but have a read here:
[http://bodhizazen.net/Tutorials/SSH_security](http://bodhizazen.net/Tutorials/SSH_security)

---

### Post by mr-woof on 2015-09-24
Thanks Charles, I've had a play but still can't seem to get anything working when the script is running.

I'll have another play with it tonight

---

### Post by CharlesA on 2015-09-24
If you drop the output rule, it should work fine.

You could even simplify the rules entirely. This is what I have running:
```
#!/bin/bash

iptables=/sbin/iptables

# FLUSH existing rules
$iptables -F

# REJECT connections with an invalid state
$iptables -A INPUT -m state --state INVALID -j REJECT
# Accept Related,Established connections
$iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
# Accept SSH
$iptables -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
# Prevent Bruteforce attacks against SSH
$iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH --rsource -j ACCEPT
$iptables -A INPUT -m recent --update --seconds 600 --hitcount 8 --rttl --name SSH --rsource -j REJECT
# Allow Loopback
$iptables -A INPUT -i lo -j ACCEPT
# REJECT all not accepted
$iptables -A INPUT -j REJECT

```

Put that in a file called iptables in /etc/network/if-pre-up.d/ and make it executable.

That will enable the firewall rules before the interface is brought up.

EDIT: FWIW, why not just use a VPN instead of an SSH tunnel? It would probably be easier to set up.

---

### Post by The Cog on 2015-09-24
It may be that your blocking outgoing name resolution queries (DNS, UDP port 53) is your problem.

---

### Post by mr-woof on 2015-09-24
Hi guys, thanks for the replies. 

The Cog, I think you're right. I've gone through auth.log and I'm seeing this sort of error:

error: connect_to [www.google.com:](www.google.com:) unknown host (Temporary failure in name resolution)

Doh....

---

### Post by mr-woof on 2015-09-24
As Charles as suggested, I've removed the drop/forward rules, so this is what I've ended up with so far and it's now working with ssh tunnel

iptables -F
iptables -X

iptables -P INPUT DROP

iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

---

### Post by mr-woof on 2015-09-24
Okies, this is what I've got as I've added Charles SSH brute force bits in as well:

# Flush all rules
iptables -F
iptables -X

# INPUT Policy to drop
iptables -P INPUT DROP

# Allow Loopback
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

# Allow SSH IN  on 22
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH --rsource -j ACCEPT
iptables -A INPUT -m recent --update --seconds 600 --hitcount 3 --rttl --name SSH --rsource -j REJECT

# REJECT all not accepted
iptables -A INPUT -j REJECT

Anything else I should consider adding?

---

### Post by mr-woof on 2015-09-24
It's been a good learning exercise, but as mentioned above I'll probably go for a VPN solution instead of messing around with SSH tunnels as I can't get it working on cyanogen mod 12.1 on my phone. It connects but nothing seems to be getting pushed down the SSH pipe, but works fine on the older cyanogen on my Nexus 7.

I'm thinking of having a play with openvpn and seeing if I can get that to work, the android openvpn client seems good. Is it difficult to get up and running?

---

### Post by CharlesA on 2015-09-24
I'll leave this here: [https://github.com/Nyr/openvpn-install](https://github.com/Nyr/openvpn-install)

I used it to set up my VPS with OpenVPN (cuz I'm lazy).

---

