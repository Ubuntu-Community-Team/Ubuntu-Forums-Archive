---
title: "ubuntu 14.04 looses ip forwarding"
date: 2016-01-08
forum: Server Platforms
---

### Post by Seb_Boffen on 2016-01-08
Hi please help my newly installed ubuntu 14.04 upgrade from 12.04 (the real new install), Annex router, dhcp server, web server, dns server, firewall, ftp server, mail server, samba server. Looses the default gateway and the ip forward ability.

Default iptables rules:

#!/bin/bash
# Accept all packets via ppp* interfaces (for example, ppp0)
/sbin/iptables -A INPUT -i ppp+ -j ACCEPT
/sbin/iptables -A OUTPUT -o ppp+ -j ACCEPT
# Accept incoming connections to port 1723 (PPTP)
/sbin/iptables -A INPUT -p tcp --dport 1723 -j ACCEPT
# Accept GRE packets
/sbin/iptables -A INPUT -p 47 -j ACCEPT
/sbin/iptables -A OUTPUT -p 47 -j ACCEPT
# Enable IP forwarding
/sbin/iptables -F FORWARD
/sbin/iptables -A FORWARD -j ACCEPT
# Enable NAT for eth0 ? ppp* interfaces
/sbin/iptables -A POSTROUTING -t nat -o ppp+ -j MASQUERADE
/sbin/iptables -A POSTROUTING -t nat -o eth0 -j MASQUERADE
/bin/echo 1 > /proc/sys/net/ipv4/ip_forward
# Enable Local Networks
/sbin/iptables -A dynamic -s relay mailserver ips -j ACCEPT
/sbin/iptables -A dynamic -s local isp router network -j  ACCEPT
/sbin/iptables -A dynamic -s network behind the server -j ACCEPT
/sbin/iptables -A dynamic -s isp ip address -j ACCEPT
/sbin/iptables-save | /usr/bin/tee /etc/iptables.sav

After a time, cannot be specific, the server looses gateway connectivety, mostly within the hour, afer giving the command: /bin/echo 1 > /proc/sys/net/ipv4/ip_forward and or ping the local gateway, the server will trace the route to the internet again.
Within sysctl.conf: net.ipv4.ip_forward = 1 is enabled. The firewall is not blocking etc as the connection turns out fine in the beginning, or after the above commands.

Output: route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 eth0
10.5.5.0        0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.178.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0

---

### Post by darkod on 2016-01-08
Why are you doing the ip_forward with a script? Open /etc/sysctl.conf and configure it there, save and close the file, reboot. That makes it permanent.

For iptables, also there are better ways than running scripts. Put all rules in a file (just the rule, without the /sbin/iptables part) and load it at boot in /etc/network/interfaces. For example, in the stanza for the main eth0 you can load the rules by adding something like:
```
post-up iptables-restore < /path/iptables.rules
```

Now, if you have a reason doing it with a script, maybe running it multiple times a day, the above approach might not work for you.

But I have done it like this on many servers in the last few years and never even one has lost iptables rules or ip forwarding.

---

### Post by Seb_Boffen on 2016-01-08
The rules are based in /etc/network/if-up.d and in rc.local if the adapter ever bounces or the server restarts the rules are applied or are applied double.
But I'll appy your post-up to see if things change, situation was Always a bit unstable. But not in rules only regarding routing and ip forwarding, but nothing like this installation the only thing edit to this config is the vpn part, which should still not interfear with default routing and ip forward. In the mean while I've removed the /bin/echo 1 > /proc/sys/net/ipv4/ip_forward from the script rebooted and ended up with the same issue sysctl.conf does not control net.ipv4.ip_forward = 1, I expect the issue lies in the routes, although I have the situation up and running by running cron every minute with command /bin/echo 1 > /proc/sys/net/ipv4/ip_forward, this is very unpleasant for log entries and not 100% guaranteed to work, after the ping to the gateway the system finds its way,

---

### Post by Doug S on 2016-01-08
Darko,
I use a script for all this stuff also. There are just a few non-iptables commands that I want to keep track of under the same umbrella, and I find it easier, in terms of server configuration control, to have it all in a master script. I used to use iptables-restore. I do load mine via a pre-up directive in /etc/network/interfaces.

Seb_Boffen,
I don't currently have any input as to your issue. I think I'll have to re-read your posts a few times.

---

### Post by Seb_Boffen on 2016-01-08
yes no pobs tomorrow during the day time I will convert the siluation to post-up and see how the server keeps up, I've read about being able to put routes in tables but the how to did not work out

---

### Post by darkod on 2016-01-09
I know, using scripts should also work, especially if you need to run them not onlt on boot. But I would definitely take the ip_forward out of it, and do it in /etc/sysctl.conf. If the machine is a router, you need ip_forward enabled all the time anyway.

As for the iptables rules file, you set the chain policies, and then rules. I usually leave OUTPUT policy at ACCEPT, so it looks like this:
```
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]

-A INPUT -i ppp+ -j ACCEPT
-A INPUT -p tcp --dport 1723 -j ACCEPT
... ...

COMMIT

*nat

/nat rules here, PREROUTING and POSTROUTING /

COMMIT
```

If you set the OUTPUT policy to ACCEPT you don't need any OUTPUT rules of course. If you set it to drop you will need outgoing OUTPUT rule for each traffice type.

Also don't forget the traffic for local lo interface and for the related and established traffic. I see you have no such iptables rules. If INPUT is DROP you have to allow the returned traffic to enter. I usually do:
```
-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
```

Of course, if you set the FORWARD policy to ACCEPT no need for FORWARD specific rules too. If you set it to DROP you will have to allow your forwarding/routing traffic.

For your dynamic rules you will have to see how and where to implement them. I suppose they should go in the *filter section, depending what the rule is exactly.

Something like this should work good, especially if your rules are mostly fixed and static.

In your above file I don't see where you set INPUT to DROP. Don't forget that by default it's ACCEPT. Unless you change the policy, all is open anyway and you don't need any rules for INPUT too. And if the machine is on public IP you are leaving it open in a way... :)

First you need to set the INPUT, FORWARD and OUTPUT policies and then work with the rules. Don't forget to allow ssh port 22, otherwise you'll lock yourself out!!! I don't see such rule also, so I guess your input policy is actually accept. In which case you are not actually blocking anyway. If the machine is on private IP behind a firewall, that's still good. But in such case you don't need any blocking/allowing with iptables, just the part for forwarding (masquerade and such)...

---

### Post by Seb_Boffen on 2016-01-09
Hi thank you for the insight, at the moment I've taken out /bin/echo 1 > /proc/sys/net/ipv4/ip_forward for the script and the forward ability is now stable, other parts of connections is managed via shorewall firewall which was already running great together with fail2ban, both programs are running with the same blacklist. I now realize that running the forward command together with the setting sysctl.conf: net.ipv4.ip_forward = 1 at the same time resulted in the issues I faced.

---

