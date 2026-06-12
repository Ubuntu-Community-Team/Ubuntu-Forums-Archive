---
title: "iptables openvpn killswitch"
date: 2018-08-23
forum: Server Platforms
---

### Post by Wojciech_Marusiak on 2018-08-23
Hi guys, 

I have 18.04 Ubuntu Server connecting as VPN client to VPN provider.

I have the following setup:

**Network interfaces**
```

eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.25.18.24  netmask 255.255.240.0  broadcast 172.25.31.255


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0   


tun0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1500
        inet 10.100.200.168  netmask 255.255.252.0  destination 10.100.200.168

```

**iptables script**
```

#!/bin/bash
# Flush
iptables -t nat -F
iptables -t mangle -F
iptables -F
iptables -X


# allow Localhost
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT


# Make sure you can communicate with any DHCP server
iptables -A OUTPUT -d 255.255.255.255 -j ACCEPT
iptables -A INPUT -s 255.255.255.255 -j ACCEPT


# Make sure that you can communicate within your own network
iptables -A INPUT -s 172.16.0.0/12 -d 172.16.0.0/12 -j ACCEPT
iptables -A OUTPUT -s 172.16.0.0/12 -d 172.16.0.0/12 -j ACCEPT


# Allow established sessions to receive traffic:
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT


# Allow TUN
iptables -A INPUT -i tun+ -j ACCEPT
iptables -A FORWARD -i tun+ -j ACCEPT
iptables -A OUTPUT -o tun+ -j ACCEPT


# allow VPN connection
iptables -I OUTPUT 1 -p udp --destination-port 993 -m comment --comment "Allow VPN connection" -j ACCEPT


# allow SSH connection
iptables -I OUTPUT 1 -p udp --destination-port 1010 -m comment --comment "Allow SSH connection" -j ACCEPT


# allow HTTPS connection
iptables -I OUTPUT 1 -p udp --destination-port 443 -m comment --comment "Allow HTTPS connection" -j ACCEPT


# Block All
iptables -A OUTPUT -j DROP
iptables -A INPUT -j DROP
iptables -A FORWARD -j DROP


# Log all dropped packages, debug only.


iptables -N logging
iptables -A INPUT -j logging
iptables -A OUTPUT -j logging
iptables -A logging -m limit --limit 2/min -j LOG --log-prefix "IPTables general: " --log-level 7
iptables -A logging -j DROP


echo "saving"


iptables-save > /etc/iptables.rules


echo "done"

```
[B]
Client VPN config[/B]
```

client
dev tun
remote 10.10.10.10 1010
proto tcp-client
remote-cert-tls server
auth-user-pass
tls-client
pull
auth SHA1
cipher AES-256-CBC
persist-key
resolv-retry infinite
reneg-sec 0
verb 1
#script-security 2 system
auth-nocache
route-delay 2
redirect-gateway def1
auth-user-pass 
log-append /var/log/openvpn.log

```

Once I enable iptables VPN can't connect anymore. Can someone point where I did mistake?

---

### Post by darkod on 2018-08-23
I think what you are missing is to allow FORWARD for traffic going out over tun0 too, not just coming in. And the masquerade rule for traffic in tun0.

```
iptables -A FORWARD -o tun+ -j ACCEPT
iptables -t nat -A POSTROUTING -o tun+ -j MASQUERADE
```

I think you are overdoing it... The server is already on private IP unroutable over the internet. Nothing can reach it unless you forward traffic to it yourself. You don't need so strict iptables protection. As you can see, it is very easy to block valid traffic if you make iptables too strict.

For example I never saw any use of OUTPUT -j DROP. Why would you drop traffic originating from your server? Is it invalid traffic? For someone to issue invalid traffic originating from your server that means he already has access to it. In which case you have bigger problems and iptables won't help you much IMHO...

---

### Post by Wojciech_Marusiak on 2018-08-23
I added your suggestions. VPN still can't establish connectivity.

[IMG]https://i.imgur.com/3xG5BYO.jpg[/IMG]

[IMG]https://i.imgur.com/H0Yyrbk.jpg[/IMG]

---

### Post by darkod on 2018-08-23
Your protocol is set to tcp-client in the config and you are allowing udp/993 in iptables. You can see in the log it is trying to establish TCP connection, so it gets blocked and fails.

---

### Post by Wojciech_Marusiak on 2018-08-23
Perfect. It works!

Thanks a lot.

Just one question. From where does tose line come from?
[IMG]https://i.imgur.com/eGNVBwQ.jpg[/IMG]

---

### Post by darkod on 2018-08-23
Just follow the rules, they are in order... :)

The first looks to be the lo ACCEPT (loopback int).

The other two the FORWARD -i and -o for tun+.

---

### Post by Doug S on 2018-08-23
You are using a method for displaying your iptables rule set that does not tell the whole story. In particular, the possible interface limitations. If you use this:

```
sudo iptables -v -x -n -L
```instead, it should become clearer. Example:

```
doug@s17:~$ [COLOR="#FF0000"]sudo iptables -A INPUT -i lo -j ACCEPT[/COLOR]
doug@s17:~$ [COLOR="#FF0000"]sudo iptables -L[/COLOR]
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
[COLOR="#FF0000"]ACCEPT     all  --  anywhere             anywhere
[/COLOR]
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


```

```
$ [COLOR="#FF0000"]sudo iptables -v -x -n -L[/COLOR]
Chain INPUT (policy ACCEPT 93 packets, 6732 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       [COLOR="#FF0000"]0        0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0[/COLOR]

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 53 packets, 7100 bytes)
    pkts      bytes target     prot opt in     out     source               destination
```

EDIT: I took so long writing this, that Darko answered already.

---

### Post by Wojciech_Marusiak on 2018-08-23
Thanks. Indeed better overview.

---

### Post by Wojciech_Marusiak on 2018-08-23
Guys it is me again.

Looks like there is still some misconfiguration here.

```

#!/bin/bash
# Flush
iptables -t nat -F
iptables -t mangle -F
iptables -F
iptables -X


# allow Localhost
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT


# Make sure you can communicate with any DHCP server
iptables -A OUTPUT -d 255.255.255.255 -j ACCEPT
iptables -A INPUT -s 255.255.255.255 -j ACCEPT


# Make sure that you can communicate within your own network
iptables -A INPUT -s 172.16.0.0/12 -d 172.16.0.0/12 -j ACCEPT
iptables -A OUTPUT -s 172.16.0.0/12 -d 172.16.0.0/12 -j ACCEPT


# Allow established sessions to receive traffic:
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT


# Allow TUN
iptables -A INPUT -i tun+ -j ACCEPT
iptables -A FORWARD -i tun+ -j ACCEPT
iptables -A FORWARD -o tun+ -j ACCEPT
iptables -t nat -A POSTROUTING -o tun+ -j MASQUERADE
iptables -A OUTPUT -o tun+ -j ACCEPT


# allow VPN connection
iptables -I OUTPUT 1 -p tcp --destination-port 993 -m comment --comment "Allow VPN connection" -j ACCEPT


# Block All
iptables -A OUTPUT -j DROP
iptables -A INPUT -j DROP
iptables -A FORWARD -j ACCEPT


# Log all dropped packages, debug only.


iptables -N logging
iptables -A INPUT -j logging
iptables -A OUTPUT -j logging
iptables -A logging -m limit --limit 2/min -j LOG --log-prefix "IPTables general: " --log-level 7
iptables -A logging -j DROP




echo "saving"


iptables-save > /etc/iptables.rules


echo "done"

```

As long as I have just VPN working and allowed on the firewall I can ping external IP. This shouldn't be the case.

```

root@RT:~# iptables -x -n -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  255.255.255.255      0.0.0.0/0
ACCEPT     all  --  172.16.0.0/12        172.16.0.0/12
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
DROP       all  --  0.0.0.0/0            0.0.0.0/0
logging    all  --  0.0.0.0/0            0.0.0.0/0


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:993 /* Allow VPN connection */
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            255.255.255.255
ACCEPT     all  --  172.16.0.0/12        172.16.0.0/12
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
DROP       all  --  0.0.0.0/0            0.0.0.0/0
logging    all  --  0.0.0.0/0            0.0.0.0/0


Chain logging (2 references)
target     prot opt source               destination
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 2/min burst 5 LOG flags 0 level 7 prefix "IPTables general: "
DROP       all  --  0.0.0.0/0            0.0.0.0/0

```

---

### Post by Wojciech_Marusiak on 2018-08-24
I did some changes in the script which includes default drop policy but still ping works!

```

#!/bin/bash
# Flush
iptables -t nat -F
iptables -t mangle -F
iptables -F
iptables -X


# Block All
iptables -P OUTPUT DROP
iptables -P INPUT DROP
iptables -P FORWARD DROP


# allow Localhost
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT


# Make sure you can communicate with any DHCP server
iptables -A OUTPUT -d 255.255.255.255 -j ACCEPT
iptables -A INPUT -s 255.255.255.255 -j ACCEPT


# Make sure that you can communicate within your own network
iptables -A INPUT -s 172.16.0.0/12 -d 172.16.0.0/12 -j ACCEPT
iptables -A OUTPUT -s 172.16.0.0/12 -d 172.16.0.0/12 -j ACCEPT


# Allow established sessions to receive traffic:
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT


# Allow TUN
iptables -A INPUT -i tun+ -j ACCEPT
iptables -A FORWARD -i tun+ -j ACCEPT
iptables -A FORWARD -o tun+ -j ACCEPT
iptables -t nat -A POSTROUTING -o tun+ -j MASQUERADE
iptables -A OUTPUT -o tun+ -j ACCEPT


# allow VPN connection
iptables -I OUTPUT 1 -p tcp --destination-port 993 -m comment --comment "Allow VPN connection" -j ACCEPT


# allow SSH connection
iptables -I OUTPUT 1 -p tcp --destination-port 1010 -m comment --comment "Allow SSH connection" -j ACCEPT


# Block All
iptables -A OUTPUT -j DROP
iptables -A INPUT -j DROP
iptables -A FORWARD -j DROP


# Log all dropped packages, debug only.


iptables -N logging
iptables -A INPUT -j logging
iptables -A OUTPUT -j logging
iptables -A logging -m limit --limit 2/min -j LOG --log-prefix "IPTables general: " --log-level 7
iptables -A logging -j DROP


echo "saving"
iptables-save > /etc/iptables.rules
echo "done"
echo 'openVPN - Rules successfully applied, we start "watch" to verify IPtables in realtime (you can cancel it as usual CTRL + c)'
sleep 3
watch -n 0 "sudo iptables -nvL"

```

```

root@RT:~# iptables -nvL
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
21820   85M ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  *      *       255.255.255.255      0.0.0.0/0
    0     0 ACCEPT     all  --  *      *       172.16.0.0/12        172.16.0.0/12
58858   11M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
 2742  236K ACCEPT     all  --  tun+   *       0.0.0.0/0            0.0.0.0/0
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 logging    all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  tun+   *       0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  *      tun+    0.0.0.0/0            0.0.0.0/0
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    8   332 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:1010 /* Allow SSH connection */
27538 5776K ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:993 /* Allow VPN connection */
21820   85M ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            255.255.255.255
    0     0 ACCEPT     all  --  *      *       172.16.0.0/12        172.16.0.0/12
30147 2875K ACCEPT     all  --  *      tun+    0.0.0.0/0            0.0.0.0/0
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 logging    all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain logging (2 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 2/min burst 5 LOG flags 0 level 7 prefix "IPTables general: "
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0

```

---

### Post by darkod on 2018-08-24
What is your default route when VPN is on?
```
route -n
```

If the server tells the client to use the VPN tunnel as default when connected, then ping will continue to work going out through the VPN tunnel.

Run a trace route to the same destination and see which path it takes.

---

