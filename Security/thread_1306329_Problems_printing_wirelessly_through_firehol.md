---
title: "Problems printing wirelessly through firehol"
date: 2009-10-30
forum: Security
---

### Post by gee42 on 2009-10-30
Grateful if anyone can help me with a firehol configuration issue related to printing wirelessly with HP’s hplip . . .

A quick history: I have installed a printer using HP’s hplip (as a newbie this was very easy by the way – I was most impressed) and I’m trying to get it working wirelessly. Our ubuntu 8.04 has firehol installed as part of a Dans Guardian installation and if I turn firehol off then wireless printing works perfectly. So I did some research and found various suggestions for the following ports to be opened: 161, 162, 631, 2207, 2208 and 9100 (UDP and TCP).

I’m afraid I ended up taking a brute force over ignorance approach as I was not having any success. So in the end my firehol.conf is as below which still doesn’t let me print wirelessly. So I think I may have one of two problems: have I used the correct configuration or have I the right ports opened? I will also post this in the printer forum.

version 5
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP
transparent_squid 8080 "proxy root"

# Accept all client traffic on any interface
interface any world
policy drop
protection strong
	client all accept
server cups accept
server custom cups tcp/631 default accept
server custom cups udp/631 default accept
server custom snmp tcp/161 default accept
server custom snmp udp/161 default accept
server custom snmptrap tcp/162 default accept
server custom snmptrap udp/162 default accept
server custom jetdirect tcp/9100 default accept
server custom jetdirect udp/9100 default accept
server custom hpssd tcp/2207 default accept
server custom hpssd udp/2207 default accept
server custom hpiod tcp/2208 default accept
server custom hpiod udp/2208 default accept

Any help much appreciated.  Gee42.

---

### Post by cariboo on 2009-10-30
I don't know if this helps, I just installed a Brother HL-5250DN network printer, It specified port 9100 during the setup, I'm sure wireless would be quite similar.

---

