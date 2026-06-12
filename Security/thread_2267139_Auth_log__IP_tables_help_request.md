---
title: "Auth log / IP tables help request"
date: 2015-02-27
forum: Security
---

### Post by vRanger on 2015-02-27
Need a pointer.  Have an email server I've neglected for 6 months, and I'm suspicious that there are no failed login attempts showing up in the auth.log.  However, I vaguely recall doing something to block everything, but can't remember what I did, if anything.  I just remember that fail2ban would routinely log messages showing failed login attempts, and now it is not.  Here is the sudo iptables -L output: could a kind person tell me if there is a line that is effectively blocking all outside connection attempts. Or is there something else I should consider? Thanks!

> 

Chain INPUT (policy DROP)
target     prot opt source               destination
fail2ban-postfix  tcp  --  anywhere             anywhere             multiport dports http,https,smtp,submission,pop3,pop3s,imap2,imaps,sieve
fail2ban-dovecot  tcp  --  anywhere             anywhere             multiport dports http,https,smtp,submission,pop3,pop3s,imap2,imaps,sieve
fail2ban-roundcube  tcp  --  anywhere             anywhere             multiport dports http,https,smtp,submission,pop3,pop3s,imap2,imaps,sieve
fail2ban-ssh  tcp  --  anywhere             anywhere             tcp dpt:ssh
fail2ban-roundcube  tcp  --  anywhere             anywhere             multiport dports http,https,smtp,submission,pop3,pop3s,imap2,imaps,sieve
fail2ban-dovecot  tcp  --  anywhere             anywhere             multiport dports http,https,smtp,submission,pop3,pop3s,imap2,imaps,sieve
fail2ban-postfix  tcp  --  anywhere             anywhere             multiport dports http,https,smtp,submission,pop3,pop3s,imap2,imaps,sieve
fail2ban-ssh  tcp  --  anywhere             anywhere             tcp dpt:ssh
fail2ban-postfix  tcp  --  anywhere             anywhere             multiport dports http,https,smtp,submission,pop3,pop3s,imap2,imaps,sieve
fail2ban-dovecot  tcp  --  anywhere             anywhere             multiport dports http,https,smtp,submission,pop3,pop3s,imap2,imaps,sieve
fail2ban-roundcube  tcp  --  anywhere             anywhere             multiport dports http,https,smtp,submission,pop3,pop3s,imap2,imaps,sieve
fail2ban-ssh  tcp  --  anywhere             anywhere             tcp dpt:ssh
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  116.10.191.0/24      anywhere
DROP       all  --  61.0.0.0/8           anywhere
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:smtp
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:submission
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt: pop3
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt: pop3s
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:imap2
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:imaps
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request

Chain FORWARD (policy DROP)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain fail2ban-dovecot (3 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere

Chain fail2ban-postfix (3 references)
target     prot opt source               destination
DROP       all  --  pixmapt-33-f74.oklands.net  anywhere
DROP       all  --  net-91-81-64-210.cust.vodafonedsl.it  anywhere
DROP       all  --  smart-taberei.cluj.astral.ro  anywhere
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere

Chain fail2ban-roundcube (3 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere

Chain fail2ban-ssh (3 references)
target     prot opt source               destination
DROP       all  --  23.97.225.181        anywhere
DROP       all  --  server1258.inovacaowebsystem.com.br  anywhere
DROP       all  --  106.245.228.35       anywhere
DROP       all  --  123.127.240.21       anywhere
DROP       all  --  115.238.236.77       anywhere
DROP       all  --  31.186.12.250        anywhere
DROP       all  --  68-68-2-182.applecreek.pathcom.com  anywhere
DROP       all  --  65.19.156.239        anywhere
DROP       all  --  212-129-8-84.rev.poneytelecom.eu  anywhere
DROP       all  --  180.179.172.131      anywhere
DROP       all  --  srv153.dedi64.de     anywhere
DROP       all  --  58.83.146.252        anywhere
DROP       all  --  117.79.91.244        anywhere
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere



---

### Post by Doug S on 2015-02-27
I'm finding your post hard to read, but no I don't see any problem.. Could you do me a favor and post the output from this:```
sudo iptables -v -x -n -L
```inside of CODE tags (the # in the menu).
Do you see anything in /var/log/mail.log? or mail.err?

Edit: Is your mail server listening?```
doug@doug-64:~$ [COLOR=#ff0000]sudo netstat -lnpt[/COLOR]
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      1856/smbd
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1498/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      1856/smbd
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1613/apache2
tcp        0      0 173.180.XXX.YYY:53 0.0.0.0:*               LISTEN      1480/named
tcp        0      0 192.168.111.1:53        0.0.0.0:*               LISTEN      1480/named
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1480/named
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1314/sshd
[COLOR=#ff0000]tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1711/master[/COLOR]
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      1480/named
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      1613/apache2
```

---

### Post by vRanger on 2015-03-02
The concern is the system has been hacked and now isn't logging authentication information as expected.  I would expect many entries in auth.log showing failed attempts and IP addresses, and for iptables to have hundreds of ip addresses at this point from permanent fail2ban entries (f2b is set to fail permanently after three attempts).

**>Is your mail server listening?**
Yes, I have that line for port 25.  The email server is functioning as expected.  This is more of an ssh question, and is using port 22.

[B]>sudo iptables -v -x -n -L
> [/B]
Chain INPUT (policy DROP 20441878 packets, 1736812812 bytes)
    pkts      bytes target     prot opt in     out     source               destination
  330543 39443298 fail2ban-postfix  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 80,443,25,587,110,995,143,993,4190
  330543 39443298 fail2ban-dovecot  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 80,443,25,587,110,995,143,993,4190
  330543 39443298 fail2ban-roundcube  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 80,443,25,587,110,995,143,993,4190
   11730  2068308 fail2ban-ssh  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
  330543 39443298 fail2ban-roundcube  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 80,443,25,587,110,995,143,993,4190
  330543 39443298 fail2ban-dovecot  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 80,443,25,587,110,995,143,993,4190
  330543 39443298 fail2ban-postfix  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 80,443,25,587,110,995,143,993,4190
   11730  2068308 fail2ban-ssh  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
  330543 39443298 fail2ban-postfix  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 80,443,25,587,110,995,143,993,4190
  330543 39443298 fail2ban-dovecot  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 80,443,25,587,110,995,143,993,4190
  330543 39443298 fail2ban-roundcube  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 80,443,25,587,110,995,143,993,4190
   11730  2068308 fail2ban-ssh  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
 1566690 531424144 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
   27309  1631920 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
       0        0 DROP       all  --  *      *       116.10.191.0/24      0.0.0.0/0
       0        0 DROP       all  --  *      *       61.0.0.0/8           0.0.0.0/0
       5      276 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80
   19739  1026420 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:443
     183    10188 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:25
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:587
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:110
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:995
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:143
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:993
       5      260 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
  101514  5001273 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 1606714 packets, 193181593 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain fail2ban-dovecot (3 references)
    pkts      bytes target     prot opt in     out     source               destination
  991629 118329894 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain fail2ban-postfix (3 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 DROP       all  --  *      *       198.204.227.226      0.0.0.0/0
       0        0 DROP       all  --  *      *       91.81.64.210         0.0.0.0/0
       0        0 DROP       all  --  *      *       89.137.17.19         0.0.0.0/0
  991629 118329894 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain fail2ban-roundcube (3 references)
    pkts      bytes target     prot opt in     out     source               destination
  991629 118329894 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain fail2ban-ssh (3 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 DROP       all  --  *      *       23.97.225.181        0.0.0.0/0
       0        0 DROP       all  --  *      *       173.242.113.169      0.0.0.0/0
       0        0 DROP       all  --  *      *       106.245.228.35       0.0.0.0/0
       0        0 DROP       all  --  *      *       123.127.240.21       0.0.0.0/0
       0        0 DROP       all  --  *      *       115.238.236.77       0.0.0.0/0
       0        0 DROP       all  --  *      *       31.186.12.250        0.0.0.0/0
       0        0 DROP       all  --  *      *       68.68.2.182          0.0.0.0/0
       0        0 DROP       all  --  *      *       65.19.156.239        0.0.0.0/0
       0        0 DROP       all  --  *      *       212.129.8.84         0.0.0.0/0
       0        0 DROP       all  --  *      *       180.179.172.131      0.0.0.0/0
       0        0 DROP       all  --  *      *       80.244.247.98        0.0.0.0/0
       0        0 DROP       all  --  *      *       58.83.146.252        0.0.0.0/0
       0        0 DROP       all  --  *      *       117.79.91.244        0.0.0.0/0
   35190  6204924 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0



---

### Post by vRanger on 2015-03-02
Found it.  Examined all installed programs 
      dpkg -l
found entry
      "ii  denyhosts                              2.6-10                                 Utility to help sys admins thwart SSH crackers"
googled and found denyhosts stores ip addresses in 
      cat /etc/hosts.deny
Found a long list of IP's
Checked my change log, and found I had installed it last May, I just didn't see that the first time I checked my change log.

So it looks like denyhosts is blocking "all" of the offenders at this point which is why I'm not seeing failed log attempts.

Thanks so much for your reply!

---

