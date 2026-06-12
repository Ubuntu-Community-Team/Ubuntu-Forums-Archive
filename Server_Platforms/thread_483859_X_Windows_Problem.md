---
title: "X Windows Problem"
date: 2007-06-25
forum: Server Platforms
---

### Post by infin?ty on 2007-06-25
I am learning how to make a firewall with ipfilter, but i am having a little problem.
I have started with a initial DENY all approach, but after that i ACCEPT the packets thru loopback.
The problem i am facing is that once irun the script all the windows hang and i have to then
accept everything and flush the ipfilter to get everything back on track. following is the little code which is cauing the problem, plz can someone point me out wat mistake i am making.

```

# Set the default policy to drop 
$IPT --policy INPUT   DROP 
$IPT --policy OUTPUT  DROP 
$IPT --policy FORWARD DROP
$IPT -t nat --policy PREROUTING  DROP 
$IPT -t nat --policy OUTPUT DROP 
$IPT -t nat --policy POSTROUTING DROP 
$IPT -t mangle --policy PREROUTING DROP 
$IPT -t mangle --policy OUTPUT DROP 

# Unlimited traffic on the loopback interface 
$IPT -A INPUT  -i lo -j ACCEPT 
$IPT -A OUTPUT -o lo -j ACCEPT 


```

After this i even tried accepting all the udp and tcp packets but the problem remains.

---

