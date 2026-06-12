---
title: "Iptables and local Privoxy/Tor proxy"
date: 2011-09-27
forum: Security
---

### Post by zedixal on 2011-09-27
Hi,

I have used Tor for a while, with the classic scheme: Browser --> Privoxy --> Tor. Now I'd like to use iptables to redirect all http connections to Privoxy, so I read [this page]("https://trac.torproject.org/projects/tor/wiki/doc/TransparentProxy"). The instructions kinda worked, but this way it seems that Privoxy is bypassed through Tor TransPort.
So I kept only the DNS redirect rule, but now I'm stuck. My current set of tor-related iptables directives are:

```

# Tor's UID
TOR_UID=$(id -u debian-tor)
# Privoxy UID
PRIVOXY_UID=$(id -u privoxy)

# Redirect DNS packets to Tor DNSPort
iptables -t nat -A OUTPUT -p udp --dport 53 -m state --state NEW -j REDIRECT --to-ports 53
# Tor is allowed to open a HTTPS connection
iptables -A OUTPUT -o ppp0 -p tcp --dport 443 -m state --state NEW -m owner --uid-owner $TOR_UID -j ACCEPT
# Tor is allowed to send new TCP packets on ports 9001 and 9030
iptables -A OUTPUT -o ppp0 -p tcp --dport 9001 -m state --state NEW -m owner --uid-owner $TOR_UID -j ACCEPT
iptables -A OUTPUT -o ppp0 -p tcp --dport 9030 -m state --state NEW -m owner --uid-owner $TOR_UID -j ACCEPT

```TIA

---

### Post by bodhi.zazen on 2011-09-27
You are not re-directing anything to privoxy nor are you re-directing http traffic.

See :

[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)
[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

---

### Post by zedixal on 2011-09-27
Thank you bodhi.zazen

Following the directives in [your blog]("http://blog.bodhizazen.net/linux/how-to-transparent-proxy/"), I changed /etc/privoxy/config

```

listen-address  127.0.0.1:8118
accept-intercepted-requests 1

```

and added the rules

```

sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner root -j ACCEPT
sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner ! --uid-owner privoxy -j REDIRECT --to-port 8118

```

but running wget without setting a proxy gives me these lines

```

wget www.google.com
--2011-09-27 22:00:06--  http://www.google.com/
Resolving www.google.com... 74.125.235.50
Connecting to www.google.com|74.125.235.50|:80... failed: Connection timed out.
Retrying.

--2011-09-27 22:03:16--  (try: 2)  http://www.google.com/
Connecting to www.google.com|74.125.235.50|:80... failed: Connection timed out.
Retrying.

--2011-09-27 22:06:27--  (try: 3)  http://www.google.com/
Connecting to www.google.com|74.125.235.50|:80... failed: Connection timed out.
Retrying.

```

and so on. I guess I'm missing something.

---

### Post by bodhi.zazen on 2011-09-27
First you will need to post all your rules as the order of your rules counts.

Second you have not accepted traffic from either privoxy or Tor.

---

### Post by zedixal on 2011-09-28
Sorry for the delay, this is the firewall script I use in my Tor box

```

#!/bin/bash

# 
# Kernel configuration.
# 
# Disable IP forwarding.
# Note: Turning this on and off should reset all settings to their defaults.
sudo echo 1 > /proc/sys/net/ipv4/ip_forward
sudo echo 0 > /proc/sys/net/ipv4/ip_forward
# Enable IP spoofing protection (i.e. source address verification).
sudo echo 1 > /proc/sys/net/ipv4/conf/all/rp_filter
# Protect against SYN flood attacks (see http://cr.yp.to/syncookies.html).
sudo echo 1 > /proc/sys/net/ipv4/tcp_syncookies
# Ignore all (incoming + outgoing) ICMP ECHO requests (i.e. disable PING).
# Usually not a good idea, as some protocols and users need/want this.
# echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
sudo echo 0 > /proc/sys/net/ipv4/icmp_echo_ignore_all
# Ignore ICMP ECHO requests to broadcast/multicast addresses. We do not
# want to participate in smurf (and similar) DoS attacks.
sudo echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
# Log packets with impossible addresses.
sudo echo 1 > /proc/sys/net/ipv4/conf/all/log_martians
# Don't log invalid responses to broadcast frames, they just clutter the logs.
sudo echo 1 > /proc/sys/net/ipv4/icmp_ignore_bogus_error_responses
# Don't accept or send ICMP redirects.
sudo echo 0 > /proc/sys/net/ipv4/conf/all/accept_redirects
sudo echo 0 > /proc/sys/net/ipv4/conf/all/send_redirects
# Don't accept source routed packets.
sudo echo 0 > /proc/sys/net/ipv4/conf/all/accept_source_route
# Disable proxy_arp. Should not be needed, usually.
sudo echo 0 > /proc/sys/net/ipv4/conf/all/proxy_arp
# Enable secure redirects, i.e. only accept ICMP redirects for gateways
# listed in the default gateway list. Helps against MITM attacks.
sudo echo 1 > /proc/sys/net/ipv4/conf/all/secure_redirects 
# Disable bootp_relay. Should not be needed, usually.
sudo echo 0 > /proc/sys/net/ipv4/conf/all/bootp_relay

# 
# Set the default policy for each of the pre-defined chains
# 
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

# 
# Cleanup
# 
# Delete all rules
iptables -F
iptables -t nat -F
iptables -t mangle -F
# Delete all (non-builtin) user-defined chains
iptables -X
iptables -t nat -X
iptables -t mangle -X
# Zero all packet and byte counters
iptables -Z
iptables -t nat -Z
iptables -t mangle -Z

# 
# Accept anything on localhost
# 
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

# 
# Allow established connections
# 
# Accept established incoming connections
iptables -A INPUT -m state --state ESTABLISHED -j ACCEPT
# Accept established outgoing connections
iptables -A OUTPUT -m state --state ESTABLISHED -j ACCEPT


# 
# Tor
# 
TOR_UID=$(id -u debian-tor)
PRIVOXY_UID=$(id -u privoxy)

# Tor is allowed to open a HTTPS connection
iptables -A OUTPUT -o ppp0 -p tcp --dport 443 -m state --state NEW -m owner --uid-owner $TOR_UID -j ACCEPT
# Tor is allowed to send new TCP packets on ports 9001 (ORPort) and 9030 (DIRPort)
iptables -A OUTPUT -o ppp0 -p tcp --dport 9001 -m state --state NEW -m owner --uid-owner $TOR_UID -j ACCEPT
iptables -A OUTPUT -o ppp0 -p tcp --dport 9030 -m state --state NEW -m owner --uid-owner $TOR_UID -j ACCEPT
# Redirect DNS requests to Tor DNSPort
iptables -t nat -A OUTPUT -p udp --dport 53 -m state --state NEW -j REDIRECT --to-ports 53

# *****
iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner root -j ACCEPT
iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner ! --uid-owner $PRIVOXY_UID -j REDIRECT --to-port 8118
# *****

exit 0

```

---

### Post by bodhi.zazen on 2011-09-28
You are using a very restrictive set of rules so you need a rule to allow traffic you wish to allow, which is --dport 80 and 443 for privoxy, which you still have not done, all you have done is redirect non-privoxy users.

---

### Post by zedixal on 2011-09-28
Ok, now the last three rules of my script look like:

```
iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner root -j ACCEPT
iptables -t nat -A OUTPUT -p tcp -m multiport --dports 80,443 -m owner --uid-owner $PRIVOXY_UID -j ACCEPT
iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner ! --uid-owner $PRIVOXY_UID -j REDIRECT --to-port 8118
```but the result is still the same. How should I allow Privoxy?

---

### Post by bodhi.zazen on 2011-09-28
You will have to look and see where your packets are getting dropped.

---

### Post by zedixal on 2011-09-29
Well, after some little research (e.g. tcpdump mysterious outputs), I am even more :???:.

Obviously, if I omit the line

```
iptables -P OUTPUT DROP
```in my script, redirection works well. But I'm not sure that setting OUTPUT default policy to ACCEPT is a good idea for a Tor firewall

---

### Post by zedixal on 2011-09-29
By trial and error, I finally found that the rule I need is

```

iptables -A OUTPUT -o ppp0 -p tcp -m multiport --dports 1024:65535 -m state --state NEW -j ACCEPT

```after the three in #7. If I try to restrict this rule (with a 'owner' option) to Tor only, redirection doesn't work. So I suppose that something (not Tor) needs to connect directly to an external target.
I have no idea of what this rule means, and why it is necessary. Actually, this rule smells of security risk.

---

### Post by bodhi.zazen on 2011-09-29
> **zedixal said:**
> Actually, this rule smells of security risk.

Well, I have not been giving you the answer as I sort of want you to learn how iptables works.

If you do not understand that rule, take a look at 

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by zedixal on 2011-09-30
Hi there

I'm digging into iptables, realizing that my current knowledge of it is quite crude
I think I'll need some time to understand what I have misunderstood :redface: - However, I consider this thread solved

Thank you bodhi.zazen

---

### Post by bodhi.zazen on 2011-09-30
> **zedixal said:**
> Hi there

I'm digging into iptables, realizing that my current knowledge of it is quite crude
I think I'll need some time to understand what I have misunderstood :redface: - However, I consider this thread solved

Thank you bodhi.zazen

There is a bit of a learning curve with iptables.

If it helps, see also :

[http://bodhizazen.net/IPTables.odt](http://bodhizazen.net/IPTables.odt)

---

