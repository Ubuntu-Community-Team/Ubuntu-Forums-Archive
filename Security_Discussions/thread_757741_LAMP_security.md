---
title: "LAMP security"
date: 2008-04-17
forum: Security Discussions
---

### Post by opus_az on 2008-04-17
Hi. I'm steadily learning about Ubuntu and LAMP. Everything is working fine and I'll soon have a small site going public with a blog and a few other basic things. Right now most of LAMP is still at its default installed state.

I'd like to know what typically should to done for basic essential security. For example I know how important it is to put an Apache password on the phpmyadmin directory.

I'm still a novice and this isn't a very important website but I want to be 'proper'. I hope to be doing much more in the future and I don't want to miss the security essentials.

Any suggestions or links?

---

### Post by FakeOutdoorsman on 2008-04-17
Here's an easy start.  First secure your shell access:
[Securing OpenSSH]("http://wiki.centos.org/HowTos/Network/SecuringSSH")
[Keeping SSH access secure]("http://www.debian-administration.org/articles/87")

Also, never forget to keep your web applications/software updated.  I once worked on a server that was compromized through an old version of AWStats.

I'll post more when I'm not supposed to be working.

---

### Post by The Tronyx on 2008-04-17
> **FakeOutdoorsman said:**
> Here's an easy start.  First secure your shell access:
[Securing OpenSSH]("http://wiki.centos.org/HowTos/Network/SecuringSSH")
[Keeping SSH access secure]("http://www.debian-administration.org/articles/87")

Also, never forget to keep your web applications/software updated.  I once worked on a server that was compromized through an old version of AWStats.

I'll post more when I'm not supposed to be working.

Nice suggestions.  I also recommend downloading nikto and running it against your server.  It's very helpful for spidering known vulnerable URLs that can be major security holes sometimes left open by default settings.  Nessus is also a nice automated scanner for finding potential problems and may have a nikto plugin you can use (I'd have to check to be sure on that one though).  Both of these tools will probably provide a few false positives so be sure to verify the test results manually.

Hope tha thelps and good luck!:)

---

### Post by opus_az on 2008-04-18
Thanks, all! Two excellent suggestions. I'll spend some time on both of them this weekend.

Thanks again!

---

### Post by HermanAB on 2008-04-18
See this doc:
[http://www.nsa.gov/snac/os/redhat/rhel5-guide-i731.pdf](http://www.nsa.gov/snac/os/redhat/rhel5-guide-i731.pdf)

It contains very good info on securing Apache and PHP.

Cheers,

Herman

---

### Post by FakeOutdoorsman on 2008-04-18
Next you can work on your iptables firewall:

[Basic IPTables]("http://www.5dollarwhitebox.org/wiki/index.php/Howtos_Basic_IPTables")
[IPTables HOWTO]("http://wiki.centos.org/HowTos/Network/IPTables")
[Using iptables to rate-limit incoming connections]("http://www.debian-administration.org/articles/187")

Some people recommend Shorewall or FireHOL to help build/manage their firewall, but I have no experience with them.  Others might also recommend Fail2Ban and DenyHosts (which I also have no experience with) which watch your logs for dictionary/brute force attacks and ban or rate-limit the offenders' connections, but you can do something similar with iptables with the above link.

I recommend only working on iptables if you have physical access to your machine because it is easy to block yourself from connecting if you make a mistake.

Here's a script I use for a database backup computer.  There are some extra items in there as examples.  This script only allows local LAN computers to connect to it:
```
#!/bin/bash
#
# iptables configuration script
#
# Flush all current rules from iptables
#
iptables -F
#
# Set default policies for INPUT, FORWARD and OUTPUT chains
#
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT
#
# Set access for localhost
#
iptables -A INPUT -i lo -j ACCEPT
#
# Set access for eth0
#
#iptables -A INPUT -i eth0 -j ACCEPT
#
# Accept packets belonging to established and related connections
#
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
#
# Accept packets from trusted IP addresses
#
iptables -A INPUT -s 192.168.1.0/24 -j ACCEPT
#
# Accept tcp packets on destination port 22 (SSH) from private LAN
#
iptables -A INPUT -p tcp -s 192.168.1.0/24 --dport 22 -j ACCEPT
#
# Accept tcp packets on destination ports 40821-40830 (bittorrent)
#
#iptables -A INPUT -p tcp --dport 40821:40830 -j ACCEPT
#
# Accept udp packets on destination port 40820 (bittorrent DHT)
#
#iptables -A INPUT -p udp --dport 40820 -j ACCEPT
#
# Save settings
#
iptables-save
#
# List rules
#
iptables -L -v
exit
```

---

### Post by FakeOutdoorsman on 2008-04-18
I almost forgot: [Securing Debian Manual]("http://www.debian.org/doc/manuals/securing-debian-howto/").

---

### Post by opus_az on 2008-04-21
Wow. Again, thanks everyone! I got bogged down in more mundane  details of my LAMP server this weekend (I was my own worst enemy :) ) so I may not get to use this info for another few days.

But, thanks again! It's greatly appreciated.

---

