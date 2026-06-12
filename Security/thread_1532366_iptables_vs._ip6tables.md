---
title: "iptables vs. ip6tables"
date: 2010-07-16
forum: Security
---

### Post by Sporkman on 2010-07-16
Question (and Google results aren't making this clear):

Ubuntu has both iptables & ip6tables installed.

1. If I set a rule in iptables, does that rule also apply to ipv6, or just ipv4?

2. If "no" to above, then it would be prudent to *also* set ip6tables rules as well if I want to maintain an active firewall, correct?

3. Does ip6tables rules have the same syntax and behavior (more or less) to iptables rules - i.e. can I just copy my iptables rules & change "iptables" to "ip6tables"?

4. Any gotchas or issues that I should be aware of?

-Thanks

---

### Post by kemra on 2010-07-16
I can't answer most of your questions here as I tend to use hardware firewalls, but as for number 2 I don't believe you need to set any ipv6 rules unless you are using ipv6 on your network. Some one please correct me if I'm wrong as I would love to know.

---

### Post by bodhi.zazen on 2010-07-16
> **Sporkman said:**
> Question (and Google results aren't making this clear):

Ubuntu has both iptables & ip6tables installed.

1. If I set a rule in iptables, does that rule also apply to ipv6, or just ipv4?

2. If "no" to above, then it would be prudent to *also* set ip6tables rules as well if I want to maintain an active firewall, correct?

3. Does ip6tables rules have the same syntax and behavior (more or less) to iptables rules - i.e. can I just copy my iptables rules & change "iptables" to "ip6tables"?

4. Any gotchas or issues that I should be aware of?

-Thanks

No, if you want to set rules for ipv6 use ip6tables.

The syntax is the same

iptables -A INPUT foo -j DROP 

becomes

ip6tables -A INPUT foo -j DROP

Unless your IP provider has enabled ipv6 it is a non-issue.

If you are paranoid, simply

```
sudo ip6tables -A INPUT -j DROP
```Or disable ipv6 .

---

### Post by wacky_sung on 2010-07-16
> **bodhi.zazen said:**
> 

```
sudo ip6talbes -A INPUT -j DROP
```



Correction

```
sudo ip6tables -A INPUT -j DROP
```

Below is just a sample of of my ipv6 tables.

```
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all      any    any     anywhere             anywhere            recent: UPDATE seconds: 86400 name: lastmeasure side: source 
    0     0 DROP       tcp      any    any     anywhere             anywhere            state NEW recent: UPDATE seconds: 60 name: DEFAULT side: source 
    6   420 ACCEPT     all      lo     any     anywhere             anywhere            
    0     0 DROP       all      any    any     anywhere             anywhere            state INVALID 
    0     0 ACCEPT     all      any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 DROP       tcp      any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
    0     0 DROP       tcp      any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,RST,PSH,ACK,URG 
    0     0 DROP       tcp      any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/NONE 
    0     0 ACCEPT     tcp      any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 
    0     0 DROP       tcp      any    any     anywhere             anywhere            tcp flags:FIN,ACK/FIN 
    0     0 DROP       tcp      any    any     anywhere             anywhere            tcp flags:PSH,ACK/PSH 
    0     0 DROP       tcp      any    any     anywhere             anywhere            tcp flags:ACK,URG/URG 
    0     0 DROP       tcp      any    any     anywhere             anywhere            tcp flags:FIN,RST/FIN,RST 
    0     0 DROP       tcp      any    any     anywhere             anywhere            tcp flags:FIN,SYN/FIN,SYN 
    0     0 DROP       tcp      any    any     anywhere             anywhere            tcp flags:SYN,RST/SYN,RST 
    0     0 DROP       tcp      any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,RST,PSH,ACK,URG 
    0     0 DROP       tcp      any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/NONE 
    0     0 DROP       tcp      any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,PSH,URG 
    0     0 DROP       tcp      any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,PSH,URG 
    0     0 DROP       tcp      any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,RST,ACK,URG 
    0     0 ACCEPT     tcp      any    any     anywhere             anywhere            tcp flags:RST/RST limit: avg 2/sec burst 2 
    0     0 DROP       udp      any    any     anywhere             anywhere            limit: avg 1/sec burst 2 
    0     0 DROP       all      any    any     anywhere             anywhere            frag ids:100:200 first 
    0     0 DROP       udp      eth0   any     anywhere             anywhere            udp dpt:domain recent: UPDATE seconds: 660 hit_count: 7 name: DEFAULT side: source 
    0     0 ACCEPT     ipv6-icmp    any    any     anywhere             anywhere            ipv6-icmp echo-request limit: avg 30/min burst 5 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all      any    any     anywhere             anywhere            state INVALID 

Chain OUTPUT (policy DROP 6 packets, 384 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    6   420 ACCEPT     all      any    lo      anywhere             anywhere            
    0     0 DROP       all      any    any     anywhere             anywhere            state INVALID 
    0     0 ACCEPT     all      any    any     anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
    0     0 DROP       tcp      any    any     anywhere             anywhere            tcp dpt:ipp 
    0     0 DROP       udp      any    any     anywhere             anywhere            udp dpt:ipp 
    0     0 DROP       all      any    any     anywhere             anywhere            frag ids:100:200 first 

```

Iptables is similiar to ip6tables but the protocol ICMP is kinda difference in ipv6.

---

### Post by Sporkman on 2010-07-16
Ok thanks. :)

---

### Post by movieman on 2010-07-16
> **bodhi.zazen said:**
> Unless your IP provider has enabled ipv6 it is a non-issue.

Assuming no-one can access your LAN; if you allow random people onto it then you want to either disable IPV6 or firewall it just like IPV4.

Personally I like having IPV4 and V6 on my LAN at home because I can still log in over IPV6 when I accidentally block all traffic while reconfiguring the IPV4 firewall :).

---

### Post by bodhi.zazen on 2010-07-16
> **movieman said:**
> Assuming no-one can access your LAN; if you allow random people onto it then you want to either disable IPV6 or firewall it just like IPV4.

If someone can access your LAN, ipv6 is the least of your worries - :lolflag:

> Personally I like having IPV4 and V6 on my LAN at home because I can still log in over IPV6 when I accidentally block all traffic while reconfiguring the IPV4 firewall :).

Try iptables-save.

You then edit the saved file

You apply changes with iptables-apply. If you do not confirm a connection, iptables-apply reverses the changes.

[http://bodhizazen.net/Tutorials/iptables/#Saving_your_configuration](http://bodhizazen.net/Tutorials/iptables/#Saving_your_configuration)

```
root@ufbt:~#iptables-apply /etc/iptables.save
Applying new ruleset... done.
Can you establish NEW connections to the machine? (y/N) apparently not...
Timeout. Something happened (or did not). Better play it safe...
Reverting to old ruleset... done.
```

Helps prevent lockouts (not that that has EVER happened to me =) ).

---

### Post by wacky_sung on 2010-07-16
This is what i did to manual load both iptables and ip6tables at the same time in my interfaces file.


```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

auto eth0
iface eth0 inet dhcp
  pre-up iptables-restore < /etc/iptables.rules
  pre-up ip6tables-restore < /etc/ip6tables.rules
  post-down iptables-restore < /etc/iptables.downrules
  post-down ip6tables-restore < /etc/ip6tables.downrules

```

---

### Post by bodhi.zazen on 2010-07-16
> **wacky_sung said:**
> This is what i did to manual load both iptables and ip6tables at the same time in my interfaces file.


```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

auto eth0
iface eth0 inet dhcp
  pre-up iptables-restore < /etc/iptables.rules
  pre-up ip6tables-restore < /etc/ip6tables.rules
  post-down iptables-restore < /etc/iptables.downrules
  post-down ip6tables-restore < /etc/ip6tables.downrules

```

Perfect =)

---

### Post by wacky_sung on 2010-07-16
Thank you.I barely use Ubuntu for 3 months and i am still learning.Beside that,i am not from IT profession but it is just my interest focus on internet security.

---

### Post by bodhi.zazen on 2010-07-16
In reviewing your rules, that only sets up eth0, you need to add similar syntax to wlan0 (pre-up and post-down).

---

### Post by wacky_sung on 2010-07-16
> **bodhi.zazen said:**
> In reviewing your rules, that only sets up eth0, you need to add similar syntax to wlan0 (pre-up and post-down).

Probably you can show me to add the SSID and password if i am using on my personal wifi / view public free wifi.Thank.

---

### Post by bodhi.zazen on 2010-07-16
> **wacky_sung said:**
> Probably you can show me to add the SSID and password if i am using on my personal wifi / view public free wifi.Thank.

Start here:

[HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc. - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=318539") 

Begin a new thread if you have a problem.

---

### Post by wacky_sung on 2010-07-16
Much appreciated.Thank you.

---

