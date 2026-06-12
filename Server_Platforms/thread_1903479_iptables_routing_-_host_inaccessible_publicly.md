---
title: "iptables routing - host inaccessible publicly"
date: 2012-01-02
forum: Server Platforms
---

### Post by NetSkay on 2012-01-02
hey guys i submitted a question to serverfault.com but no one seems to be able to help me out, i edited a few things and posted the iptables ruleset so if anyone could point me in some direction thank you very much!

this is ubuntu 8 installation on AppleTV

[http://serverfault.com/questions/345825/iptables-routing-host-inaccessible-publicly](http://serverfault.com/questions/345825/iptables-routing-host-inaccessible-publicly)

---

### Post by Doug S on 2012-01-02
If I understand correctly (which is often not the case) the SSH daemon is listening on port 50. Try changing this line:```
-A INPUT -p tcp -m tcp -i eth0 --sport 50 -j ACCEPT
``` to this: ```
-A INPUT -p tcp -m tcp -i eth0 --dport 50 -j ACCEPT
```

---

### Post by mclimber43 on 2012-01-03
I think Doug S has a great suggestion for the ssh.  As for the vpn, do you have a rule allowing udp traffic in on port 1194?

-A INPUT -p udp -m udp -i eth0 --dport 1194 -j ACCEPT

---

### Post by NetSkay on 2012-01-03
> **Doug S said:**
> If I understand correctly (which is often not the case) the SSH daemon is listening on port 50. Try changing this line:```
-A INPUT -p tcp -m tcp -i eth0 --sport 50 -j ACCEPT
``` to this: ```
-A INPUT -p tcp -m tcp -i eth0 --dport 50 -j ACCEPT
```

THNX DOUG!! that worked, i was overlooking destination vs source :)
i pasted your reply to serverfault.com and linked back here for credit :)

---

### Post by NetSkay on 2012-01-03
mclimber43, i have VPN running over TCP and not UDP
really weird though, SSH works, and so does the webserver on port 10000 but i cant seem to connect to the VPN server, and the rules ive set are the same you guys have suggested but different port, ie. 1194 and 1195 even when i allow all traffic to go through... let me investigate some more

EDIT

i switched to UDP, and now i can connect publicly but the client hangs on receiving server responses, so basically the client can send data packets to the server but the server cannot route back; i think this arises due to the fact that the server sits behind 2 NAT routers and if someone can confirm that this is the problem that would be great
the first NAT router faces the internet, and the second NAT router has a static IP behind the first and it IS set in the DMZ of the first, internet facing router, and i have specific ports forwarded on the second NAT router
however what confuses me is that i can serve web pages under this configuration but cannot get openVPN working properly...

---

### Post by Doug S on 2012-01-04
I'm glad that the SSH part is now working, and thanks for replying back here about it.
For your VPN issue, perhaps you could post your current iptables rule set here.

---

### Post by NetSkay on 2012-01-04
ok so here here is the config for the openVPN server daemon


```
port 5000

# TCP or UDP server?
proto tcp

dev tun

ca /etc/openvpn/ca.crt
cert /etc/openvpn/server.crt
key /etc/openvpn/server.key  # This file should be kept secret

dh /etc/openvpn/dh2048.pem

ifconfig-pool-persist ipp.txt

push "route 192.168.0.0 255.255.0.0"

client-to-client
keepalive 10 120
cipher DES-EDE3-CBC  # Triple-DES
comp-lzo
max-clients 10
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3
```

client config:
```
client
dev tun
proto tcp
remote a.b.c.d 5000
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert netskay.crt
key netskay.key
ns-cert-type server
cipher DES-EDE3-CBC
comp-lzo
verb 3
```

current iptables ive been using to troubleshoot; all connections to the host are allowed:
```
*nat
:PREROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]

-A POSTROUTING -s 192.168.3.0/255.255.255.0 -j MASQUERADE
COMMIT

*mangle
:PREROUTING ACCEPT [213:219554]
:INPUT ACCEPT [213:219554]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [155:35616]
:POSTROUTING ACCEPT [155:35616]
COMMIT

*filter
:FORWARD ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT -m state --state ESTABLISHED -j ACCEPT
-A INPUT -m state --state RELATED -j ACCEPT
# VPN - LAN (5000)
-A INPUT -p udp -m udp --dport 5000 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 10000 # webmin, i can access fine
# router/local
-A INPUT -s 192.168.2.0/255.255.255.0 -i eth0 -j ACCEPT
# VPN - redirect
-A INPUT -s 192.168.3.0/255.255.255.0 -i tun1 -j ACCEPT
# VPN - LAN
-A INPUT -s 192.168.4.0/255.255.255.0 -i tun0 -j ACCEPT
# macbook
-A INPUT -m mac --mac-source XX:XX:XX:XX:XX:XX -j ACCEPT
COMMIT
```

---

### Post by NetSkay on 2012-01-04
i can connect from the within the LAN to the VPN, from behind router 1, which faces the net, and from within router 2, which is connected to router 1 and both are NAT-ed, router 1 has router 2 on its DMZ, and router 2 forwards ports, the VPN server sits on a static ip behind router 2

thank you for your help :)

---

### Post by Doug S on 2012-01-04
Hi NetSkay,
I am having trouble to assemble the various story fragments into something that makes sense (to me, at least). In your latest iptables rules set listing, I don't see the SSH stuff, which you mentioned is now working. I see various sub-nets, but it not clear (to me, at least) which sub-net is where with respect to the text. The configs seems to be for tcp, yet the related rule is for udp. It isn't even clear (to me, at least) which box this iptable rule set is running on.
Perhaps I am just being dense. Anyway, I am unable to help, at least for now.
 
... Doug S.

---

### Post by NetSkay on 2012-01-05
this configuration of iptables allows me to connect to port 50 even though it is not listed because i have set the default action to ACCEPT, so basically the firewall permits all connections to/from the host; so i know for sure it is NOT an iptables issue, more of an openVPN configuration issue from my understanding :/
sorry for the confusion i hope this clears things a bit more

---

### Post by NetSkay on 2012-01-05
so im sorry to say but the problem isnt the vpn server configuration, nor iptables, nor my router... IT IS MY ******* ISP

[http://www.dslreports.com/faq/7288](http://www.dslreports.com/faq/7288)
[http://community.spiceworks.com/topic/78249-pptp-vpn-ports-blocked](http://community.spiceworks.com/topic/78249-pptp-vpn-ports-blocked) [best answer reply]

immense frustration

i can probably host it over Tor

---

### Post by aaron.kyle on 2012-04-27
forgive me here as I am very new to this.

let's say that  I am connecting a home server to an EC2 instance via OpenVPN.  I want the EC2 elastic IP to resolve to the home server --effectively making my home server (blocked by ISP NAT) public.  Doing this should be a matter of assigning public IP traffic to resolve to the private IP of my server registered on the OpenVPN, but I can't for the life of me figure this out.  Where to start?  Apache?  iptables?  something else entirely?

---

