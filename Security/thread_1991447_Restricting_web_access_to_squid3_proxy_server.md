---
title: "Restricting web access to squid3 proxy server"
date: 2012-05-30
forum: Security
---

### Post by bdwernychuk on 2012-05-30
We've been running a squid proxy for years but have users who are "de-configuring" their desktops to bypass squid (and the usage reports we generate from it).

I want to limit web access (http and https) to the proxy server at 192.168.0.254 and block any web access by users trying to bypass the proxy.

Network config is 20 desktops on a 192.168.0.0/24 net. Proxy is an Ubuntu 12.04 VM at 192.168.0.254. Firewall/gateway is another Ubuntu 12.04 machine at 192.168.0.3.

The firewall/gateway uses ufw for iptables management.

ufw defaults are to allow all outgoing, deny all incoming and I've got port forwards set up as needed for incoming traffic (to the mail and web servers inside the firewall).

General internet access is done by this line in the before.rules file:
[COLOR=SeaGreen]-A POSTROUTING -s 192.168.0.0/24 -o eth2 -j MASQUERADE[/COLOR]

I don't touch this stuff often enough to be competent with iptables so any help would be greatly appreciated.

---

### Post by moonpup on 2012-05-30
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid)

Read the section regarding Enforcing the use of your squid proxy server.

---

### Post by bdwernychuk on 2012-06-04
Thanks! The article covers the problem I'm having.

---

### Post by bdwernychuk on 2012-06-05
The attempt to force all port 80 traffic through our proxy server didn't work: users can still bypass the proxy server by deconfiguring proxy use in their web browsers.

I read the material on enforcing use of the proxy server and made the suggested changes to my system:

1. on the proxy server, at 192.168.0.254, the http_port includes the keyword "transparent";

2. on the firewall at 192.168.0.3 (Ubuntu 12.04, running ufw), I modified my before.rules file to include the suggested iptables statements.

My before.rules file (omitting the default portions that are below my nat rules block) appears below. "## NEW" marks the 4 added rules. 

UFW starts without error but the four rules are not doing their job. Any help would be appreciated.

Barry


[COLOR="Green"]# rules.before
#
# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-before-input
#   ufw-before-output
#   ufw-before-forward
#

# nat Table rules
*nat

:PREROUTING - [0:0]

# Port forwarding pre-routing rules

# SMTP (25) to 192.168.0.7
-A PREROUTING -i eth0 -p tcp --dport 25 -j DNAT --to-destination 192.168.0.7

# HTTP (80) to 192.168.0.15
-A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to-destination 192.168.0.15
-A PREROUTING -i eth0 -p udp --dport 80 -j DNAT --to-destination 192.168.0.15

# HTTP (8080) to docbox.nta.local 192.168.0.219
-A PREROUTING -i eth0 -p tcp --dport 8080 -j DNAT --to-destination 192.168.0.219
-A PREROUTING -i eth0 -p udp --dport 8080 -j DNAT --to-destination 192.168.0.219


# VPN Data (543) to 192.168.0.251
-A PREROUTING -i eth0 -p tcp --dport 543 -j DNAT --to-destination 192.168.0.251

# VPN Admin/Web Access (943) to 192.168.0.251
-A PREROUTING -i eth0 -p tcp --dport 943 -j DNAT --to-destination 192.168.0.251
-A PREROUTING -i eth0 -p udp --dport 943 -j DNAT --to-destination 192.168.0.251

# POP3 (110) to 192.168.0.7
-A PREROUTING -i eth0 -p tcp --dport 110 -j DNAT --to-destination 192.168.0.7
-A PREROUTING -i eth0 -p udp --dport 110 -j DNAT --to-destination 192.168.0.7

# IMAP (143) to 192.168.0.7
-A PREROUTING -i eth0 -p tcp --dport 143 -j DNAT --to-destination 192.168.0.7
-A PREROUTING -i eth0 -p udp --dport 143 -j DNAT --to-destination 192.168.0.7

# SSL (for remote Outlook) to 192.168.0.7
-A PREROUTING -i eth0 -p tcp --dport 443 -j DNAT --to-destination 192.168.0.7
-A PREROUTING -i eth0 -p udp --dport 443 -j DNAT --to-destination 192.168.0.7

## NEW -  Force web access through proxy server at 192.168.0.254
# All outbound port 80 traffic off the local net (except from proxy server) is redirected to proxy server

-A PREROUTING -i eth1 -s ! 192.168.0.254 -p tcp --dport 80 -j DNAT --to 192.168.0.254:3128


:POSTROUTING ACCEPT [0:0]

## NEW - make all traffic going back to the proxy look like it's from the firewall
-A POSTROUTING -o eth1 -s 192.168.0.0/24 -d 192.168.0.254 -j SNAT --to 192.168.0.3

# Forward traffic from eth1 (internal net) through eth0 (Internet)
-A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE

## NEW - forward rules to enable forced port 80 traffic to flow to the proxy server

:FORWARD [0:0]

-A FORWARD -s 192.18.0.0/24 -d 192.168.0.254 -i eth1 -o eth1 -m state --state NEW,ESTABLISHED,RELATED -p tcp --dport 3128 -j ACCEPT
-A FORWARD -d 192.18.0.0/24 -s 192.168.0.254 -i eth1 -o eth1 -m state --state ESTABLISHED,RELATED -p tcp --sport 3128 -j ACCEPT

## END of NAT RULES
COMMIT
[/COLOR]

---

