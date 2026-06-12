---
title: "Too many perls ..."
date: 2005-11-07
forum: Server Platforms
---

### Post by dbee on 2005-11-07
So I did a
```

netstat -np -p -l

```
and I was a bit surprised to find that I had 4 open perl ports... 
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:20000           0.0.0.0:*               LISTEN     6578/perl
tcp        0      0 127.0.0.1:587           0.0.0.0:*               LISTEN     6569/sendmail: MTA:
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN     6579/perl
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     7140/cupsd
tcp        0      0 0.0.0.0:1241            0.0.0.0:*               LISTEN     7236/nessusd: waiti
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     6569/sendmail: MTA:
tcp6       0      0 :::80                   :::*                    LISTEN     6635/apache2
tcp6       0      0 :::22                   :::*                    LISTEN     6470/sshd
udp        0      0 0.0.0.0:10000           0.0.0.0:*                          6579/perl
udp        0      0 0.0.0.0:20000           0.0.0.0:*                          6578/perl
udp        0      0 0.0.0.0:68              0.0.0.0:*                          4856/dhclient3

```
... I use this computer as a desktop so I have all kinda stuff loaded on to it ... but I can't imagine why I'd need four perl ports ...

also why doesn't the -p all work in iptables 
```

iptables -A OUTPUT -p all --sports 6578,6579 -j DROP

```
... doesn't work for some reason, but 
```

iptables -A INPUT -p tcp --sports 6578,6579 -j DROP

```
works fine ???

---

