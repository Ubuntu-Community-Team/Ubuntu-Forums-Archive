---
title: "What ports and IP addrs need to be open for Ubuntu to work?"
date: 2008-02-08
forum: Server Platforms
---

### Post by samaricsm on 2008-02-08
I have written an iptables script to test on my machine before implementing it on the router.  The only traffic allowed in is ESTABLISHED,RELATED.  The only traffic I allowed out was:
FTP (21,22)
email (25,110)
NTP (37)
whois (43)
DNS (udp 53)
web (80,443)

Everything, except the update manager seems to be working fine.  The update manager seems to want 169.254.1.135:21302, part of the zeroconf/multicast DNS protocol.

Before I get bitten too badly, what other protocols or IP addresses do I need to leave open?

Thanks

---

### Post by faulkes on 2008-02-08
> **samaricsm said:**
> I have written an iptables script to test on my machine before implementing it on the router.  The only traffic allowed in is ESTABLISHED,RELATED.  The only traffic I allowed out was:

FTP (21,22)
email (25,110)
NTP (37)
whois (43)
DNS (udp 53)
web (80,443)



If you are only letting in established or related connections, why are you
filtering outbound?  I.e. do you have a specific need? is this box running as
a gateway/firewall?

Edit: nevermind, I should learn to read ;), see below.

> 
Everything, except the update manager seems to be working fine.  The update manager seems to want 169.254.1.135:21302, part of the zeroconf/multicast DNS protocol.

Before I get bitten too badly, what other protocols or IP addresses do I need to leave open?

Thanks

That all depends on what applications you use, or in the case of this being
a gateway/firewall box, what your users use.

MSN / any IM protocol
Torrents
VOIP
SSH
Telnet
IRC
VPN
etc.

Faulkes

---

### Post by samaricsm on 2008-02-08
Thanks for the reply.

Yes, I am familiar with the other services, and their IP needs.  I was wondering if there were any more for native Ubuntu that I needed to worry about.  Until yesterday, I had never heard of zeroconf.  (Not too surprising, I have spent my life securing the Redmond drain, and PuNP is a big no-no through my firewalls.)

I looked, and I could not find any where that states, "For Ubuntu to work, have the following ports open:".

---

### Post by The Cog on 2008-02-09
Looks like a good set of stuff to me. You don't need to allow the zeroconf stuff out - in fact I don't think you are allowed to use those addresses on the Internet.

If you do this with iptables on your desktop, you also need to allow the loopback interface to talk to itself or strange things get broken internally, like print spooling.
iptables -A INPUT -i lo -j ACCEPT

---

### Post by samaricsm on 2008-02-12
Yes,  thanks for the tip on 127.  I wasn't sure if it got as far as netfilter.  Now, I know.

Currently, it is on  my desktop.  The router that I got from the ISP has a firewall, but it is useless.  I need their router, as it is a MoCA protocol.  Dusting off my old box.  It will be my new firewall.

---

### Post by Gen2ly on 2008-02-12
Heres my firewall walkthrough.  I'd give the original guide - but its a been.. wiked.  

Goal

Make sure all ports are closed and that internet connection prevents incoming attacks.

To Do
&#8226; Internet Streaming - Safe?

Creating Rules

# List rules
iptables -nvL

# Flush Tables
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -F
iptables -X

# Input Policy

# Dropping All and adding exceptions
iptables -P INPUT DROP
iptables -A INPUT -i lo -j ACCEPT

# Limit Ping
iptables -A INPUT -m state --state INVALID -j DROP

# Allow established connections to continue
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Some icmp are useful (needed for pings)
iptables -A INPUT -p icmp --icmp-type destination-unreachable -j ACCEPT
#iptables -A INPUT -p icmp --icmp-type time-exceeded -j ACCEPT
#iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
#iptables -A INPUT -p icmp --icmp-type echo-reply -j ACCEPT

# Allow ssh, http, secure http
iptables -A INPUT -p tcp --dport ssh -j ACCEPT
iptables -A INPUT -p tcp --dport http -j ACCEPT
iptables -A INPUT -p tcp --dport https -j ACCEPT

# Bittorrent
iptables -A INPUT -p tcp --dport 6900:6950 -j ACCEPT

# Output Policy

iptables -P OUTPUT DROP
iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
iptables -A OUTPUT -p icmp -j ACCEPT

# Allow DNS
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT

# Allow http, https, ssh and bittorrent
iptables -A OUTPUT -p tcp --dport ssh -j ACCEPT
iptables -A OUTPUT -p tcp --dport http -j ACCEPT
iptables -A OUTPUT -p tcp --dport https -j ACCEPT
iptables -A OUTPUT -p tcp --dport 6900:6950 -j ACCEPT

# Forward Policy

# iptables on same machine, not necessary to forward
iptables -P FORWARD DROP
#iptables -A FORWARD -s 10.0.1.169 -p tcp --dport 6900:6950 -j ACCEPT


Save the Rules, Backup and Start.

Adding rules saves them, but if you want to be safe.

&#8226; /etc/init.d/iptables save

Make a backup of the rules

cp /var/lib/iptables/rules-save /var/lib/iptables/rules.working

Start iptables and add to run level 

/etc/init.d/iptables start
rc-update all iptables default

The iptables configuration file (not much here)

geany /etc/conf.d/iptables

Issues
&#8226; Bittorrent trackers are on random ports the only way to enable them is to establish a connection them before starting a firewall.
&#8226; Subspace Tracker is on what port?

Firewall Hardening via Kernel
&#8226; [http://www.gentoo.org/doc/en/security/security-handbook.xml?full=1#book_part1_chap9](http://www.gentoo.org/doc/en/security/security-handbook.xml?full=1#book_part1_chap9)

&#8226; These are done modifying /proc with sysctl in /etc/sysctl.conf
&#8226; These also appear to be able to be done with firewall rules which is probably the best way.
&#8226; disable ICMP ping messages ( type 0 )
&#8226; disable response to ICMP broadcasts
&#8226; disable ICMP redirect packets
&#8226; disable ICMP bad error messages
&#8226; Disable source routed packets
&#8226; Enable reverse path filtering~~
~~* In sysctrl now not using bash script

---

