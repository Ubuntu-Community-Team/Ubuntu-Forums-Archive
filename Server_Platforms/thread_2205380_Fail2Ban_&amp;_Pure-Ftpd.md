---
title: "Fail2Ban &amp; Pure-Ftpd"
date: 2014-02-13
forum: Server Platforms
---

### Post by matt59 on 2014-02-13
I have pure-ftpd running on web server with Fail2Ban. Fail2Ban is letting apache2 connections in but are denying any FTP connection from anything but local host. I have attempted to modify the jail.local and jail.conf files but I am still having issues.

Here is the pure-ftpd section of my jail.local file:

```

[pure-ftpd]
enabled = true
port     = ftp,ftp-data,ftps,ftps-data
filter   = pure-ftpd
logpath  = /var/log/auth.log
maxretry = 6

```

Here is a view of my iptables -L -n:

```

Chain INPUT (policy DROP)
target     prot opt source               destination
fail2ban-postfix  tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 80,443,25,587,110,995,143,993,4190
fail2ban-dovecot  tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 80,443,25,587,110,995,143,993,4190
fail2ban-roundcube  tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 80,443,25,587,110,995,143,993,4190
fail2ban-ssh  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22
fail2ban-pure-ftpd  tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 21,20,990,989
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:80
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:443
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:25
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:587
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:110
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:995
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:143
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:993
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8

Chain FORWARD (policy DROP)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain fail2ban-dovecot (1 references)
target     prot opt source               destination
RETURN     all  --  0.0.0.0/0            0.0.0.0/0

Chain fail2ban-postfix (1 references)
target     prot opt source               destination
RETURN     all  --  0.0.0.0/0            0.0.0.0/0

Chain fail2ban-pure-ftpd (1 references)
target     prot opt source               destination
RETURN     all  --  0.0.0.0/0            0.0.0.0/0

Chain fail2ban-roundcube (1 references)
target     prot opt source               destination
RETURN     all  --  0.0.0.0/0            0.0.0.0/0

Chain fail2ban-ssh (1 references)
target     prot opt source               destination
RETURN     all  --  0.0.0.0/0            0.0.0.0/0

```

If I run the following commands manually FTP works, but I really want to get this working with Fail2Ban:
```

iptables -A INPUT -p tcp --dport 21 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 20 -j ACCEPT

```

Any idea what is going on?

---

