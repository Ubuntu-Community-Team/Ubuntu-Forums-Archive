---
title: "Iptables logging not logging failed connections"
date: 2016-11-15
forum: Security
---

### Post by John_Creane on 2016-11-15
I've set up logging to log any packets dropped on the INPUT chain, 

This is the script I'm running to manage iptables 

```
iptables --flush 

iptables  -P INPUT DROP
iptables  -P OUTPUT ACCEPT
iptables  -P FORWARD ACCEPT


# Allow unrestricted traffic on the loopback interface

iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT 

# Stateful Packet Inspection - So that traffic that goes out can come back in through the firewall

iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT


# Inbound Rules 

# Access to all ports - Management 

iptables -I INPUT -s 192.168.0.20 -j ACCEPT
iptables -I INPUT -s 192.168.0.69 -j ACCEPT

# SSH

#iptables -I INPUT -p tcp -s 192.168.0.0/24  --dport 22 -j ACCEPT
iptables -I INPUT -p tcp -s 192.168.1.0/24  --dport 22 -j ACCEPT

# Plex 

iptables -I INPUT -p tcp -s 192.168.0.0/24  --dport 32400 -j ACCEPT
iptables -I INPUT -p tcp -s 192.168.1.0/24  --dport 32400 -j ACCEPT

# NTP 

iptables -I INPUT -p udp -s 0.0.0.0  --dport 123 -j ACCEPT


# Logging

iptables -N LOGGING
iptables -A INPUT -j LOGGING
iptables -A LOGGING -m limit --limit 2/min -j LOG --log-prefix "IPTables-Dropped: " --log-level 4
iptables -A LOGGING -j DROP


```

I attempt to SSH to this server (IP is 192.168.0.70) from 192.168.0.2 which isn't allowed by iptables & the connection is refused however when I tail the /var/log/iptables/iptables.log it doesn't list this failed connection, I see nothing for DPT=22, DST=192.168.0.70. 

This is the only mention of 192.168.0.70 in the logs, 

```
cat /var/log/iptables/iptables.log | grep 192.168.0.70
Nov 16 02:33:56 server kernel: IPTables-Dropped: IN=eno16777736 OUT= MAC= SRC=192.168.0.70 DST=192.168.0.255 LEN=217 TOS=0x00 PREC=0x00 TTL=64 ID=3781 DF PROTO=UDP SPT=138 DPT=138 LEN=197 
Nov 16 02:41:25 server kernel: IPTables-Dropped: IN=eno16777736 OUT= MAC= SRC=192.168.0.70 DST=192.168.0.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=3872 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
Nov 16 02:47:56 server kernel: IPTables-Dropped: IN=eno16777736 OUT= MAC= SRC=192.168.0.70 DST=192.168.0.255 LEN=256 TOS=0x00 PREC=0x00 TTL=64 ID=3885 DF PROTO=UDP SPT=138 DPT=138 LEN=236 
Nov 16 02:55:26 server kernel: IPTables-Dropped: IN=eno16777736 OUT= MAC= SRC=192.168.0.70 DST=192.168.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=3911 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Nov 16 04:20:25 server kernel: IPTables-Dropped: IN=eno16777736 OUT= MAC= SRC=192.168.0.70 DST=192.168.0.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=46624 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
Nov 16 04:20:25 server kernel: IPTables-Dropped: IN=eno16777736 OUT= MAC= SRC=192.168.0.70 DST=192.168.0.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=46625 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
Nov 16 04:20:25 server kernel: IPTables-Dropped: IN=eno16777736 OUT= MAC= SRC=192.168.0.70 DST=192.168.0.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=46626 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
Nov 16 04:20:25 server kernel: IPTables-Dropped: IN=eno16777736 OUT= MAC= SRC=192.168.0.70 DST=192.168.0.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=46627 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
Nov 16 04:20:25 server kernel: IPTables-Dropped: IN=eno16777736 OUT= MAC= SRC=192.168.0.70 DST=192.168.0.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=46628 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
Nov 16 04:20:55 server kernel: IPTables-Dropped: IN=eno16777736 OUT= MAC= SRC=192.168.0.70 DST=192.168.0.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=46659 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
```

Any ideas wha'ts going on folks :confused:?

---

### Post by SeijiSensei on 2016-11-16
Why do you have a rate limit in the rule?  Single connection attempts won't hit that rule.  Try removing the "-m limit limit 2/min" parameters and see how that works.

---

### Post by John_Creane on 2016-11-17
Thanks making that change has allowed me to see the dropped SSH connections that IPtables is blocking.  


```
[root@server scripts]# cat /var/log/iptables/iptables.log | grep DST=192.168.0.70
Nov 17 07:58:53 server kernel: IPTables-Dropped: IN=eno16777736 OUT= MAC=00:0c:29:02:97:04:00:19:bb:d1:cc:a2:08:00 SRC=192.168.0.2 DST=192.168.0.70 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=64607 DF PROTO=TCP SPT=50176 DPT=22 WINDOW=29200 RES=0x00 SYN URGP=0 

```

I have a question though why is it logging the items below, as I thought it would only log traffic where the destination was this server (IP=192.168.0.70) but it's logging traffic where the source is another server on my network (192.168.0.2) going to the broadcast address 192.168.0.255

```

Nov 17 08:05:02 server kernel: IPTables-Dropped: IN=eno16777736 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:bb:d1:cc:a2:08:00 SRC=192.168.0.2 DST=192.168.0.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=3157 DF PROTO=UDP SPT=51843 DPT=32414 LEN=29 
Nov 17 08:05:03 server kernel: IPTables-Dropped: IN=eno16777736 OUT= MAC=ff:ff:ff:ff:ff:ff:80:2a:a8:16:b5:6c:08:00 SRC=192.168.0.253 DST=255.255.255.255 LEN=174 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=41650 DPT=10001 LEN=154 
Nov 17 08:05:07 server kernel: IPTables-Dropped: IN=eno16777736 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:bb:d1:cc:a2:08:00 SRC=192.168.0.2 DST=192.168.0.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=3713 DF PROTO=UDP SPT=45743 DPT=32412 LEN=29 
Nov 17 08:05:07 server kernel: IPTables-Dropped: IN=eno16777736 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:bb:d1:cc:a2:08:00 SRC=192.168.0.2 DST=192.168.0.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=3714 DF PROTO=UDP SPT=51843 DPT=32414 LEN=29 
Nov 17 08:05:12 server kernel: IPTables-Dropped: IN=eno16777736 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:bb:d1:cc:a2:08:00 SRC=192.168.0.2 DST=192.168.0.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=4818 DF PROTO=UDP SPT=45743 DPT=32412 LEN=29 
Nov 17 08:05:12 server kernel: IPTables-Dropped: IN=eno16777736 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:bb:d1:cc:a2:08:00 SRC=192.168.0.2 DST=192.168.0.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=4819 DF PROTO=UDP SPT=51843 DPT=32414 LEN=29 


```

---

### Post by untrustytahr on 2016-11-17
> **John_Creane said:**
> 
I have a question though why is it logging the items below, as I thought it would only log traffic where the destination was this server (IP=192.168.0.70) but it's logging traffic where the source is another server on my network (192.168.0.2) going to the broadcast address 192.168.0.255



 ```

iptables -A INPUT -j LOGGING
iptables -A LOGGING -m limit --limit 2/min -j LOG --log-prefix "IPTables-Dropped: " --log-level 4
iptables -A LOGGING -j DROP
```

Because you told it to.  This setup sends all traffic hitting the INPUT table that didn't match the earlier rules to the LOGGING table.  The logging table is sending it all to the LOG target (-j LOG) where it gets logged with your prefix.  It then proceeds to drop it.  So basically you're logging any/all input traffic that didn't match any rules.  The reason you only saw the broadcast traffic initially is because you met the rate limit threshold.  Now everything will meet it (no rate limit).

If you are going to set up a discreet firewall log for firewall messages, you may want to make sure you setup logrotate to keep the file under control.  They can fill up fast.

---

### Post by SeijiSensei on 2016-11-18
Every machine on the network sees traffic addressed to 192.168.0.255.  If you don't want to log broadcasts, just add another rule:

```

iptables -A INPUT -d 192.168.0.255 -j ACCEPT   # accept broadcasts but don't log
iptables -N LOGGING
iptables -A INPUT -j LOGGING
iptables -A LOGGING -j LOG --log-prefix "IPTables-Dropped: " --log-level 4
iptables -A LOGGING -j DROP

```

---

