---
title: "iptables and ufw"
date: 2009-08-26
forum: Server Platforms
---

### Post by dragos2 on 2009-08-26
I disabled ufw and I am using now only these rules that I need in order to provide
Internet access to/from a openvz container.

```

iptables -t nat -A PREROUTING -p tcp -d 193.19.x.y --dport port_num -i eth0 -j DNAT --to-destination 192.168.1.1:80 
iptables -t nat -A POSTROUTING -s 192.168.2.1.1 -o eth0 -j SNAT --to 193.19.x.y

```

Can I still use ufw and keeping the above iptables rules ?

---

### Post by cdenley on 2009-08-26
UFW doesn't seem to touch the nat table, so those rules should be safe. You can add these lines to /etc/ufw/before.rules to make those persistent.
```

*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
-F PREROUTING
-F POSTROUTING
-A PREROUTING -d 193.19.x.y -i eth0 -p tcp -m tcp --dport port_num -j DNAT --to-destination 192.168.1.1:80
-A POSTROUTING -s 192.168.2.1 -o eth0 -j SNAT --to-source 193.19.x.y
COMMIT

```

---

### Post by dragos2 on 2009-08-27
> **cdenley said:**
> UFW doesn't seem to touch the nat table, so those rules should be safe. You can add these lines to /etc/ufw/before.rules to make those persistent.
```

*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
-F PREROUTING
-F POSTROUTING
-A PREROUTING -d 193.19.x.y -i eth0 -p tcp -m tcp --dport port_num -j DNAT --to-destination 192.168.1.1:80
-A POSTROUTING -s 192.168.2.1 -o eth0 -j SNAT --to-source 193.19.x.y
COMMIT

```

It doesnt seem to work, after I enable ufw I can access the webserver from
the container. Any ideas why ?

```

root@deb01:~# cat /etc/ufw/before.rules
#
# rules.before
#
# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-before-input
#   ufw-before-output
#   ufw-before-forward
#

# Don't delete these required lines, otherwise there will be errors
*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
# End required lines


# allow all on loopback
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-output -i lo -j ACCEPT

# connection tracking rules
-A ufw-before-input -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT

# drop INVALID packets
# uncomment to log INVALID packets
#-A ufw-before-input -m conntrack --ctstate INVALID -j LOG --log-prefix "[UFW BLOCK INVALID]: "
-A ufw-before-input -m conntrack --ctstate INVALID -j DROP

# connection tracking for outbound
-A ufw-before-output -p tcp -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
-A ufw-before-output -p udp -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

# allow dhcp client to work
-A ufw-before-input -p udp --sport 67 --dport 68 -j ACCEPT

#
# ufw-not-local
#
-A ufw-before-input -j ufw-not-local

# if LOCAL, RETURN
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN

# if MULTICAST, RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN

# if BROADCAST, RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN

-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK NOT-TO-ME]: "

# all other non-local packets are dropped
-A ufw-not-local -j DROP

# allow MULTICAST, be sure the MULTICAST line above is uncommented
-A ufw-before-input -s 224.0.0.0/4 -j ACCEPT
-A ufw-before-input -d 224.0.0.0/4 -j ACCEPT


*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
-F PREROUTING
-F POSTROUTING
-A PREROUTING -d 193.19.x.y -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.1.1:80
-A POSTROUTING -s 192.168.1.1 -o eth1 -j SNAT --to-source 193.19.x.y


# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT

```

x.y are numbers in the above script.

---

### Post by cdenley on 2009-08-27
Are those 2 rules deleted when you enable ufw, or do they not work as you expect them to? Do they work before you enable ufw?
```

sudo iptables -t nat -L -n

```

---

### Post by dragos2 on 2009-08-27
> **cdenley said:**
> Are those 2 rules deleted when you enable ufw, or do they not work as you expect them to? Do they work before you enable ufw?
```

sudo iptables -t nat -L -n

```

The rules work if ufw is disabled. If I enable ufw then I can't access my webserver from
outside(Internet).

This is the output:

```

root@deb01:~# iptables -t nat -L -n
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
DNAT       tcp  --  0.0.0.0/0            193.19.x.y       tcp dpt:80 to:192.168.1.1:80

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
SNAT       all  --  192.168.1.1          0.0.0.0/0           to:193.19.x.y

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
root@deb01:~# ufw status
Firewall not loaded

```

---

### Post by cdenley on 2009-08-27
```

sudo ufw enable
sudo iptables -t nat -L -n

```
What is the web server? Where is the ubuntu computer between the internet and the web server?

---

### Post by dragos2 on 2009-08-28
> **cdenley said:**
> ```

sudo ufw enable
sudo iptables -t nat -L -n

```What is the web server? Where is the ubuntu computer between the internet and the web server?

There ubuntu computer/server is directly visible from the internet and has a public IP
assigned. I installed OpenVZ on it and then run another ubuntu server on top
of the already existing computer and inside that I am running a webserver.

This is a drawing (borrowed from here [http://www.cyberciti.biz/faq/centos-rhel-linux-openvz-hardware-node-iptables-firewall/](http://www.cyberciti.biz/faq/centos-rhel-linux-openvz-hardware-node-iptables-firewall/))
```

Router
   \\
     \\
Hardware Node - eth0
            //
           //
        venet0
+----------+------------+
|           |           |
vps1      vps2           vps3


```

But my problem is how can I make ufw coexist with the iptables rules that are needed
in order to provide my vps with internet ?

---

### Post by cdenley on 2009-08-28
> **dragos2 said:**
> 
But my problem is how can I make ufw coexist with the iptables rules that are needed in order to provide my vps with internet ?

Well, you haven't run the command I suggested, so we have yet to determine whether or not the rules do coexist. I suspect the rules are in there, but UFW sets the default action for the FORWARD chain to DROP, so nothing will ever be routed.

---

### Post by dragos2 on 2009-08-28
> **cdenley said:**
> Well, you haven't run the command I suggested, so we have yet to determine whether or not the rules do coexist. I suspect the rules are in there, but UFW sets the default action for the FORWARD chain to DROP, so nothing will ever be routed.

```

root@deb01:~# sudo ufw enable
Firewall started and enabled on system startup
root@deb01:~# sudo iptables -t nat -L -n
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
DNAT       tcp  --  0.0.0.0/0            193.19.x.y       tcp dpt:80 to:192.1                   68.1.1:80

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
SNAT       all  --  192.168.1.1          0.0.0.0/0           to:193.19.x.y

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

Does it helps ?

---

### Post by cdenley on 2009-08-28
Yes. The two rules you needed are loaded along with UFW. Now, I suspect you need to fix the FORWARD chain.
```

sudo iptables -L FORWARD -n

```

---

### Post by dragos2 on 2009-08-31
> **cdenley said:**
> Yes. The two rules you needed are loaded along with UFW. Now, I suspect you need to fix the FORWARD chain.
```

sudo iptables -L FORWARD -n

```

```

root@deb01:~# ufw enable
Firewall started and enabled on system startup
root@deb01:~# iptables -L FORWARD -n
Chain FORWARD (policy DROP)
target     prot opt source               destination
ufw-before-forward  all  --  0.0.0.0/0            0.0.0.0/0
ufw-after-forward  all  --  0.0.0.0/0            0.0.0.0/0

```

Good or bad ?

---

### Post by cdenley on 2009-08-31
The default policy is "drop" and there are no rules to accept, so unless a rule matches in either the ufw-before-forward or ufw-after-forward chain to accept it, no packets will be forwarded (routed, DNAT'ed).

---

### Post by dragos2 on 2009-09-01
> **cdenley said:**
> The default policy is "drop" and there are no rules to accept, so unless a rule matches in either the ufw-before-forward or ufw-after-forward chain to accept it, no packets will be forwarded (routed, DNAT'ed).

Hmm, then why your solution involving ufw-bofore-forward did not worked ?

---

### Post by dragos2 on 2009-09-01
What I want to achieve is

-having only these NAT rules using iptables
```

#vps1
iptables -t nat -A PREROUTING -p tcp -d 193.19.x.y  --dport 80 -i eth1 -j DNAT --to-destination 192.168.1.1:80 
iptables -t nat -A POSTROUTING -s 192.168.1.1 -o eth1 -j SNAT --to 193.19.176.28


#vps2
iptables -t nat -A POSTROUTING -s 192.168.2.1 -o eth1 -j SNAT --to 193.19.x.y
iptables -t nat -A PREROUTING -p tcp -d 193.19.x.y  --dport 1000 -i eth1 -j DNAT --to-destination 192.168.2.1:1000

iptables -t nat -A PREROUTING -p tcp -d 193.19.x.y  --dport 137 -i eth1 -j DNAT --to-destination 192.168.2.1:137
iptables -t nat -A PREROUTING -p tcp -d 193.19.x.y  --dport 138 -i eth1 -j DNAT --to-destination 192.168.2.1:138
iptables -t nat -A PREROUTING -p tcp -d 193.19.x.y  --dport 139 -i eth1 -j DNAT --to-destination 192.168.2.1:139
iptables -t nat -A PREROUTING -p tcp -d 193.19.x.y  --dport 445 -i eth1 -j DNAT --to-destination 192.168.2.1:445

```

And then to be able for the main hardware node to use ufw and set rules
that affects only the hardware node.

cdenley can you please help me with a working solution ?

---

### Post by cdenley on 2009-09-01
> **dragos2 said:**
> Hmm, then why your solution involving ufw-bofore-forward did not worked ?
What solution was that? I don't recall giving any specific rules for any forward chain, though you will need some if you expect any packets to be forwarded with a default action to drop them. I guess you could add this line to after.rules before "COMMIT".
```

-A ufw-after-forward -j ACCEPT

```
This, I believe, would cause any FORWARD packets to be accepted. I suppose you could add it to before.rules instead, just make sure you add it before the first, original "COMMIT", and replace "after" with "before".

As I said before, regardless of the rules in your nat table, no packet will be forwarded until it is accepted in the FORWARD chain.

---

