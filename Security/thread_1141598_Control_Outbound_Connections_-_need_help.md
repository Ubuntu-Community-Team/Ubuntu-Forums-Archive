---
title: "Control Outbound Connections - need help"
date: 2009-04-28
forum: Security
---

### Post by xoros on 2009-04-28
I want to have this script run at start up and add these rules to iptables. But, do I have to flush all chains first? 

My virtual machine software places a bunch of rules in there and I didn't want it to conflict with that.  I'm not sure what all the processes are that the vm uses, so kind of difficult to whitelist that.

Should I try to whitelist the vm, if so will it work the same as the previous rules that it had set up- if those are removed?

```
#!/bin/bash
# -WOPP- Whitelist Outbound Processes/Programs
# v1.0 by xoros
# Purpose: You don't need to allow -ALL- outbound traffic -ALL- the time!

# First we define normal services to be allowed
# Comment-out any to turn off what you don't want
# accept localhost traffic
iptables -A INPUT -i lo -j ACCEPT
# accept dns tcp
iptables -A INPUT -p tcp -m tcp --sport 53 -j ACCEPT 
iptables -A OUTPUT -p tcp -m tcp --dport 53 -j ACCEPT 
# accept dns udp
iptables -A INPUT -p udp -m udp --sport 53 -j ACCEPT 
iptables -A OUTPUT -p udp -m udp --dport 53 -j ACCEPT
# accept dhcp
iptables -A INPUT -p udp -m udp --sport 67:68 -j ACCEPT 
iptables -A OUTPUT -p udp -m udp --dport 67:68 -j ACCEPT
# accept http and https
iptables -A INPUT -p tcp -m multiport --sports 80,88,443 -j ACCEPT 
iptables -A OUTPUT -p tcp -m multiport --dports 80,88,443 -j ACCEPT
# mail tsl outbound
# iptables -A OUTPUT -p tcp -m tcp --dport 587 -j ACCEPT 
# mail ssl outbound
# iptables -A OUTPUT -p tcp -m tcp --dport 995 -j ACCEPT

# Now we can use our whitelist
# Manually use "ps aux" to find names
# Substitute "wprocessname1..etc" with names you want
WHTPROC="wprocessname1
wprocessname2
wprocessname3
wprocessname4"
for whtproc in $WHTPROC
do
pid=""
pid=`ps aux | grep $whtproc | head -n 1 | cut -b 10-14`
iptables -A OUTPUT -p tcp -m owner --pid-owner $pid -j ACCEPT
iptables -A OUTPUT -p udp -m owner --pid-owner $pid -j ACCEPT
done

# Drop everything else
iptables -A INPUT -j DROP
iptables -A OUTPUT -j DROP
```

---

