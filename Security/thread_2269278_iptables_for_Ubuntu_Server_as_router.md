---
title: "iptables for Ubuntu Server as router"
date: 2015-03-14
forum: Security
---

### Post by bartgrefte on 2015-03-14
After being used to the webinterfaces of pfSense and IPFire, I am switching to Ubuntu Server 14.10, without a webinterface. Meaning writing iptables firewall rules by myself.

Now that isn't too difficult, but since this particular computer will be working as a router as well, it gets a little more complicated because of NAT. 

So I did some Googling for a while and ended up with this:```
# Flush, remove chains/rules and reset counters
iptables -F
iptables -X
iptables -Z
iptables -t nat -F
iptables -t mangle -F
iptables -t nat -X
iptables -t mangle -X

# set default policy
iptables -P OUTPUT DROP
iptables -P INPUT DROP
iptables -P FORWARD DROP

# allow all IPv4 traffic on loopback
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

# allow all IPv4 traffic on LAN
iptables -A INPUT -i $LAN -p all -j ACCEPT
iptables -A OUTPUT -o $LAN -p all -j ACCEPT

# give LAN access to the internet
iptables -A FORWARD -i $LAN -j ACCEPT
iptables -A FORWARD -i $WAN -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -t nat -F POSTROUTING
iptables -t nat -A POSTROUTING -o $WAN -j MASQUERADE

# give apt-get access to the internet https://darktraining.com/debian/45/
iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT
iptables -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# forward port for uTorrent
iptables -A FORWARD -i $WAN -p tcp --dport 12345 -d 192.168.1.2:12345 -j ACCEPT
iptables -A FORWARD -i $WAN -p udp --dport 12345 -d 192.168.1.2:12345 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp -i $WAN --dport 12345 -j DNAT --to 192.168.1.2:12345
iptables -t nat -A PREROUTING -p udp -i $WAN --dport 12345 -j DNAT --to 192.168.1.2:12345
```

I'm using the "DROP all, except" approach, which I have done before with ip**6**tables, but not with iptables and NAT.

Am I on the right track with these rules or is it a complete mess? Also, I'm having doubts about adding ```
# allow ICMP
iptables -A INPUT -i $WAN -p ICMP -j ACCEPT
iptables -A FORWARD -i $WAN -p ICMP -j ACCEPT
iptables -A OUTPUT -o $WAN -p ICMP -j ACCEPT
```I know you have to allow ICMP with IPv6, but I'm not entirely sure about IPv4. I would like to be able to ping and run tracert, so I think I do need those rules.

Any comments on this?

---

### Post by TheFu on 2015-03-14
Why would you change from pfsense to Linux for a router?  

The BSD network stack is generally considered the best in the world and under extreme loads, it slows down, but doesn't crash.  If you ask network security professionals which edge router software to deploy, 80% will say pfsense - I know - I asked this exact question to a defcon email list.

Seems like the allowed output rules are lacking - no https, ssh, smtp, ftp?  Plus, what happens when an external HTTP server doesn't run on the default port?  Traffic type is the better way to allow outbound traffic, not ports.

---

### Post by bartgrefte on 2015-03-14
> **TheFu said:**
> Why would you change from pfsense to Linux for a router?  

The BSD network stack is generally considered the best in the world and under extreme loads, it slows down, but doesn't crash.  If you ask network security professionals which edge router software to deploy, 80% will say pfsense - I know - I asked this exact question to a defcon email list.Well, I went from pfSense to IPFire for 2 reasons:
- The *BSD atheros driver was buggy at best and (back then) it didn't have 802.11n-features;
- pfSense suddenly started sending about 10,000 DHCP requests in half an hour to my ISP, who cut off the connection.

First I did try a clean install of pfSense, but didn't solve the problem, a clean install of IPFire did plus wifi started working a whole lot better.

> **TheFu said:**
> 
Seems like the allowed output rules are lacking - no https, ssh, smtp, ftp?  Plus, what happens when an external HTTP server doesn't run on the default port?  Traffic type is the better way to allow outbound traffic, not ports.
Are you referring to the output rules for the Ubuntu router itself or the LAN? The only access the router itself needs to have is to be able to download and install updates using apt-get. While the LAN has complete access to the outside, although connections are only allowed back in with the "RELATED,ESTABLISHED state"-rule

---

