---
title: "MAC Address filtering using Iptables"
date: 2016-04-18
forum: Tutorials
---

### Post by sushrut91 on 2016-04-18
This is a tutorial to help you configure mac-id based protection in your server firewall. I had come up with a requirement where I was supposed to restrict server data access only to a few computers / devices physically present in the company. Also I have set up Open VPN on this server.

I searched Internet extensively for any facility in UFW ( the default Ubuntu Firewall package) to get this functionality but didn't find it easily available. So after browsing through many solutions, I decided to post my firewall IP-Table based solution here.

Firstly what is Iptables ? Ip tables is nothing but a firewall package which works in form of tables. Ip tables has tables which are NAT, MANGLE, FILTER, but here we would be dealing with the FILTER table to add our rules. 

Firstly you need to disable all ufw rules using the following command:
```

sudo apt-get ufw disable

```

Here are my rules as implemented to allow only specific Hardware/ MAC ids as specified in the rule list. Save all these rules in a file /etc/iptablemac.rules
```

*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]

#----------------------MAC ADRESSES TO ALLOW --------------------------
#Router
-A INPUT -i br0 -p tcp -m mac --mac-source XX:XX:XX:XX:XX:XX -j ACCEPT
-A INPUT -i br0 -p udp -m mac --mac-source XX:XX:XX:XX:XX:XX -j ACCEPT

#Wired Router
-A INPUT -i br0 -p tcp -m mac --mac-source XX:XX:XX:XX:XX:XX -j ACCEPT
-A INPUT -i br0 -p udp -m mac --mac-source XX:XX:XX:XX:XX:XX -j ACCEPT

#Router Wireless<br>
-A INPUT -i br0 -p tcp -m mac --mac-source XX:XX:XX:XX:XX:XX -j ACCEPT
-A INPUT -i br0 -p udp -m mac --mac-source XX:XX:XX:XX:XX:XX -j ACCEPT

#------------------------------------------------------------------------------------

#----------------------------Global Settings---------------------------------------
#Allow PING Requests (ICMP Protocol)
-A INPUT -i br0 -p tcp --dport 7 -j ACCEPT
-A INPUT -i br0 -p udp --dport 7 -j ACCEPT
<br>
#Allow DHCP ports
-A INPUT -i br0 -p tcp --dport 67 -j ACCEPT
-A INPUT -i br0 -p udp --dport 67 -j ACCEPT
-A INPUT -i br0 -p tcp --dport 68 -j ACCEPT
-A INPUT -i br0 -p udp --dport 68 -j ACCEPT
<br>
#Allow port 22 SSH to everyone
-A INPUT -i br0 -p tcp --dport 22 -m limit --limit 3/minute -j ACCEPT
-A INPUT -i br0 -p udp --dport 22 -m limit --limit 3/minute -j ACCEPT
<br>
#Allow port 1194 OPEN VPN to everyone<br>
-A INPUT -i br0 -p tcp --dport 1194 -j ACCEPT
-A INPUT -i br0 -p udp --dport 1194 -j ACCEPT

#Allow port 5222 EJABBERD to everyone
-A INPUT -i br0 -p tcp --dport 5222 -j ACCEPT
-A INPUT -i br0 -p udp --dport 5222 -j ACCEPT

#----------------------------------------------------------------------------
#Deny everything else not mentioned above
-A INPUT -i br0 -p tcp -j DROP
-A INPUT -i br0 -p udp -j DROP

COMMIT


```

Matching happens from top to botton. There is an exception with interface br0 (bridge) created for openvpn between eth0 and tap0.

The rules can be made every time to load inside memory at bootup or ifup at with this mechanism. *filter specifies the table to use to add the rules inside the kernel.

Add the following line in side your /etc/network/interfaces after your interface rules. If the interface is not managed, refer to other documentation to learn configuring interfaces file

```

pre-up iptables-restore < /etc/iptablemac.rules

```

So next time when the system boots up the rules will should be added. To verify the result use the command
```

sudo iptables -L

```

you should see your new rules added  :). Kudos ! Hope this helps you secure your server more. 

After making any changes to rules flush the iptables previously in memory.
Also keep in mind that if the last 2 lines specifying DROP rules are missing then by default iptables doesn't restrict any traffic by default.

---

