---
title: "TOR - Transparent Proxy Question"
date: 2012-03-31
forum: Security
---

### Post by michael_schmid on 2012-03-31
Hello,

It seems mine is yet another attempt to get a transparent TOR proxy ready to work. I found the following posts, hope I've more luck :):

[http://ubuntuforums.org/showthread.php?t=1722655&highlight=TOR+transparent+proxy](http://ubuntuforums.org/showthread.php?t=1722655&highlight=TOR+transparent+proxy)
[http://ubuntuforums.org/showthread.php?t=1840153&highlight=TOR+transparent+proxy](http://ubuntuforums.org/showthread.php?t=1840153&highlight=TOR+transparent+proxy)

_**Goal:**_ 

Set up TOR to act as a transparent proxy for **all outgoing traffic**, this specifically includes DNS requests.

[B][U]What happend so far:

[/U][/B]I have installed the latest and greatest TOR browser bundle from [https://www.torproject.org/](https://www.torproject.org/), additional proxy software like privoxy or squid is not installed yet as i wanted to keep things simple. I followed these instructions: [https://trac.torproject.org/projects/tor/wiki/doc/TransparentProxy](https://trac.torproject.org/projects/tor/wiki/doc/TransparentProxy), specifically the directions given in the "Local Redirection Through TOR" section - with one important exception:

The given instructions try to configure the local TOR DNS server to use the standard port 53, which AFAIK requires root privileges. For obvious reasons I don't want to start TOR with root privileges, so I changed the following line in $TORBundle/Data/Tor/torrc from

DNSPort 53

to

DNSPort 8753

Vidalia log output shows that TOR can bind to the port and the transparent proxy gets started:

```

Mar 31 13:48:07.300 [Notice] Opening Socks listener on 127.0.0.1:0
Mar 31 13:48:07.301 [Notice] Socks listener listening on port 58030.
Mar 31 13:48:07.301 [Notice] Opening Transparent pf/netfilter listener on 127.0.0.1:9040
Mar 31 13:48:07.301 [Notice] Opening DNS listener on 127.0.0.1:8753
Mar 31 13:48:07.301 [Notice] Opening Control listener on 127.0.0.1:0
Mar 31 13:48:07.301 [Notice] Control listener listening on port 39424.
Mar 31 13:48:07.301 [Notice] Parsing GEOIP file ./Data/Tor/geoip.
Mar 31 13:48:07.939 [Notice] OpenSSL OpenSSL 1.0.0h 12 Mar 2012 looks like version 0.9.8m or later; I will try SSL_OP to enable renegotiation
Mar 31 13:48:07.939 [Notice] We now have enough directory information to build circuits.
Mar 31 13:48:07.939 [Notice] Bootstrapped 80%: Connecting to the Tor network.
Mar 31 13:48:07.939 [Notice] New control connection opened.
Mar 31 13:48:08.807 [Notice] Bootstrapped 85%: Finishing handshake with first hop.
Mar 31 13:48:10.039 [Notice] Bootstrapped 90%: Establishing a Tor circuit.
Mar 31 13:48:15.042 [Notice] Tor has successfully opened a circuit. Looks like client functionality is working.
Mar 31 13:48:15.043 [Notice] Bootstrapped 100%: Done.

```At this point browsing the web using the bundled Firefox works, but all other connection attempts (e.g. thunderbird, pinging or whois-ing sites) are blocked because the system can't connect to the local TOR DNS server. I think the problem lies with the iptables configuration, unfortunately i'm no iptables wizard. This is the iptables configuration script I use, again: note that it is slightly modified to reflect my custom DNS server port of 8753:

```

# destinations you don't want routed through Tor
NON_TOR="192.168.1.0/24 192.168.0.0/24 10.0.0.0/24"

# the UID Tor runs as
TOR_UID="1000"

# Tor's TransPort
TRANS_PORT="9040"

iptables -F
iptables -t nat -F

iptables -t nat -A OUTPUT -m owner --uid-owner $TOR_UID -j RETURN
iptables -t nat -A OUTPUT -p udp --dport 53 -j REDIRECT --to-ports 8753
for NET in $NON_TOR 127.0.0.0/9 127.128.0.0/10; do
 iptables -t nat -A OUTPUT -d $NET -j RETURN
done
iptables -t nat -A OUTPUT -p tcp --syn -j REDIRECT --to-ports $TRANS_PORT

iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
for NET in $NON_TOR 127.0.0.0/8; do
 iptables -A OUTPUT -d $NET -j ACCEPT
done
iptables -A OUTPUT -m owner --uid-owner $TOR_UID -j ACCEPT
iptables -A OUTPUT -j REJECT

```At this point I'm stuck, with the exception of changing the DNS port I followed the given instructions to the letter. Browsing works, but the DNS server configuration (or the iptables rules regarding DNS requests)  is messed up. Any insights or pointers to relevant are most welcome!

Thanks in advance

---

