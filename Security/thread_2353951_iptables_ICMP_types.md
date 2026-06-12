---
title: "iptables ICMP types"
date: 2017-02-26
forum: Security
---

### Post by smd3 on 2017-02-26
I'm slowly working toward writing my iptables, using various guides.  (I have chosen to go with the iptables-persistent implementation)

I haven't been able to find clarification on the --icmp-type usage.  If '--icmp-type 0' specifies an entire type, does '[COLOR=#000000]iptables -A INPUT -p icmp --icmp-type 3/4 -j ACCEPT' specify type 3/code 4?[/COLOR]

It seems to be implied in the reference I've been looking at, but I haven't been able to find any other documentation on it.
[http://oregontechsupport.com/articles/icmp.txt](http://oregontechsupport.com/articles/icmp.txt)

My intention is to limit my machines responses to specific types of ICMP traffic.

---

### Post by anoda on 2017-03-08
Hello **smd3**. Generally, I always block an [COLOR=#008000]**ICMP**[/COLOR] protocol (especially an **echo** request.) You have written that: "*If '--icmp-type 0' specifies an entire type...*", right? It's wrong. Type **0** is not specifying an entire type but just **Echo Reply**. (By the way; here You will find [COLOR=#008000]**ICMP**[/COLOR] types <_[http://www.iana.org/assignments/icmp-parameters/icmp-parameters.xhtml](http://www.iana.org/assignments/icmp-parameters/icmp-parameters.xhtml)_>) Anyway, to get list of [COLOR=#008000]**ICMP**[/COLOR] types, You can use this command: **[COLOR=#0000ff]/sbin/iptables -p icmp -h[/COLOR]**. So generally, I blocking **echo-request **(type **8**.) To do this You can use, for example, this rule (your intention is to limit my machines responses to specific types of [COLOR=#008000]**ICMP**[/COLOR] traffic): 

```
iptables -A INPUT -p icmp --icmp-type 8 -j DROP
``` Here, I will provide more examples of rules to block [COLOR=#008000]**ICMP**[/COLOR] protocol. However, many peoples says, that it's not a good idea to block an [COLOR=#008000]**ICMP**[/COLOR] protocol. There is many reasons, check for example: <http://serverfault.com/questions/84963/why-not-block-icmp> 

```
***# Drop ICMP (you usually don't need this protocol).***
/sbin/iptables -A INPUT -p icmp -j DROP

***# Drop/block pings -- the same as "--icmp-type 8"; see above.***
/sbin/iptables -A INPUT -p icmp --icmp-type echo-request -j DROP

[B][I]# Drop fragmented icmp. Normally they aren't needed and blocking fragments 
# will mitigate UDP fragmentation flood (is this applies also to an ICMP?) [/I][/B]
/sbin/iptables -A INPUT --fragment -p icmp -j DROP
[I]
**# Destination-unreachable -- can be maliciously injected.**[/I]
/sbin/iptables -A INPUT -p icmp --icmp-type destination-unreachable -j DROP

***# Router Advertisement and router solicitation -- can be used to facilitate MITM attacks etc.***
/sbin/iptables -A INPUT -p icmp --icmp-type router-advertisement -j DROP
/sbin/iptables -A INPUT -p icmp --icmp-type router-solicitation -j DROP

***# Source Quench -- can be maliciously sent to make your server un-responsible (?)***
/sbin/iptables -A INPUT -p icmp --icmp-type source-quench -j DROP

***# Invalid outgiong icmp packets, need/should to be dropped to prevent a possible exploit.***
/sbin/iptables -A OUTPUT -p icmp -m conntrack --ctstate INVALID -j DROP
```

Some interesting informations about [COLOR=#008000]**ICMP**[/COLOR] and limiting response to this protocol: <https://www.freebsd.org/doc/en/books/faq/networking.html#idp60048744> Filtering incoming [COLOR=#008000]**ICMP**[/COLOR]traffic can be used to block - for example - the ping of death attack and ICMP floods and so on. You probably should block all [COLOR=#008000]**ICMP**[/COLOR] and PING traffic for outside except for your own internal network. 

And If it's about tcp/udp protocols, some people suggest to block these two with (others suggest simply **DROP**):** tcp:** "*--reject-with tcp-reset*" and 
**udp:** "*--reject-with icmp-port-unreachable*". 

That's is just for an information. If it's about me: I think, that the best way to block e.g. [COLOR=#008000]**ICMP **[/COLOR]protocol and other "bad" things is to use PREROUTING chain (which applies to packets that enter the network interface card) with *mangle* table. So PREROUTING is ideally to filter the bad packets etc. Of course, You should also remember about **[COLOR=#0000ff]/etc/sysctl.conf[/COLOR]** file, which contain two very interesting options: *net.ipv4.icmp_echo_ignore_broadcasts *(set to **1**) and *net.ipv4.icmp_ignore_bogus_error_responses* (set to **1**). And many, many more. Sorry **smd3 **but that's all what I can remind for now. 

All of these are just an examples of rules and so on. You should read more about all of these issues etc.

Thanks.

---

