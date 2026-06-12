---
title: "Problems writing IPv6 rules for ip6tables"
date: 2018-01-04
forum: Security
---

### Post by courtney2 on 2018-01-04
I am currently working on a box that requires IPv6 support. I have my rules generally wrapped up, my issue right now being allowing my wanted inbound traffic, and then rejecting the rest. Right now, I generically have this in an ip6tables file:

```

*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT


-A INPUT -p tcp -m state --state NEW -m tcp --dport 22 -j ACCEPT
-A INPUT -p tcp -m state --state NEW -m tcp --dport 80 -j ACCEPT
-A INPUT -p tcp -m state --state NEW -m tcp --dport 443 -j ACCEPT
-A INPUT -p icmpv6 -m icmpv6 --icmpv6-type echo-request -j ACCEPT
-A INPUT -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7
-A INPUT -j REJECT
-A INPUT -j REJECT --reject-with icmp6-port-unreachable
-A FORWARD -j REJECT --reject-with icmp6-port-unreachable
-A OUTPUT -p icmpv6 --icmpv6-type echo-request -d ::1/128 -j REJECT --reject-with icmp6-port-unreachable
-A OUTPUT -p icmpv6 --icmpv6-type echo-request -d fe80::/64 -j REJECT --reject-with icmp6-port-unreachable
-A OUTPUT -j ACCEPT
COMMIT

```

Some rules were removed for privacy and security, but they are not relevant to the rules shown. My problem lies at ```
-A INPUT -j REJECT
```. With IPv4 rules, this seems to right out reject inbound traffic that isn't previously listed. But with IPv6 once the rule is applied it seems to just drop any inbound traffic at all. Is there an alternate way that ip6tables does this? I've been scouring the web and there still doesn't seem to be much that talks about all this

---

