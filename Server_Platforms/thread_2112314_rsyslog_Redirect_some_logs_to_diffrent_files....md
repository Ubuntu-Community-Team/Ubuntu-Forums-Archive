---
title: "rsyslog: Redirect some logs to diffrent files..."
date: 2013-02-04
forum: Server Platforms
---

### Post by emil.s on 2013-02-04
Hello!

I'm trying to set split my logs to some different files for easier reading and troubleshooting.
I have been reading a lot of howtos and guides, and of course the official documentation...

I have ended up with this in my /etc/rsyslog.d/10-emil.conf
```
root@Lord-Dvorak: /etc/rsyslog.d #> cat 10-emil.conf 
:syslogfacility, regex, "dhclient*" -/var/log/network/dhcp.log
:rawmsg, regex, "dhclient*" -/var/log/network/dhcp.log
:rawmsg, contains, "DHCPREQUEST" -/var/log/network/dhcp.log
:rawmsg, contains, "DHCPREQUEST" /var/log/network/dhcp.log
:msg, contains, "iptables" /var/log/network/iptables.log
:msg, contains, "iptables: " -/var/log/iptables.log
```

The last line is just a copy-past from this site:
[http://blog.shadypixel.com/log-iptables-messages-to-a-separate-file-with-rsyslog/](http://blog.shadypixel.com/log-iptables-messages-to-a-separate-file-with-rsyslog/)

However, nothing works...

I have these lines in syslog:
```

Feb  4 17:18:28 localhost dhclient: DHCPREQUEST of 193.11.xxx.xxx on br-net to 193.11.xxx.xxx port 67
Feb  4 17:16:57 localhost kernel: [2325862.867525] iptables: IN=server_link OUT= MAC=45:30:00:68:00:00:40:00:32:04:c6:0d:5b:5f:e0:c6:c1:0b:85:23:45:00:00:54:00:00:40:00:40:01:25:df:0a:64 SRC=10.100.0.2 DST=10.100.0.1 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=25162 SEQ=51030 
Feb  4 17:16:57 localhost kernel: [2325862.867541] iptables IN=server_link OUT= MAC=45:30:00:68:00:00:40:00:32:04:c6:0d:5b:5f:e0:c6:c1:0b:85:23:45:00:00:54:00:00:40:00:40:01:25:df:0a:64 SRC=10.100.0.2 DST=10.100.0.1 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=25162 SEQ=51030

```

I have been trying a lot of different variants of all matching-statements, but I'm still pretty sure that ":msg, contains, "iptables" /var/log/network/iptables.log" definitely should match "Feb  4 17:16:57 localhost kernel: [2325862.867525] iptables: IN=server_link OUT=....."

So I guess that something else is wrong... but what!?

---

