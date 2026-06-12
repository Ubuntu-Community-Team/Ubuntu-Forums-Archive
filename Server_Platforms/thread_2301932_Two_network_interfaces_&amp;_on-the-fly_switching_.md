---
title: "Two network interfaces &amp; on-the-fly switching of internet gateway"
date: 2015-11-06
forum: Server Platforms
---

### Post by saku537 on 2015-11-06
Hello,

The network structure is as follows:
```

Interface p2p1:
address 172.16.131.5
netmask 255.255.255.0
gateway 172.16.131.1

Interface p3p1:
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1

Current routing table:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 p3p1
172.16.131.0    0.0.0.0         255.255.255.0   U     0      0        0 p2p1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 p3p1
```

I need help in order to manage to get it working as planned. The idea how it should work is as follows, when p3p1 looses it's link and internet access, switch to p2p1 interface and use it till the p3p1 is back up again. There's 3 Reverse AutoSSH tunnel(s) that needs to be up again after switching between interfaces. This full process needs to be automatic as possible.

The Reverse AutoSSH tunnel(s) has an unique port for monitoring for each of them. They are as follows: 10984,10985 and 10986. (as -M parameter in the AutoSSH command.)
Those tunnels has been setup via the /etc/rc.local file so it needs to be run again after internet connectivity is restored by either of those interfaces.

Please help me to get this working as planned. There would hopefully be an fail over in case there's no internet connectivity at all so it needs to wait till it detects an internet connection again and then resumes operation. What's the best approach in doing this?

Thanks for your help in advance. :)

P.S Original topic is located [here]("http://forum.ubuntu-fi.org/index.php?topic=49647.msg380395#msg380395"). (In Finnish.)

---

### Post by tgalati4 on 2015-11-06
*network-manager* is not installed on servers typically, but it could be used to auto switch between active network connections.  As for reconnecting your ssh sessions, that would need some fancy scripting. 

[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

An alternative is to bond the 2 interfaces:  [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

---

### Post by saku537 on 2015-11-06
> **tgalati4 said:**
> *network-manager* is not installed on servers typically, but it could be used to auto swich between active network connections.  As for reconnecting your ssh sessions, that would need some fancy scripting. 

[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

An alternative is to bond the 2 interfaces:  [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

You are correct that network-manager is not installed and I would not like to as there's no GUI present unless you count CLI as one.

How does the boding work? I'm unsure if that's a good practice to use in this as there are two different IP subnet's in use here.

I have managed to get some kind of a script to handle the ssh sessions already, but needs a lot of tweaking. I would just need an easy way to implement an checker for internet connectivity and if no internet is detected, pause ssh sessions. After internet connectivity is restored, re-establish the SSH Tunnels.

Thank you for your help and quick reply.

---

### Post by darkod on 2015-11-06
Bonding wouldn't help you since you correctly noticed you are talking about two different subnets. Bonding is "virtual joining" of two or more network adapters to gain high availability and/or speed. If one adapter fails the rest continue working as normal. But the bond acts as single device and as such will have single IP/subnet configured on it.

Except lots of scripting, I don't see a way to do this easily... What you are trying to do looks like "HA cluster in reverse". You are not trying to do HA cluster on server end, instead you work on client end and you want to switch gateways dynamically...

---

### Post by saku537 on 2015-11-06
> **darkod said:**
> Bonding wouldn't help you since you correctly noticed you are talking about two different subnets. Bonding is "virtual joining" of two or more network adapters to gain high availability and/or speed. If one adapter fails the rest continue working as normal. But the bond acts as single device and as such will have single IP/subnet configured on it.

Except lots of scripting, I don't see a way to do this easily... What you are trying to do looks like "HA cluster in reverse". You are not trying to do HA cluster on server end, instead you work on client end and you want to switch gateways dynamically...

Let me tell you some background for the need of this. I'm living in a student dormitory which has pretty rogue firewall and security policy so we cannot forward ports without the use of Reverse SSH Tunnel(s) at all. The 192.168.1.* subnet is an 4G connection which gets turned off every Friday over the weekend by me and it's prepaid so it might not always have internet. The 172.16.131.* subnet is the student dormitory internal network which has the rogue firewall, but still needs to be default route over the weekend in order for the tunnels to reach the server outside. The problem also is that the school internal network's internet access is blocked from midnight to 6.00 AM, but that's a totally different problem. This is why it should have an pause in connections between midnight and 6.00 AM and when internet is back online, resume connections A.K.A re-establish the tunnels.

What do you think would be the best solution to manage this kind of a setup? Fail over switch perhaps?

---

### Post by tgalati4 on 2015-11-06
Perhaps draw a diagram with your network topology, I confused, can't you simply get your own dedicated internet connection and not rely on the dorm's connection?  Where is your server located?  Where are you physically located when trying to access your server?

---

### Post by SeijiSensei on 2015-11-07
I think you can use "metrics" in the route command to accomplish this or the advanced features in the iproute package.

[http://www.tldp.org/LDP/nag2/x-087-2-issues.routing.html](http://www.tldp.org/LDP/nag2/x-087-2-issues.routing.html)

[http://www.rjsystems.nl/en/2100-adv-routing.php](http://www.rjsystems.nl/en/2100-adv-routing.php)

---

### Post by saku537 on 2015-11-07
> **tgalati4 said:**
> Perhaps draw a diagram with your network topology, I confused, can't you simply get your own dedicated internet connection and not rely on the dorm's connection?  Where is your server located?  Where are you physically located when trying to access your server?

 Dorn Internet -----> Rogue Firewall (172.16.131.1) -----> Switch ----> Server (172.16.131.5)
 4G Internet -------> 4G Modem (192.168.1.1) ----> Switch ----> Server (192.168.1.3)
 Tunnel Endpoint is located in a datacenter outside of these networks.
Incoming traffic is blocked on both, unless it's though the Reverse SSH Tunnel.

[ATTACH=CONFIG]265401[/ATTACH]


I cannot get an dedicated line as the server is in the dormitory. 4G/LTE is as close to direct line that's possible.
I can be either in a train or home (not in the dormitory) when I'm trying to access it. The access works though the server in the datacenter due to the Reverse SSH Tunnels in place.
The dorn connection is 100/100 Mbps fiber optic link....

> **SeijiSensei said:**
> I think you can use "metrics" in the route  command to accomplish this or the advanced features in the iproute  package.

[http://www.tldp.org/LDP/nag2/x-087-2-issues.routing.html](http://www.tldp.org/LDP/nag2/x-087-2-issues.routing.html)

[http://www.rjsystems.nl/en/2100-adv-routing.php](http://www.rjsystems.nl/en/2100-adv-routing.php)


The "metrics" thing might work, but I still need an way to re-establish the tunnels if the internet access is lost automatically.

---

### Post by SeijiSensei on 2015-11-07
> **saku537 said:**
> The "metrics" thing might work, but I still need an way to re-establish the tunnels if the internet access is lost automatically.
Run a command via cron to check the connection via ping and restart the tunnels when needed.  In /etc/crontab add a line 
```
* * * * * root /usr/local/sbin/check_tunnels
```
which runs the command once each minute.  Then create /usr/local/sbin/check_tunnels with code along these lines:
```

#!/bin/sh

CHECK=$(ping -c5 8.8.8.8 | grep '100% packet loss')

if [ "$CHECK" != "" ]
then
     # tunnel is down 
     run some command(s) here to restart tunnels
     echo "$(date +%c) - restarted tunnels" >> /var/log/tunnel_check.log
fi

exit 0

```
Mark the script executable, take the tunnels down manually, and run the script to make sure it restarts them correctly.

---

### Post by tgalati4 on 2015-11-07
Since you know the down times, you can simply schedule *cron* to use the *check_tunnels* during the down periods.  You can also use a 15-min check interval, and access your server at those 15-min intervals.  Otherwise, the ping check may get shut down due to firewall policy.

Port-knocking would be helpful in this situation, but since you don't have policy control of the Rogue Firewall, then that option is not available.

---

### Post by saku537 on 2015-11-07
> **SeijiSensei said:**
> Run a command via cron to check the connection via ping and restart the tunnels when needed.  In /etc/crontab add a line 
```
* * * * * root /usr/local/sbin/check_tunnels
```
which runs the command once each minute.  Then create /usr/local/sbin/check_tunnels with code along these lines:
```

#!/bin/sh

CHECK=$(ping -c5 8.8.8.8 | grep '100% packet loss')

if [ "$CHECK" != "" ]
then
     # tunnel is down 
     run some command(s) here to restart tunnels
     echo "$(date +%c) - restarted tunnels" >> /var/log/tunnel_check.log
fi

exit 0

```
Mark the script executable, take the tunnels down manually, and run the script to make sure it restarts them correctly.

Thank you for the script example. :)
Can I have two default routes, but just specify with metrics value which one is primary?

---

### Post by SeijiSensei on 2015-11-07
> **saku537 said:**
> Can I have two default routes, but just specify with metrics value which one is primary?
Yes, I believe so, but I hardly ever do anything like that, so I recommend reading some documentation.

And if you do have some idea when to run the checks, then I agree with tgalati that you should only schedule the cron job to run in those periods.

---

### Post by saku537 on 2015-11-08
> **tgalati4 said:**
> Since you know the down times, you can simply schedule *cron* to use the *check_tunnels* during the down periods.  You can also use a 15-min check interval, and access your server at those 15-min intervals.  Otherwise, the ping check may get shut down due to firewall policy.

Port-knocking would be helpful in this situation, but since you don't have policy control of the Rogue Firewall, then that option is not available.

In those periods when internet connectivity is lost on p3p1?

> **SeijiSensei said:**
> Yes, I believe so, but I hardly ever do anything like that, so I recommend reading some documentation.

And if you do have some idea when to run the checks, then I agree with tgalati that you should only schedule the cron job to run in those periods.

Do you mean that I should check the documentation for metrics?

P.S Thanks everyone for the help already, it's really appreciated. (:

---

### Post by SeijiSensei on 2015-11-08
> **saku537 said:**
> Do you mean that I should check the documentation for metrics?
That, and maybe acquaint yourself with routing generally if you've never dealt with this stuff much before.  The first link I gave you covers the concepts.

---

### Post by saku537 on 2015-11-08
> **SeijiSensei said:**
> That, and maybe acquaint yourself with routing generally if you've never dealt with this stuff much before.  The first link I gave you covers the concepts.

Alright. We will need to see next weekend what happens as I think that this setup should work.

route -n:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    1      0        0 p3p1
0.0.0.0         172.16.131.1    0.0.0.0         UG    2      0        0 p2p1
172.16.131.0    0.0.0.0         255.255.255.0   U     0      0        0 p2p1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 p3p1

```

/etc/network/interfaces:
```

# The primary network interface / 4G Connection
auto p3p1
iface p3p1 inet dhcp
        metric 1

# The secondary network interface / School Network
auto p2p1
iface p2p1 inet dhcp
        metric 2

```

---

### Post by SeijiSensei on 2015-11-08
That's my understanding of how it works as well.  Come back and let us know.

---

### Post by saku537 on 2015-11-15
> **SeijiSensei said:**
> That's my understanding of how it works as well.  Come back and let us know.

Alright, it didin't work as planned.

I need to figure out an script to check if there's internet connection available at all over the weekend. Preferred to have multiple checks via TCP/UDP and ICMP

/var/log/tunnel_check.log:
```

Thu 12 Nov 2015 09:38:14 PM EET - Tunnels are OK, not restarting.
Fri 13 Nov 2015 11:30:07 AM EET - Tunnels are down, restarting.
Sat 14 Nov 2015 06:30:15 AM EET - Tunnels are down, restarting.
Sun 15 Nov 2015 06:30:15 AM EET - Tunnels are down, restarting.

```

/usr/local/sbin/check_tunnels:
```

#!/bin/sh

CHECK=$(ping -c5 8.8.8.8 | grep '100% packet loss')

if [ "$CHECK" != "" ]
        then
                # Tunnel is down
                /usr/bin/killall autossh
                /bin/sh /usr/local/sbin/tunnel_startup
                echo "$(date +%c) - Tunnels are down, restarting." >> /var/log/tunnel_check.log
        else
                # Tunnel is up
                echo "$(date +%c) - Tunnels are OK, not restarting." >> /var/log/tunnel_check.log

fi

exit 0

```

EDIT: It works as I want it to. The problem was fixed by letting the router do the Dual-WAN functions.

Tunnel check log:
```

Mon 09 Nov 2015 12:30:20 AM EET - Tunnels are OK.
Mon 09 Nov 2015 12:33:30 AM EET - Tunnels are OK, not restarting.
Mon 09 Nov 2015 02:15:31 AM EET - Tunnels are OK, not restarting.
Thu 12 Nov 2015 09:38:14 PM EET - Tunnels are OK, not restarting.
Fri 13 Nov 2015 11:30:07 AM EET - Tunnels are down, restarting.
Sat 14 Nov 2015 06:30:15 AM EET - Tunnels are down, restarting.
Sun 15 Nov 2015 06:30:15 AM EET - Tunnels are down, restarting.
Sun 15 Nov 2015 10:19:02 PM EET - Tunnels are down, restarting.
Sun 15 Nov 2015 10:40:30 PM EET - Tunnels are OK, not restarting.
Fri 20 Nov 2015 11:30:10 AM EET - Tunnels are OK, not restarting.
Sat 21 Nov 2015 06:30:11 AM EET - Tunnels are OK, not restarting.
Sun 22 Nov 2015 06:30:11 AM EET - Tunnels are OK, not restarting.
Fri 27 Nov 2015 11:30:06 AM EET - Tunnels are OK, not restarting.
Sat 28 Nov 2015 06:30:06 AM EET - Tunnels are OK, not restarting.
Sun 29 Nov 2015 06:30:06 AM EET - Tunnels are OK, not restarting.
Fri 04 Dec 2015 11:30:12 AM EET - Tunnels are OK, not restarting.
Sat 05 Dec 2015 06:30:12 AM EET - Tunnels are OK, not restarting.
Sun 06 Dec 2015 06:30:11 AM EET - Tunnels are OK, not restarting.

```

---

