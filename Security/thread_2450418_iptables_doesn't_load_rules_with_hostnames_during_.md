---
title: "iptables doesn't load rules with hostnames during boot"
date: 2020-09-13
forum: Security
---

### Post by linusnilsson on 2020-09-13
Hi.

I just did a fresh install of Ubuntu Server 20.04.1 LTS to act as a gateway for my LAN. I already had a working iptables-script which I want to use. I confirmed that the ufw.service was disabled, did a copy of its systemd-file and modified it to run my iptables-script. This works, except all the iptables-rules that depend on resolving a dns. So the rules that contain a hostname instead of an IP address causes errors which results in those rules not getting loaded at all.

I suspect this is caused by the firewall getting loaded before my internet interface and dns settings are completely up and running. If I immediately login and run the script manually I get no errors and all the rules, including those containing hostnames, gets loaded properly.

What would be the best solution to this?

As of now, I have some ideas:
[LIST=1]
[*]Somehow delay the iptables-script from loading until all interfaces are up. The downside of this is that there will be a time when the internet interface is up and the firewall is not yet loaded, which I see as a security risk.
[*]Somehow split the firewall into two parts. Load the first part, including rules that doesn't depend on an internet connection/dns. Then wait for the internet interface to come up and load all dns-dependent rules.
[*]As most of the hostname-based rules are regulating access to services like ssh and openvpn, is there a way to make those rules load depending on the service? Like when openvpn starts, the rules regarding openvpn automatically gets loaded, and when it stops they get deleted? Is that somehow possible with iptables?
[/LIST]

There might be other/better solutions out there that I'm not aware of so I'd appreciate every suggestion :)

---

### Post by SeijiSensei on 2020-09-13
Put the hostnames in /etc/hosts or use IP addresses in the ruleset.

---

### Post by linusnilsson on 2020-09-13
I use hostnames because those hosts have dynamic ip addresses. If they had static ip addresses your suggestion would be a solution.

---

### Post by SeijiSensei on 2020-09-13
If the addresses change but remain within a defined IP subnet, you can use the subnet address instead.  For instance, if a set of hosts are all in 192.168.1.0/24, you could write rules permitting or blocking traffic from that range. For instance,
```
sudo iptables -A INPUT -p tcp -s 192.168.1.0/24 --dport 22
```
Most distributions load the iptables rules before anything else to protect the system from intrusion while it is loading its applications.

---

### Post by linusnilsson on 2020-09-13
I'm afraid I can't predict the address range as it is internet routable addresses. 

I might have found a better solution though. I used networkd-dispatcher to monitor the internet interface and when it comes up it loads the iptables-script. Kinda like the old if-up hook in */etc/network/interfaces*.

It actually solved a couple of more issues I had since it now reloads the firewall every time the internet interface comes up. This solution is also more dynamic.

For those who are interested in the details, what I did was:
[LIST]
[*]Verified that networkd-dispatcher was installed
[*]Created the file */etc/networkd-dispatcher/routable.d/50-ifup*
[*]Made sure 50-ifup is chown root:root and chmod 755 (executable)
[/LIST]
```
#!/bin/bash

if [ "$IFACE" == "enp1s0" ];
then
        su -c "/etc/rc.firewall";
fi
```
This script runs every time ANY interface reaches a routable status so it need to check if the interface is my internet interface (enp1s0). If yes, runs the script /etc/rc.firewall which loads the firewall.

I could also choose to load the firewall at boot as before, so it is up before the interface is up. Then I let networkd-dispatcher load just the dns-depending rules after the interface is up.

---

