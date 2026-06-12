---
title: "A quick IPTables verification"
date: 2011-02-27
forum: Server Platforms
---

### Post by matthew1471 on 2011-02-27
Could someone do me a favour and check that this iptables config will:

- only allow web traffic from ipn.sandbox.paypal.com
- only allow web traffic from notify.paypal.com
- only allow other web traffic from 192.168.1.1 to 192.168.1.254
- allow ssh on port 1976
- allow established connections
- drop anything that doesn't match the above

Many thanks,
Matt

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:1976 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www source IP range 192.168.1.1-192.168.1.254
ACCEPT     tcp  --  ipn.sandbox.paypal.com  anywhere            tcp dpt:www 
ACCEPT     tcp  --  notify.paypal.com    anywhere            tcp dpt:www 
DROP       all  --  anywhere             anywhere

---

### Post by elico on 2011-02-27
this is a script that i wrote just as a reference
[http://ubuntuforums.org/showpost.php?p=10439802&postcount=4](http://ubuntuforums.org/showpost.php?p=10439802&postcount=4)

and about your clients it's not an input rule but masquarade and forward and input.
means
[PHP]-A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -s 192.168.1.0/16 -i eth1 -j ACCEPT
-A FORWARD -d 192.168.1.0/16 -i eth1 -j ACCEPT
[/PHP]i also recommend to use these

[PHP]-A FORWARD -p gre -j ACCEPT
-A FORWARD -p ah -j ACCEPT
-A FORWARD -p esp -j ACCEPT
-A FORWARD -p l2tp -j ACCEPT
[/PHP]and on the MASQUERADE
[PHP] -A POSTROUTING -o pppX -j MASQUERADE[/PHP](or your wan interface here ^^)

---

