---
title: "iptables causing slow ssh and name lookup errors"
date: 2010-01-24
forum: Server Platforms
---

### Post by matthew1471 on 2010-01-24
Hi,

Why would this iptables cause this mail delivery error? I think it's to do with dns lookups not being routed properly... if remove the last rule, mail works fine.

ssh is also very slow to connect when the last rule is enabled.

postfix mail error:
```
Jan 24 11:32:18 xxxx postfix/smtp[15065]: 9F2162C519: to=<xxxxx@hotmail.com>, relay=none, delay=1005, delays=965/0.01/40/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=hotmail.com type=MX: Host not found, try again)
```

iptables
```
Chain INPUT (policy ACCEPT 1510 packets, 283K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  lo     any     anywhere             anywhere            
 3384  264K ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:1976 
  522 46669 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:www 
   12   648 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:domain 
  291 19722 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:domain
 1269 72208 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:pop3 
  414  179K ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:smtp 
  759 63756 ACCEPT     icmp --  any    any     anywhere             anywhere            
    0     0 DROP       all  --  any    any     anywhere             anywhere            

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 6632 packets, 2968K bytes)
 pkts bytes target     prot opt in     out     source               destination 
```

---

### Post by matthew1471 on 2010-01-24
Ok, here's the answer.

Because lookups are sent to the nameserver on port 53, and the reply comes  on a higher number port [which is blocked] we need to allow access to the ISP's nameservers on the higher numbered port.

```
iptables -A INPUT -p udp -s <ISP DNS server IP>/32 --source-port 53 -d 0/0 --destination-port 1024:65535 -j ACCEPT
```

If you wanted to allow the reply on any port [only do this if you trust your ISP's nameserver]:

```
iptables -A INPUT -p udp -s <ISP DNS server IP>/32 --source-port 53 -d 0/0 -j ACCEPT
```

This is a great resource:

[http://oceanpark.com/notes/firewall_example.html](http://oceanpark.com/notes/firewall_example.html)

---

