---
title: "Masquerade not present on Dapper"
date: 2006-09-02
forum: Server Platforms
---

### Post by jose3 on 2006-09-02
Hi guys,
I am running Dappero 6.06 as a server with firewall in an XP lan. I have updates a couple of days ago and tryed to use the internet routing that alreade workied in 5.10 with these lines.
> 
iptables -P FORWARD ACCEPT iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
echo 1 > /proc/sys/net/ipv4/ip_forward


I have searched information about troubleshooting here. It is in spanish
[http://www.tldp.org/HOWTO/IP-Masquer...piling3.1.html](http://www.tldp.org/HOWTO/IP-Masquer...piling3.1.html)

I have ran "ls /proc/net/" to see weather masquerade was loaded
> 
anycast6 igmp6 ip_tables_targets protocols snmp tr_rif arp ip6_flowlabel ipv6_route psched snmp6 udp atm ip_conntrack mcfilter raw sockstat udp6 dev ip_conntrack_expect mcfilter6 raw6 sockstat6 unix dev_mcast ip_mr_cache netfilter route softnet_stat wirelessdev_snmp6 ip_mr_vif netlink rt6_stats stat if_inet6 ip_tables_matches netstat rt_acct tcp igmp ip_tables_names packet rt_cache tcp6


But "ip_masquerade" does not appear.

What should I do? Recompile the Kernel? How come this functionality is not installed by default?

Is there any information else I should post?

Thanks very much.
Jose

---

### Post by jose3 on 2006-09-03
Well I guess is a tought one.
If there is any orientation in order for me to get out of this mess I would appresite. 

Any good troubleshooting for Dapper ipetables?

Thanks

---

