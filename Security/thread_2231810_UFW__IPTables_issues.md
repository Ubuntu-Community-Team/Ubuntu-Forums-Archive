---
title: "UFW / IPTables issues"
date: 2014-06-28
forum: Security
---

### Post by ohiknow on 2014-06-28
Can someone help me understand how this is happening:

```

jeremy:/var/log/named$ sudo netstat -taupen

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode       PID/Program name
udp        0      0 10.0.0.55:36466         [COLOR=#ff0000]37.209.196.5:53[/COLOR]         ESTABLISHED 109        6523645     14500/named
udp        0      0 10.0.0.55:35461         [COLOR=#ff0000]37.209.196.5:53 [/COLOR]        ESTABLISHED 109        6523642     14500/named
udp        0      0 10.0.0.55:25271         [COLOR=#ff0000]37.209.196.5:53 [/COLOR]        ESTABLISHED 109        6523641     14500/named
udp        0      0 10.0.0.55:42382         [COLOR=#ff0000]37.209.196.5:53 [/COLOR]        ESTABLISHED 109        6523646     14500/named



```

when i have this setup:

```

jeremy:/var/log/named$ sudo ufw status numbered

Status: active


     To                         Action      From
     --                         ------      ----
[ 1] Anywhere                   DENY IN     177.11.51.70
[COLOR=#ff0000][ 2] 37.0.0.0/8                 DENY IN     Anywhere[/COLOR]
[COLOR=#ff0000][ 3] Anywhere                   DENY IN     37.0.0.0/8[/COLOR]
[ 4] 46.182.218.140             DENY IN     Anywhere
[ 5] Anywhere                   DENY IN     46.182.218.140
[ 6] 119.107.200.24             DENY IN     Anywhere
[ 7] Anywhere                   DENY IN     119.107.200.24
[COLOR=#ff0000][ 8] 53                         DENY IN     37.0.0.0/8[/COLOR]
[ 9] 53                         DENY IN     119.107.200.24
[10] Anywhere                   ALLOW IN    10.0.0.0/24
[11] 80                         ALLOW IN    Anywhere
[12] 53                         ALLOW IN    Anywhere
[13] 953                        ALLOW IN    Anywhere
[14] 25                         ALLOW IN    Anywhere
[15] 143                        ALLOW IN    Anywhere
[16] 993                        ALLOW IN    Anywhere
[17] 587                        ALLOW IN    Anywhere
[18] 465                        ALLOW IN    Anywhere
[19] 110                        ALLOW IN    Anywhere
[20] 995                        ALLOW IN    Anywhere
[21] 1279                       ALLOW IN    Anywhere
[22] 22                         ALLOW IN    Anywhere
[23] 443                        ALLOW IN    Anywhere
[24] 80                         ALLOW IN    Anywhere (v6)
[25] 53                         ALLOW IN    Anywhere (v6)
[26] 953                        ALLOW IN    Anywhere (v6)
[27] 25                         ALLOW IN    Anywhere (v6)
[28] 143                        ALLOW IN    Anywhere (v6)
[29] 993                        ALLOW IN    Anywhere (v6)
[30] 587                        ALLOW IN    Anywhere (v6)
[31] 465                        ALLOW IN    Anywhere (v6)
[32] 110                        ALLOW IN    Anywhere (v6)
[33] 995                        ALLOW IN    Anywhere (v6)
[34] 1279                       ALLOW IN    Anywhere (v6)
[35] 22                         ALLOW IN    Anywhere (v6)
[36] 443                        ALLOW IN    Anywhere (v6)



```

UFW has been reloaded after adding rules, not sure what else to do.

Thanks.

---

### Post by SeijiSensei on 2014-06-28
Unless you look at the entire iptables ruleset with "sudo iptables -L -nv" you won't know the answer to this.

Perhaps the rules you have only apply to TCP traffic; DNS requests use UDP.

---

### Post by ohiknow on 2014-06-29
From iptables -L -nv

```
Chain INPUT (policy DROP 0 packets, 0 bytes) pkts bytes target     prot opt in     out     source               destination
 1650  167K fail2ban-dovecot  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 25,465,143,220,993,110,995
 1650  167K fail2ban-sasl  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 25,465,143,220,993,110,995
 1620  166K fail2ban-courierauth  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 25,465,143,220,993,110,995
  580 71135 fail2ban-couriersmtp  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 25,465
  580 71135 fail2ban-postfix  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 25,465
 210K   15M fail2ban-apache  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 80,443
 6612  317K fail2ban-ssh  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 22
 491K   71M ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
 491K   71M ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
 3096 1172K ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    4   278 ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    4   278 ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    4   278 ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ufw-before-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 ufw-after-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 ufw-reject-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
 445K  133M ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0
 445K  133M ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0
 153K   12M ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0
 153K   12M ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0
 153K   12M ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0
 153K   12M ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain fail2ban-apache (1 references)
 pkts bytes target     prot opt in     out     source               destination
 210K   15M RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain fail2ban-courierauth (1 references)
 pkts bytes target     prot opt in     out     source               destination
 1620  166K RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain fail2ban-couriersmtp (1 references)
 pkts bytes target     prot opt in     out     source               destination
  580 71135 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain fail2ban-dovecot (1 references)
 pkts bytes target     prot opt in     out     source               destination
 1650  167K RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain fail2ban-postfix (1 references)
 pkts bytes target     prot opt in     out     source               destination
  580 71135 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain fail2ban-sasl (1 references)
 pkts bytes target     prot opt in     out     source               destination
 1620  166K RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain fail2ban-ssh (1 references)
 pkts bytes target     prot opt in     out     source               destination
 6612  317K RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-after-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-after-input (1 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:137
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:138
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:139
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:445
 3092 1171K ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:67
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:68
    0     0 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST


Chain ufw-after-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "


Chain ufw-after-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "


Chain ufw-after-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-after-output (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-before-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination
37001 3744K ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
 295K   50M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
   12   517 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            state INVALID
   12   517 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            state INVALID
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 4
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
    1    60 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
    5  1689 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp spt:67 dpt:68
 159K   17M ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            224.0.0.251          udp dpt:5353
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            239.255.255.250      udp dpt:1900
 159K   17M ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-before-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-before-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-before-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination
37001 3744K ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0
 255K  118M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
 153K   12M ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-logging-allow (0 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW ALLOW] "


Chain ufw-logging-deny (2 references)
 pkts bytes target     prot opt in     out     source               destination
   11   440 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state INVALID limit: avg 3/min burst 10
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "


Chain ufw-not-local (1 references)
 pkts bytes target     prot opt in     out     source               destination
 113K 7688K RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type LOCAL
  972 31104 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type MULTICAST
45107 9528K RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-reject-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-reject-input (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-reject-output (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-skip-to-policy-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-skip-to-policy-input (7 references)
 pkts bytes target     prot opt in     out     source               destination
 3092 1171K DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-skip-to-policy-output (0 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-track-input (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-track-output (1 references)
 pkts bytes target     prot opt in     out     source               destination
  250 14980 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            state NEW
 153K   12M ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            state NEW


Chain ufw-user-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 DROP       all  --  *      *       177.11.51.70         0.0.0.0/0
    0     0 DROP       all  --  *      *       0.0.0.0/0            37.0.0.0/8
    0     0 DROP       all  --  *      *       37.0.0.0/8           0.0.0.0/0
    0     0 DROP       all  --  *      *       0.0.0.0/0            46.182.218.140
    0     0 DROP       all  --  *      *       46.182.218.140       0.0.0.0/0
    0     0 DROP       all  --  *      *       0.0.0.0/0            119.107.200.24
    0     0 DROP       all  --  *      *       119.107.200.24       0.0.0.0/0
    0     0 DROP       tcp  --  *      *       37.0.0.0/8           0.0.0.0/0            tcp dpt:53
    0     0 DROP       udp  --  *      *       37.0.0.0/8           0.0.0.0/0            udp dpt:53
    0     0 DROP       tcp  --  *      *       119.107.200.24       0.0.0.0/0            tcp dpt:53
    0     0 DROP       udp  --  *      *       119.107.200.24       0.0.0.0/0            udp dpt:53
 132K   15M ACCEPT     all  --  *      *       10.0.0.0/24          0.0.0.0/0
22657 1358K ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:80
  147  5880 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:53
 1854  136K ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:53
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:953
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:953
   28  1408 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:25
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:25
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:143
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:143
   17  1088 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:993
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:993
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:587
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:587
    6   340 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:465
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:465
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:110
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:110
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:995
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:995
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:1279
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:1279
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:22
    8   432 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:443
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:443


Chain ufw-user-limit (0 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 5 LOG flags 0 level 4 prefix "[UFW LIMIT BLOCK] "
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable


Chain ufw-user-limit-accept (0 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0



```

---

### Post by untrustytahr on 2014-06-29
> **ohiknow said:**
> Can someone help me understand how this is happening:



Your DNS made the request to root server.  UFW by default sets up stateful connections so it won't block the incoming response.  You would need to block the outgoing (or tweak your DNS root servers-- i dont mess much with dns on linux... one area where I prefer MS-- that hurt:mad:)

---

### Post by ohiknow on 2014-06-30
Even though I'm dropping incoming and outgoing?

```

[COLOR=#000000][FONT=Ubuntu Mono]Chain ufw-user-input (1 references)[/FONT][/COLOR] 
pkts bytes target     prot opt in     out     source               destination
[COLOR=#ff0000]0     0 DROP       all  --  *      *       0.0.0.0/0            37.0.0.0/8
0     0 DROP       all  --  *      *       37.0.0.0/8           0.0.0.0/0[/COLOR]

```

---

### Post by untrustytahr on 2014-06-30
Yes... follow the red.

BTW... INPUT & OUTPUT are very different than source & destination.

> **ohiknow said:**
> From iptables -L -nv

```
Chain INPUT (policy DROP 0 packets, 0 bytes) pkts bytes target     prot opt in     out     source               destination
 1650  167K fail2ban-dovecot  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 25,465,143,220,993,110,995
 1650  167K fail2ban-sasl  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 25,465,143,220,993,110,995
 1620  166K fail2ban-courierauth  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 25,465,143,220,993,110,995
  580 71135 fail2ban-couriersmtp  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 25,465
  580 71135 fail2ban-postfix  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 25,465
 210K   15M fail2ban-apache  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 80,443
 6612  317K fail2ban-ssh  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 22
 491K   71M ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
 [SIZE=2][COLOR=#ff0000]**491K   71M ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0**[/COLOR][/SIZE]
 3096 1172K ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    4   278 ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    4   278 ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    4   278 ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ufw-before-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 ufw-after-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 ufw-reject-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
 445K  133M ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0
 445K  133M ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0
 153K   12M ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0
 153K   12M ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0
 153K   12M ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0
 153K   12M ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain fail2ban-apache (1 references)
 pkts bytes target     prot opt in     out     source               destination
 210K   15M RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain fail2ban-courierauth (1 references)
 pkts bytes target     prot opt in     out     source               destination
 1620  166K RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain fail2ban-couriersmtp (1 references)
 pkts bytes target     prot opt in     out     source               destination
  580 71135 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain fail2ban-dovecot (1 references)
 pkts bytes target     prot opt in     out     source               destination
 1650  167K RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain fail2ban-postfix (1 references)
 pkts bytes target     prot opt in     out     source               destination
  580 71135 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain fail2ban-sasl (1 references)
 pkts bytes target     prot opt in     out     source               destination
 1620  166K RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain fail2ban-ssh (1 references)
 pkts bytes target     prot opt in     out     source               destination
 6612  317K RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-after-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-after-input (1 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:137
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:138
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:139
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:445
 3092 1171K ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:67
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:68
    0     0 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST


Chain ufw-after-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "


Chain ufw-after-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "


Chain ufw-after-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-after-output (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-before-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination
37001 3744K ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
 [COLOR=#ff0000]**[SIZE=2]295K   50M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED[/SIZE]**[/COLOR]
   12   517 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            state INVALID
   12   517 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            state INVALID
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 4
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
    1    60 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
    5  1689 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp spt:67 dpt:68
 159K   17M ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            224.0.0.251          udp dpt:5353
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            239.255.255.250      udp dpt:1900
 159K   17M ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0  [COLOR=#ff0000][SIZE=2]**<-- This is where you jump to ufw-user-input chain but packet was already accepted**[/SIZE][/COLOR]


Chain ufw-before-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-before-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-before-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination
37001 3744K ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0
 255K  118M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
 153K   12M ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-logging-allow (0 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW ALLOW] "


Chain ufw-logging-deny (2 references)
 pkts bytes target     prot opt in     out     source               destination
   11   440 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state INVALID limit: avg 3/min burst 10
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "


Chain ufw-not-local (1 references)
 pkts bytes target     prot opt in     out     source               destination
 113K 7688K RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type LOCAL
  972 31104 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type MULTICAST
45107 9528K RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-reject-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-reject-input (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-reject-output (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-skip-to-policy-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-skip-to-policy-input (7 references)
 pkts bytes target     prot opt in     out     source               destination
 3092 1171K DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-skip-to-policy-output (0 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-track-input (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-track-output (1 references)
 pkts bytes target     prot opt in     out     source               destination
  250 14980 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            state NEW
 153K   12M ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            state NEW


Chain ufw-user-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-user-input (1 references)
[COLOR=#ff0000][SIZE=2]** pkts bytes**[/SIZE][/COLOR] target     prot opt in     out     source               destination
    0     0 DROP       all  --  *      *       177.11.51.70         0.0.0.0/0
    [COLOR=#ff0000][SIZE=2]**0     0**[/SIZE][/COLOR] DROP       all  --  *      *       0.0.0.0/0            37.0.0.0/8  [COLOR=#ff0000][SIZE=2]**<----These rules never match**[/SIZE][/COLOR]
   [COLOR=#ff0000][SIZE=2] 0     0[/SIZE][/COLOR] DROP       all  --  *      *       37.0.0.0/8           0.0.0.0/0
    0     0 DROP       all  --  *      *       0.0.0.0/0            46.182.218.140
    0     0 DROP       all  --  *      *       46.182.218.140       0.0.0.0/0
    0     0 DROP       all  --  *      *       0.0.0.0/0            119.107.200.24
    0     0 DROP       all  --  *      *       119.107.200.24       0.0.0.0/0
    0     0 DROP       tcp  --  *      *       37.0.0.0/8           0.0.0.0/0            tcp dpt:53
    0     0 DROP       udp  --  *      *       37.0.0.0/8           0.0.0.0/0            udp dpt:53
    0     0 DROP       tcp  --  *      *       119.107.200.24       0.0.0.0/0            tcp dpt:53
    0     0 DROP       udp  --  *      *       119.107.200.24       0.0.0.0/0            udp dpt:53
 132K   15M ACCEPT     all  --  *      *       10.0.0.0/24          0.0.0.0/0
22657 1358K ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:80
  147  5880 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:53
 1854  136K ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:53
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:953
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:953
   28  1408 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:25
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:25
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:143
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:143
   17  1088 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:993
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:993
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:587
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:587
    6   340 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:465
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:465
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:110
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:110
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:995
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:995
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:1279
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:1279
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:22
    8   432 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:443
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:443


Chain ufw-user-limit (0 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 5 LOG flags 0 level 4 prefix "[UFW LIMIT BLOCK] "
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable


Chain ufw-user-limit-accept (0 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0



```

---

### Post by ohiknow on 2014-07-01
Got it. Thank you for walking me through it.

---

### Post by untrustytahr on 2014-07-01
No worries.  Help others when you can.

---

