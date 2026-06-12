---
title: "iptables &amp; knockd"
date: 2014-10-16
forum: Security
---

### Post by info24 on 2014-10-16
Hi,


I'm trying to add a port knocking feature on my server but I'm failing at it. I've been through several documents online doing research to what I might do wrong, but I can't find it.    It is suppose to go on my external server, but since I couldn't figure it out, i'm simulating it now on a virtual server.

It's a clean install of ubuntu server 14.04 LTS
To test the environment I setup a configuration on the knockd daemon to allow or deny ping request. This way I can startup a continuously ping job on my remote machine so i can instantly see the effect.

The configuration i have for iptables is as followed
# iptables -F
# iptables --policy INPUT DROP
# iptables -A INPUT -p tcp --dport 22 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

My /etc/knockd.conf file:
```

**root@ubuntu**:**/home/vmadmin**# cat /etc/knockd.conf 
[options]
LogFile = /var/log/knockd.log


[AllowPING]
    sequence    = 7000,8000,9000
    seq_timeout = 5
    command     = /sbin/iptables -A INPUT -p icmp --icmp-type 8 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
    tcpflags    = syn

```

# /etc/init.d/knockd stop
# /etc/init.d/knockd start

From my remote system I ran the knock command with the sequence listed above, but nothing appears to happen, the ping requests still times out. If I run the command to allow the ping request manually, the ping gets through. So I know it works, but for some reason, my knock isn't getting through. 

```

**steve@steves-mbp:~**$ knock -v 192.168.56.101 7000 8000 9000
hitting tcp 192.168.56.101:7000
hitting tcp 192.168.56.101:8000
hitting tcp 192.168.56.101:9000

```

The log file doesn't say anything either, only that it is listening on eth0:

/var/log/knockd.log
[2014-10-16 14:41] starting up, listening on eth0



Is there anyone that can help me finding out what's wrong with this?
Thank you.

---

### Post by info24 on 2014-10-16
Got it working with the command
knock 192.168.56.101 7000:tcp 8000:tcp 9000:tcp

So why doesn't the command work without explicitly defining tcp after each port?  bug in the knock command?

It makes no sense.

---

