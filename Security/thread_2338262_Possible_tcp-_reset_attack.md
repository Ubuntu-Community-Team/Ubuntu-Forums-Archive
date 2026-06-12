---
title: "Possible tcp- reset attack"
date: 2016-09-26
forum: Security
---

### Post by mafialord on 2016-09-26
In the past few days, our squid server is crashing constantly. We currently allow only inbound and outbound traffic from 3128 and port 22. We observed the UFW log and observed that this crash occurs, when certain IP's flood the sever with RST packets whose value is 0.My question is will having a blanket ban on all RST packet solve the problem and will harm the network in any way

---

### Post by anoda on 2016-10-10
Hello. Please try to change 22. port to higher value (for example above 4000?). Generally, I think iptables is better than UFW if it's about config etc. I think also, that You could/should edit [COLOR=#008000]/etc/sysctl.conf[/COLOR] file and add options to better mitigate the effects of attacks. Here is _an example_ rule to limits incoming TCP RST packets to mitigate TCP RST floods - You've mentioned about this one. 

```
iptables -A INPUT -p tcp --tcp-flags RST RST -m limit --limit 2/s --limit-burst 2 -j ACCEPT
iptables -A INPUT -p tcp --tcp-flags RST RST -j DROP
```

Also block more packets with bogus TCP flags (above is just one example). One more thing: block packets from Private Subnets (i.e: 224.0.0.0/3, 172.16.0.0/12, 240.0.0.0/5, 192.168.0.0/16, 10.0.0.0/8 etc.) Also, if it's about [COLOR=#008000]/etc/sysctl.conf[/COLOR] file You can add, for example (Remeber to read about this options!): 

```
net.ipv4.conf.all.rp_filter = 1
net.ipv4.conf.all.accept_redirects = 0
net.ipv4.conf.all.send_redirects = 0
net.ipv4.conf.all.accept_source_route = 0
net.ipv4.icmp_echo_ignore_broadcasts = 1
net.ipv4.icmp_ignore_bogus_error_responses = 1
net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_synack_retries = 1
net.ipv4.tcp_syn_retries = 2
net.ipv4.tcp_max_syn_backlog = 16384
net.ipv4.tcp_rfc1337 = 1
net.ipv4.tcp_tw_recycle = 0
net.ipv4.tcp_tw_reuse = 1
vm.swappiness = 20
net.netfilter.nf_conntrack_tcp_loose = 0
``` 

If it's about the last one option - I think You can/should read more about *net.netfilter.nf_conntrack_tcp_timeout_*  *sysctl options and modify their default values to suit your needs:

```
*established
*close
*close_wait
*fin_wait
*last_ack
*syn_recv
*syn_sent
*time_wait
```

Dont forget to run ***sysctl -p*** command after edit this file! (As root or via sudo(8)). There is so many options which can be used both: in firewall and [COLOR=#008000]/etc/sysctl.conf[/COLOR] file. I don't remember many of them right now. Sorry. Please search and read...

---

