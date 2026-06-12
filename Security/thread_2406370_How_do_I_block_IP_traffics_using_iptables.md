---
title: "How do I block IP traffics using iptables?"
date: 2018-11-20
forum: Security
---

### Post by ktopa1980 on 2018-11-20
I need to block IP traffics from a certain country. I know I can export a free IP address list from [IP2Location firewall generator]("https://www.ip2location.com/free/visitor-blocker"). The sample output file for iptables format is as below.

What should I do next to block the list of IP address using iptables? I don't want to run the command line by line.

```

# -------------------------------------------------------
# Free IP2Location Firewall List by Country
# Source: https://www.ip2location.com/free/visitor-blocker
# Last Generated: 20 Nov 2018 05:20:36 GMT
# [Important] Please update this list every month
# -------------------------------------------------------
iptables -A INPUT -s 217.29.232.0/21 -j DROP
iptables -A INPUT -s 194.112.14.0/24 -j DROP
iptables -A INPUT -s 194.112.13.128/25 -j DROP
iptables -A INPUT -s 194.112.13.64/26 -j DROP
```

---

### Post by wildmanne39 on 2018-11-20
*Thread moved to **Security for a more appropriate fit**.*

---

### Post by HermanAB on 2018-11-20
```
$ sudo  iptables -I INPUT -s 192.168.1.2 -j DROP
```

The -I stuffs the rule in front of the existing rules.  It doesn't help adding it to the end of the list.

The -s is the source address that you want to block.

The -j drops the packet on the floor.

---

### Post by ktopa1980 on 2018-11-20
Do I need to run it for all the lines? Can I make a shell script to load it using one line?

---

### Post by The Cog on 2018-11-20
You need to run each line as a separate command. 
But you can put all the lines into a script and just run the script.

Or, once you are happy with the commands that you have entered, and that iptables is configured as you want, you can save that configuration. The command ```
sudo iptables-save
``` will output a full configuration to the screen for you to inspect or save to a file. You can have these rules automatically restored when you boot: [https://askubuntu.com/questions/119393/how-to-save-rules-of-the-iptables](https://askubuntu.com/questions/119393/how-to-save-rules-of-the-iptables)

---

### Post by HermanAB on 2018-11-20
Note that the "-A INPUT" will add the line at the end of the list of rules, which may not work, unless there are no rules at all to begin with.  

Iptables processes rules in a 'top down' fashion, so it is best to put drop rules at the top, with "-I INPUT", so that they will execute immediately.  A packet that was accepted by another rule, will not get to the end of the list.

---

### Post by The Cog on 2018-11-20
Another point: 
If you have already entered iptables rules by enabling ufw then you need to decide whether to go with iptables or with ufw. Do not try to mix the automated iptables rules created by ufw (or gufw of course) with manual iptables rules. If you are using ufw then I think adding those blocking rules to the ufw rules is probably easier than converting it all to manually maintained iptables rules and stopping using ufw.

---

### Post by TheFu on 2018-11-20
Check out **ipset** if you need to load thousands of rules.  [https://www.linuxjournal.com/content/advanced-firewall-configurations-ipset](https://www.linuxjournal.com/content/advanced-firewall-configurations-ipset)

But for most people using the iptables-save/-restore commands would be easier.

I'm blocking over 8500 subnets from known attackers.

+1 on not mixing firewall management tools. Use either iptables OR use ufw.  Not both.

---

### Post by cheese66 on 2018-11-20
> **TheFu said:**
> 
I'm blocking over 8500 subnets from known attackers.


Interesting. :)
Any location where I would get such list?

---

### Post by TheFu on 2018-11-20
Setup a honey pot and script the list creation based on the attacking IPs logged.

Locations attacking your business are unlikely to be attacking ours and many subnets that we are willing to block due to the nature of our business, you may not be willing.  For example, all of amazon EC2 is blocked.

You might find that starting with lists available from the pi-hole project is helpful.  We did not because it includes the wrong sort of things.

---

### Post by ktopa1980 on 2018-11-20
Thank you. I will block it manually and then export the configuration for future usage.

---

### Post by Doug S on 2018-11-21
For what its worth, I don't bother with iptables-save anymore, and have never used iptables-persitant (or whatever its called) . I just have a script that loads during boot. It also flushes all chains, such that it can be executed anytime I want. I get it to load during boot via the /etc/network/interfaces file like so (works on 16.04, but won't work on 18.04 with netplan)(observe the pre-up line):

```
# interfaces file for smythies.com 2016.01.30
#       attempt to set local DNS herein, as the method
#       used with the old 12.04 server no longer works.
#
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
[COLOR="#FF0000"]pre-up /home/doug/init/doug_firewall[/COLOR]
dns-nameservers 127.0.0.1

# The primary interface (d-link PCI card)
auto enp4s0
iface enp4s0 inet dhcp

# Local network interface (uses built in ethernet port)
auto enp2s0
iface enp2s0 inet static
  address 192.168.111.1
  network 192.168.111.0
  netmask 255.255.255.0
  broadcast 192.168.111.255

```I have built up my IP block list over a period of years. Similar to TheFu, what works for me might not work for others. If I observe some bad guy just switching to another IP address once blocked, I'll look up the entire sub-net and block the whole thing. I don't care about collateral damage. Here is a heavily edited excerpt from my currently running router/firewall:

```
Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
  886183 211667177 ACCEPT     all  --  enp4s0 *       0.0.0.0/0            XXX.YYY.ZZ.W         state RELATED,ESTABLISHED
    8405   341152 DROP       all  --  enp4s0 *       5.188.0.0/16         0.0.0.0/0
    2760   165600 DROP       all  --  enp4s0 *       220.242.0.0/15       0.0.0.0/0
    2601  1366386 DROP       all  --  enp4s0 *       37.49.0.0/16         0.0.0.0/0
    4695   187800 DROP       all  --  enp4s0 *       46.161.0.0/16        0.0.0.0/0
    3895   156096 DROP       all  --  enp4s0 *       77.72.80.0/21        0.0.0.0/0
   36656  1466360 DROP       all  --  enp4s0 *       78.128.0.0/17        0.0.0.0/0
    2083    83324 DROP       all  --  enp4s0 *       79.124.0.0/18        0.0.0.0/0
    3857   163034 DROP       all  --  enp4s0 *       80.64.0.0/10         0.0.0.0/0
    3566   146392 DROP       all  --  enp4s0 *       89.248.160.0/20      0.0.0.0/0
    8356   339352 DROP       all  --  enp4s0 *       94.102.48.0/20       0.0.0.0/0
    1969    91199 DROP       all  --  enp4s0 *       103.0.0.0/8          0.0.0.0/0
    1087    44120 DROP       all  --  enp4s0 *       109.248.9.0/24       0.0.0.0/0
    1058    51790 DROP       all  --  enp4s0 *       122.224.0.0/12       0.0.0.0/0
    3659   167320 DROP       all  --  enp4s0 *       123.112.0.0/12       0.0.0.0/0
    1839    88272 DROP       all  --  enp4s0 *       149.56.180.252/30    0.0.0.0/0
   33994  1359764 DROP       all  --  enp4s0 *       176.119.0.0/16       0.0.0.0/0
   17489   784863 DROP       all  --  enp4s0 *       185.0.0.0/8          0.0.0.0/0
    5336   213488 DROP       all  --  enp4s0 *       193.106.24.0/21      0.0.0.0/0
    6736   270736 DROP       all  --  enp4s0 *       205.206.120.226/31   0.0.0.0/0
    2824   136704 DROP       all  --  enp4s0 *       220.160.0.0/11       0.0.0.0/0

```

---

