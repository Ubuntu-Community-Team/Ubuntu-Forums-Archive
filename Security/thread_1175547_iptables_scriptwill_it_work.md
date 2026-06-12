---
title: "iptables script:will it work"
date: 2009-06-01
forum: Security
---

### Post by Steve1961 on 2009-06-01
Just looking for any feedback about the simple script I've created below.  I've not delved into iptables before but I want to start using the witopia openvpn service and ufw, firestarter, etc didn't seem to be flexible enough.

Basically I want to allow all outgoing traffic, allow all access from my home network (they're all my machines anyway), and allow a few services - ssh, bittorrent, from anywhere.  I'm not sure that I need the specific cups and samba entries but hey...

Also, i believe there was a problem with network-manager when running iptables.  Is this still the case?

Anyway, heres the script.  Any feedback appreciated.  

```

#!/bin/bash
############################################################
# * Blocks all incoming connections, except those opened by
# me, or related to already open connections
# * Blocks all forward requests
# * Allows all outgoing connections
# * Allows all incoming traffic from 192.168.1.0/24 network
# * Allows printer sharing from home network
# * Allow samba from home network
# * Allows incoming traffic on ssh port 45500/tcp and 22/tcp
# * Allows incoming traffic on bittorrent 59400/tcp/udp
# * Allows incoming traffic openvpn 1194/udp
# * Allows all traffic on tun0 interface
###
############################################################
#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 
modprobe ip_conntrack_irc
modprobe ip_conntrack_ftp
# Clearing all previous rules
iptables -F
iptables -X
# Setting Default Policies
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP
# Allowing already-established and related-incoming connections
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
# Allow all traffic on localhost
iptables -A INPUT -i lo -j ACCEPT
# Allow home network - probably not necessary with other entries
iptables -A INPUT -s 192.168.1.0/24 -d 192.168.1.0/24 -j ACCEPT
iptables -A INPUT -s 192.168.1.0/24 -d 0.0.0.0/0 -j ACCEPT
iptables -A INPUT -s 0.0.0.0/0 -d 192.168.1.0/24 -j ACCEPT 
# Samba access from home network only
iptables -A INPUT -p tcp -s 192.168.1.0/24 --dport 137 -j ACCEPT
iptables -A INPUT -p udp -s 192.168.1.0/24 --dport 137 -j ACCEPT
iptables -A INPUT -p tcp -s 192.168.1.0/24 --dport 138 -j ACCEPT
iptables -A INPUT -p udp -s 192.168.1.0/24 --dport 138 -j ACCEPT
iptables -A INPUT -p tcp -s 192.168.1.0/24 --dport 139 -j ACCEPT
iptables -A INPUT -p udp -s 192.168.1.0/24 --dport 139 -j ACCEPT
iptables -A INPUT -p tcp -s 192.168.1.0/24 --dport 445 -j ACCEPT
iptables -A INPUT -p udp -s 192.168.1.0/24 --dport 445 -j ACCEPT
# Cups IPP access from home network only
iptables -A INPUT -j ACCEPT -p tcp -s 192.168.1.0/24 --dport 631
iptables -A INPUT -j ACCEPT -p udp -s 192.168.1.0/24 --dport 631
# Allow SSH access on port 45500/tcp
iptables -A INPUT -p tcp --dport 45500 -j ACCEPT
# Keep port 22 open anyway
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
# Bittorrent port
iptables -A INPUT -p tcp --dport 59400 -j ACCEPT
iptables -A INPUT -p udp --dport 59400 -j ACCEPT
# Openvpn port
iptables -A INPUT -p udp --dport 1194 -j ACCEPT
# Allow unrestricted traffic on tun0
iptables -A INPUT -i tun0 -j ACCEPT
iptables -A OUTPUT -o tun0 -j ACCEPT
iptables -A FORWARD -o tun0 -j ACCEPT 
```

---

### Post by Dr Small on 2009-06-01
Tell me this, are you behind a firewall/router?
If so, I find that setting up firewall rules on individual systems is somewhat unnecessary (unless the network is hostile). You can use your firewall/router to setup rules for inbound/outbound along with port forwarding and such which protects all of your systems.

---

### Post by Steve1961 on 2009-06-02
> **Dr Small said:**
> Tell me this, are you behind a firewall/router?
If so, I find that setting up firewall rules on individual systems is somewhat unnecessary (unless the network is hostile). You can use your firewall/router to setup rules for inbound/outbound along with port forwarding and such which protects all of your systems.

Yes I am, and I'm aware of the debates, it's something often discussed at my local LUG.  However, I just feel more comfortable with something additional to the router.  More importantly though iptables are something I'd like to learn, which brings me back to my original questions and reasons for this post.

---

### Post by bodhi.zazen on 2009-06-02
Your script is nice however ...

1. First why are you writing this script ? iptables-save and iptables-restore are much easier.

iptables-save > /etc/iptables.save

iptables-resotre < /etc/iptables.save

2. Why are you doing all those modprobe ? Those modules are already loaded, there is no reason to keep loading those modules.

3. IMO setting the default policy to DROP is a bad idea. You will lock yourself out if you run:

iptables -F

Rather then setting the policy, make the last rule in the chain to drop all. That way you achieve the same thing without the risk of locking yourself out.

And trust me, locking oneself out is a #1 mistake of new users with most of these firewall tools and your scipt / policies are a set up for just that.

4. I put the lo interface first.

5. These rules are redundant
These rules are redundant[FONT=monospace]

[/FONT]iptables -A INPUT -s 192.168.1.0/24 -d 192.168.1.0/24 -j ACCEPT[FONT=monospace]
[/FONT]iptables -A INPUT -s 192.168.1.0/24 -d 0.0.0.0/0 -j ACCEPT

6. This rule probably does nothing[FONT=monospace], unless you are using your box as a router ?

[/FONT]iptables -A INPUT -s 0.0.0.0/0 -d 192.168.1.0/24 -j ACCEPT 

7. You should look at your samba ports . you do not need both udp and tcp on those ports, some are tcp, others are udp, none are both, and you are missing some ports.

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/securing-samba.html#firewallports](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/securing-samba.html#firewallports)

8. Not sure about IPP. Are you using IPP ?

9. Why keep port 22 open anyway ? are you using it ?
[FONT=monospace]
[/FONT]# Allow SSH access on port 45500/tcp[FONT=monospace]
[/FONT]iptables -A INPUT -p tcp --dport 45500 -j ACCEPT[FONT=monospace]
[/FONT]# Keep port 22 open anyway[FONT=monospace]
[/FONT]iptables -A INPUT -p tcp --dport 22 -j ACCEPT

9. Your bittorrent probably needs some help. Unless you are running a bittorrent server, traffic is allowed under related.

10. For your VPN tunnel, why not use masquerade ?

iptables -t nat -A POSTROUTING -s 10.0.0.0/24 -o eth0 -j MASQUERADE

You will need to change the ip netmask on that command ;)

---

### Post by Steve1961 on 2009-06-02
Many thanks for the constructive comments.  As you've probably guessed this script has been cobbled together from many google and forum searches, and as I'm far from confident with iptables this is exactly the sort of feedback I was looking for.  I've answered your questions in context: 

```
1. First why are you writing this script ? iptables-save and iptables-restore are much easier.

iptables-save > /etc/iptables.save

iptables-resotre < /etc/iptables.save
```

So by that I take it you mean just enter the rules and then run those commands.  If that's all it takes, then yes I agree it would seem easier.

```
2. Why are you doing all those modprobe ? Those modules are already loaded, there is no reason to keep loading those modules.
```

Cut and paste from a how to on the forums.  I checked lsmod and saw that they were indeed loaded just after posting so my latest version doesn't include them.

```
3. IMO setting the default policy to DROP is a bad idea. You will lock yourself out if you run:

iptables -F

Rather then setting the policy, make the last rule in the chain to drop all. That way you achieve the same thing without the risk of locking yourself out.

And trust me, locking oneself out is a #1 mistake of new users with most of these firewall tools and your scipt / policies are a set up for just that.
```

Well I'm pleased you pointed that one out.  I'll sort that out immediately and take your advice.  

```
4. I put the lo interface first.
```

Ok

```
5. These rules are redundant
These rules are redundant[FONT=monospace]

[/FONT]iptables -A INPUT -s 192.168.1.0/24 -d 192.168.1.0/24 -j ACCEPT[FONT=monospace]
[/FONT]iptables -A INPUT -s 192.168.1.0/24 -d 0.0.0.0/0 -j ACCEPT

6. This rule probably does nothing[FONT=monospace], unless you are using your box as a router ?

[/FONT]iptables -A INPUT -s 0.0.0.0/0 -d 192.168.1.0/24 -j ACCEPT 
```

I thought there were probably some rules that were unnecessary, so thanks again.

```
7. You should look at your samba ports . you do not need both udp and tcp on those ports, some are tcp, others are udp, none are both, and you are missing some ports.

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/securing-samba.html#firewallports](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/securing-samba.html#firewallports)

```

Too much cuting and pasting.  I would have checked before going live with this script but initially just wanted to make sure my syntax was ok.

```
8. Not sure about IPP. Are you using IPP ?
```

I am.  I share my hp printer attached to my desktop with two Ubuntu laptops, and ipp is what seems to work well.

```
9. Why keep port 22 open anyway ? are you using it ?
[FONT=monospace]
[/FONT]# Allow SSH access on port 45500/tcp[FONT=monospace]
[/FONT]iptables -A INPUT -p tcp --dport 45500 -j ACCEPT[FONT=monospace]
[/FONT]# Keep port 22 open anyway[FONT=monospace]
[/FONT]iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

No, and it's now deleted.

```
9. Your bittorrent probably needs some help. Unless you are running a bittorrent server, traffic is allowed under related.
```

I know, but opening a port seems to improve performance - at least that's my impression.

```
10. For your VPN tunnel, why not use masquerade ?

iptables -t nat -A POSTROUTING -s 10.0.0.0/24 -o eth0 -j MASQUERADE

You will need to change the ip netmask on that command ;)[/QUOTE]
```

Mmmm. this is where I get a bit lost and need to do some reading, but I'll get to it.

Again, many thanks.

---

