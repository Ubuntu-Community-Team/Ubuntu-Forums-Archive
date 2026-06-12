---
title: "What are these weird IP addresses?"
date: 2012-06-24
forum: Security
---

### Post by zozza on 2012-06-24
I was looking at my VPN traffic in Wireshark with ppp0 and I noticed a number of strange IPs.

I was not using the Internet (for example HTTP) and hence was not making these connections myself. 

The ufw.log file provides the same information. 

I am 109.205.169.5.

ICMP (my VPN IP to many other IPs) - always "destination unreachable - port unreachable".

WHOIS shows my ICMP traffic to:

Oriental Cable Network Co (China)
Charter Communications (USA)
MarocTelecom (Morocco)
Telenor Norge (Norway)
RCS & RDS (Romania)

TCP (their IPs to my VPN IP and my VPN IP then responds to their IPs).

WHOIS shows TCP traffic to and from:

Hetzner Online (Germany)
BVNET (Argentina)

UDP (their IPs to my VPN IP).

WHOIS shows their UDP traffic to me from:

Oriental Cable Network Co (China)
TurkTelekom (Turkey)
Bulgarian Telecommunications Company (Bulgaria)
103.2.208.5 (an IP with no WHOIS record)
Cablevision AR (Argentina)

I have enclosed the Wireshark file (only 200 entries) as an attachment.

What are these IPs?  I do not see these IPs when I do not use a VPN.  It's very strange (to me at least).

Thanks!

---

