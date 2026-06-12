---
title: "My server can't ping anything"
date: 2012-05-06
forum: Server Platforms
---

### Post by kosajaffe on 2012-05-06
Hi there,

recently I had to troubleshoot my openvpn configuration. I need to add that I had a running configuration for many month and I changed nothing on my server. But suddenly I experience some strange "read UDPv4 [EHOSTUNREACH]: No route to host (code=113)" messages so I tried to narrow it down further. And by doing this I noticed that my server can't ping any domain. This is no good, is it? Maybe I should start here... Like I said I changed nothing on my running system. I run Ubuntu Server 11.10. What can I do to solve this?

Any hints are highly apreciated.
Thanks

---

### Post by darkod on 2012-05-06
First see if you can ping an IP, like 8.8.8.8. If pinging IPs works, but domains doesn't, it's DNS issue.

If the ping to 8.8.8.8 also fails, you have no internet access.

---

### Post by kosajaffe on 2012-05-06
I can't ping anything (maybe the hosting company blocked ICMP, I don't know) but the Internet connection is working. I can do sudo apt-get update or curl google.com etc... Any further ideas?

---

### Post by darkod on 2012-05-06
And do you have a specific host/domain that is not reachable?

You can try if dns is working fine with: nslookup domain.com

If that returns a reply with the IP of the domain, all looks fine on your end. It seems the routing in the internet is broken to that domain. If the nslookup doesn't return a reply, double check your dns servers in /etc/resolv.conf and in /etc/network/interfaces.

---

### Post by kosajaffe on 2012-05-06
nslookup domain.com is working fine. I tried several domains. I also checked my download speed and I got at least 500kb/s. Not much but it seems ok. 

How can I determine that ICMP ping requests are blocked? Maybe there's a way that I block it accidentally myself... I'm not a firewall guru, so any help on that?

---

### Post by darkod on 2012-05-06
Did you configure the firewall yourself? iptables?

Post the rules you have set up, and we'll take a look. I'm no expert either but we should be able to figure out the ping rule.

Before you post them, change any public IPs or even private IPs you have in your rules with dummy IPs. It's best not to post things like that publicly.

---

### Post by kosajaffe on 2012-05-06
this is what ```
sudo iptables --list
``` gives me:

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootps 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootpc 
ufw-skip-to-policy-input  all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ACCEPT     all  --  bogon/24             anywhere            
ACCEPT     all  --  anywhere             bogon/24            
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             224.0.0.251         udp dpt:mdns 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            state INVALID limit: avg 3/min burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:81 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:81 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:openvpn 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:openvpn 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:openvpn 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:1194 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:1194 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:1194 

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination
```

---

### Post by darkod on 2012-05-06
If you are using ufw as a frontend, and you didn't touch the ICMP section in /etc/ufe/before.rules, it allows ping by default. I have used it.

So, double check the /etc/ufw/before.rules, there is icmp section towards the middle. By default it should allow ping. Make sure there are no entries commented out (with # in front).

---

### Post by kosajaffe on 2012-05-06
Well, I needed to add a rule for masquerading in order to make the OpenVPN stuff working. But the ICMP section I didn't touch.

This is my /etc/ufw/before.rules:

```
#
# rules.before
#
# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-before-input
#   ufw-before-output
#   ufw-before-forward
#

# rules for NAT Table of iptables
# required line for ufw
*nat
:POSTROUTING ACCEPT [0:0]

# Forward traffic from OpenVPN through eth0.
-A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE

# tell ufw to process the lines
COMMIT

# Don't delete these required lines, otherwise there will be errors
*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
# End required lines

# allow all on tun, since we trust OpenVPN completely
-A ufw-before-input -i tun+ -j ACCEPT
-A ufw-before-output -i tun+ -j ACCEPT

# Additionally, I must forward traffic to/from my OpenVPN
-A ufw-before-forward -s 10.8.0.0/24 -j ACCEPT
-A ufw-before-forward -d 10.8.0.0/24 -j ACCEPT

# allow all on loopback
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-output -o lo -j ACCEPT

# quickly process packets for which we already have a connection
-A ufw-before-input -m state --state RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -m state --state RELATED,ESTABLISHED -j ACCEPT

# drop INVALID packets (logs these in loglevel medium and higher)
-A ufw-before-input -m state --state INVALID -j ufw-logging-deny
-A ufw-before-input -m state --state INVALID -j DROP

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

# all other non-local packets are dropped
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny
-A ufw-not-local -j DROP

# allow MULTICAST mDNS for service discovery (be sure the MULTICAST line above
# is uncommented)
-A ufw-before-input -p udp -d 224.0.0.251 --dport 5353 -j ACCEPT


# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT

```

---

### Post by darkod on 2012-05-06
Yeap, looks good.

Is there any chance the provider is blocking pings as some kind of protection? Can you look in some FAQs or contact support?

---

### Post by kosajaffe on 2012-05-06
It's possible that they block ICMP echo req by default but I really don't know that. I did ask them (via email), so let's see what they'll reply. Is there anything else I could do?

---

### Post by darkod on 2012-05-06
Not much until they reply. Everything seems configured correctly. Maybe they are blocking ping to try to make attacks more difficult.

---

### Post by kosajaffe on 2012-05-06
Ok. Thank you for your help so far.

---

### Post by kosajaffe on 2012-05-07
I got a response from my hosting company regarding the ping issue. They say they are not blocking ICMP/Ping by default. So a ping should work. But it isn't. What can do now?

---

### Post by darkod on 2012-05-07
Did you check in /var/log/ufw.log whether ufw is blocking some icmp traffic?

That is the best way to know if ufw is blocking it. If it's not, you need to look into other possibilities, like network, etc.

I have read again your iptables list and the before.rules and can't see anything wrong.

---

### Post by kosajaffe on 2012-05-07
There are some [UFW BLOCK] lines in the log but nothing that would be indicating a problem with outgoing pings...

A ping to localhost is just working fine.

I did also traceroute somedomain.com. It dies on the router on my provider. Does this mean they do block pings? Is their firewall too strict?

```
traceroute to bbc.co.uk (212.58.241.131), 30 hops max, 60 byte packets
 1  cc.dd.ny.adsl (XXX.XX.XX.97)  3.313 ms  3.948 ms  4.614 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
...
30  * * *

```:confused:

---

### Post by darkod on 2012-05-07
It sounds like it. But they replied the opposite, under the assumption that person knew what he/she was talking about. :)

I suggest you follow up that support ticket/question and send them the above tracert result. Let them know you have tried lots of things to investigate this and it seems the only explanation is that they do block pings since your firewall is not blocking them (nothing in the log) and you have internet access, it's not like you don't.

---

