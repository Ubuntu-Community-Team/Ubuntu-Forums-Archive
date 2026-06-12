---
title: "How to disable iptables kernel logging ?"
date: 2006-08-27
forum: Server Platforms
---

### Post by Peturrr on 2006-08-27
I have configured a server to act as a very simple NAT router. 

It all works great, however, when using the internet connection over this router there is lot's and lot's of harddisk activity on the router.
I found out that every connection through the router is logged to the kernel log. I want to disable this logging, since it keeps my harddisk busy 24h/day and that definately reduces it's lifetime. 

The following rules are applied, none of them have a -LOG parameter.

```

#Flush all rules
iptables -F
iptables -t nat -F

#NAT
iptables -t nat -A POSTROUTING -s 10.0.0.2 -o eth0 -j MASQUERADE
iptables -t nat -A POSTROUTING -s 10.0.0.2 -o ppp0 -j MASQUERADE

#ALLOW Connections
iptables -A FORWARD -s 10.0.0.2 -o ppp0 -j ACCEPT
iptables -A FORWARD -s 10.0.0.2 -o eth0 -j ACCEPT

iptables -A FORWARD -d 10.0.0.2 -m state --state ESTABLISHED,RELATED -i eth0 -j ACCEPT
iptables -A FORWARD -d 10.0.0.2 -m state --state ESTABLISHED,RELATED -i ppp0 -j ACCEPT

``` 
How would I disable the logging of these rules?

---

### Post by Woei on 2006-08-27
> **Peturrr said:**
> I have configured a server to act as a very simple NAT router. 

It all works great, however, when using the internet connection over this router there is lot's and lot's of harddisk activity on the router.
I found out that every connection through the router is logged to the kernel log. I want to disable this logging, since it keeps my harddisk busy 24h/day and that definately reduces it's lifetime. 

The following rules are applied, none of them have a -LOG parameter.

```

#Flush all rules
iptables -F
iptables -t nat -F

#NAT
iptables -t nat -A POSTROUTING -s 10.0.0.2 -o eth0 -j MASQUERADE
iptables -t nat -A POSTROUTING -s 10.0.0.2 -o ppp0 -j MASQUERADE

#ALLOW Connections
iptables -A FORWARD -s 10.0.0.2 -o ppp0 -j ACCEPT
iptables -A FORWARD -s 10.0.0.2 -o eth0 -j ACCEPT

iptables -A FORWARD -d 10.0.0.2 -m state --state ESTABLISHED,RELATED -i eth0 -j ACCEPT
iptables -A FORWARD -d 10.0.0.2 -m state --state ESTABLISHED,RELATED -i ppp0 -j ACCEPT

``` 
How would I disable the logging of these rules?

The file you want to change is /etc/syslog.conf. As stated on the top of that file, you should read the excellent manual page first before changing it.

Basically, the line 'kern.* -/var/log/kern.log' means that it will log _all_ kernel messages to the named logfile, from debugging messages to critical errors. What you want to do now is either comment that line, to silence all kernel messages (*not recommended*), or modify the line to exclude certain levels of logging.

For example```
kern.*;kern.!warning -/var/log/kern.log
``` will exclude all kernel warnings (and by default, netfilter logs messages at that priority IIRC), but will log everything to /var/log/kern.log, without doing an fsync() call (the minus sign). You can play with the -j LOG --log-level setting in your firewall script to direct certain packet actions to a different level so they still get logged.

BTW, it's a fallacy to think your hard drive will wear out faster if it has to seek more. In fact, it will live longer, as the heads don't stay in one place all the time, heating up the grease and melting it on the platter, resulting in head crashes. That's the prime reason for the high failure rates in the infamous IBM Desktar line of harddrives a few years back. Even worse is having your drive spin up and down every half hour, as spinning up is tremendously stressing on the drive mechanics. It's better to leave a harddrive running, than letting it spin down 10 times a day for instance.

---

### Post by Peturrr on 2006-09-02
Thanks you for this excellent reply!

---

