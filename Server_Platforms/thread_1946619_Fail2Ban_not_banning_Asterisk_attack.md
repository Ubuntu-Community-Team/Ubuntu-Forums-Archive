---
title: "Fail2Ban not banning Asterisk attack"
date: 2012-03-25
forum: Server Platforms
---

### Post by beowulf222 on 2012-03-25
Hey,

I am using Ubuntu 9.04 LTS and installed Fail2Ban from the repository, which means I have Fail2Ban v0.8.2 on my system.

Fail2Ban generally works since it attacks and blocks SSH attacks, but attacks on the Asterisk don't cause Fail2Ban to react.

In setting up the config for Asterisk, I followed [http://www.fail2ban.org/wiki/index.php/Asterisk]("http://www.fail2ban.org/wiki/index.php/Asterisk") and [http://www.voip-info.org/wiki/view/Fail2Ban+%28with+iptables%29+And+Asterisk]("http://www.voip-info.org/wiki/view/Fail2Ban+%28with+iptables%29+And+Asterisk").

When I test the regex, it shows that it works properly (I tested it with an internal IP).

```
fail2ban-regex /var/log/asterisk/fail2ban /etc/fail2ban/filter.d/asterisk.conf

Running tests
=============

Use regex file : /etc/fail2ban/filter.d/asterisk.conf
Use log file   : /var/log/asterisk/fail2ban


Results
=======

Failregex
|- Regular expressions:
|  [1] NOTICE(?:\[\d+\]) .*: Registration from '.*' failed for '<HOST>' - Wrong password$
|  [2] NOTICE(?:\[\d+\]) .*: Registration from '.*' failed for '<HOST>' - No matching peer found$
|  [3] NOTICE.* .*: Registration from '.*' failed for '<HOST>' - No matching peer found
|  [4] NOTICE(?:\[\d+\]) .*: Registration from '.*' failed for '<HOST>' - Username/auth name mismatch$
|  [5] NOTICE(?:\[\d+\]) .*: Registration from '.*' failed for '<HOST>' - Device does not match ACL$
|  [6] NOTICE(?:\[\d+\]) .*: Registration from '.*' failed for '<HOST>' - Peer is not supposed to register$
|  [7] NOTICE(?:\[\d+\]) .*: Registration from '.*' failed for '<HOST>' - ACL error (permit/deny)$
|  [8] NOTICE(?:\[\d+\]) <HOST> failed to authenticate as '.*'$
|  [9] NOTICE(?:\[\d+\]) .*: No registration for peer '.*' \(from <HOST>\)$
|  [10] NOTICE(?:\[\d+\]) .*: Host <HOST> failed MD5 authentication for '.*' (.*)$
|  [11] NOTICE(?:\[\d+\]) .*: Failed to authenticate user .*@<HOST>.*$
|
`- Number of matches:
   [1] 0 match(es)
   [2] 25 match(es)
   [3] 25 match(es)
   [4] 0 match(es)
   [5] 0 match(es)
   [6] 0 match(es)
   [7] 0 match(es)
   [8] 0 match(es)
   [9] 0 match(es)
   [10] 0 match(es)
   [11] 0 match(es)

Ignoreregex
|- Regular expressions:
|
`- Number of matches:

Summary
=======

Addresses found:
[1]
[2]
    10.10.101.241 (Sun Mar 25 11:13:22 2012)
    10.10.101.241 (Sun Mar 25 11:13:22 2012)
    10.10.101.241 (Sun Mar 25 11:13:22 2012)
    10.10.101.241 (Sun Mar 25 11:13:23 2012)
    10.10.101.241 (Sun Mar 25 11:13:26 2012)
    10.10.101.241 (Sun Mar 25 11:13:27 2012)
    10.10.101.241 (Sun Mar 25 11:13:27 2012)
    10.10.101.241 (Sun Mar 25 11:13:30 2012)
    10.10.101.241 (Sun Mar 25 11:13:31 2012)
    10.10.101.241 (Sun Mar 25 11:13:32 2012)
    10.10.101.241 (Sun Mar 25 11:13:34 2012)
    10.10.101.241 (Sun Mar 25 11:13:34 2012)
    10.10.101.241 (Sun Mar 25 11:13:35 2012)
    10.10.101.241 (Sun Mar 25 11:13:35 2012)
    10.10.101.241 (Sun Mar 25 11:13:39 2012)
    10.10.101.241 (Sun Mar 25 11:13:39 2012)
    10.10.101.241 (Sun Mar 25 11:13:40 2012)
    10.10.101.241 (Sun Mar 25 11:13:40 2012)
    10.10.101.241 (Sun Mar 25 11:13:43 2012)
    10.10.101.241 (Sun Mar 25 11:13:43 2012)
    10.10.101.241 (Sun Mar 25 11:13:43 2012)
    10.10.101.241 (Sun Mar 25 11:13:44 2012)
    10.10.101.241 (Sun Mar 25 11:13:49 2012)
    10.10.101.241 (Sun Mar 25 11:13:49 2012)
    10.10.101.241 (Sun Mar 25 11:13:50 2012)
[3]
    10.10.101.241 (Sun Mar 25 11:13:22 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:22 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:22 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:23 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:26 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:27 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:27 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:30 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:31 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:32 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:34 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:34 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:35 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:35 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:39 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:39 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:40 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:40 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:43 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:43 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:43 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:44 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:49 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:49 2012) (already matched)
    10.10.101.241 (Sun Mar 25 11:13:50 2012) (already matched)
[4]
[5]
[6]
[7]
[8]
[9]
[10]
[11]

Date template hits:
0 hit(s): Month Day Hour:Minute:Second
0 hit(s): Weekday Month Day Hour:Minute:Second Year
0 hit(s): Weekday Month Day Hour:Minute:Second
0 hit(s): Year/Month/Day Hour:Minute:Second
0 hit(s): Day/Month/Year:Hour:Minute:Second
556 hit(s): Year-Month-Day Hour:Minute:Second
0 hit(s): Day-Month-Year Hour:Minute:Second[.Millisecond]
0 hit(s): TAI64N
0 hit(s): Epoch

Success, the total number of match is 50

```

The Fail2Ban log, however, shows no banning action at all.

Here is my config in the jail.conf

```

[asterisk-tcp]
enabled  = true
filter   = asterisk
action   = iptables-multiport[name=asterisk-tcp, port="5060,5061", protocol=tcp]
logpath  = /var/log/asterisk/fail2ban
findtime  = 60
maxretry = 3
bantime  = 600000

[asterisk-udp]

enabled  = true
filter   = asterisk
action   = iptables-multiport[name=asterisk-udp, port="5060,5061", protocol=udp]
logpath  = /var/log/asterisk/fail2ban
findtime  = 60
maxretry = 3
bantime  = 600000

```

If I manually block an attacker, it works.
```
 iptables -A INPUT -p UDP -s 85.25.95.225 --dport 5060 -j DROP
```
In this example, the IP 85.25.95.225 would no longer be able to attack the Asterisk.

Looking at Fail2Ban Logfile I don't see any obvious error

```

2012-03-25 17:32:35,004 fail2ban.jail   : INFO   Using Gamin
2012-03-25 17:32:35,004 fail2ban.filter : INFO   Created Filter
2012-03-25 17:32:35,005 fail2ban.filter : INFO   Created FilterGamin
2012-03-25 17:32:35,005 fail2ban.filter : INFO   Added logfile = /var/log/asterisk/fail2ban
2012-03-25 17:32:35,006 fail2ban.filter : INFO   Set maxRetry = 3
2012-03-25 17:32:35,006 fail2ban.filter : INFO   Set findtime = 60
2012-03-25 17:32:35,007 fail2ban.actions: INFO   Set banTime = 600000
2012-03-25 17:32:35,026 fail2ban.actions.action: INFO   Set actionBan = iptables -I fail2ban-<name> 1 -s <ip> -j DROP
2012-03-25 17:32:35,026 fail2ban.actions.action: INFO   Set actionStop = iptables -D <chain> -p <protocol> -m multiport --dports <port> -j fail2ban-<name>
iptables -F fail2ban-<name>
iptables -X fail2ban-<name>
2012-03-25 17:32:35,027 fail2ban.actions.action: INFO   Set actionStart = iptables -N fail2ban-<name>
iptables -A fail2ban-<name> -j RETURN
iptables -I <chain> -p <protocol> -m multiport --dports <port> -j fail2ban-<name>
2012-03-25 17:32:35,027 fail2ban.actions.action: INFO   Set actionUnban = iptables -D fail2ban-<name> -s <ip> -j DROP
2012-03-25 17:32:35,028 fail2ban.actions.action: INFO   Set actionCheck = iptables -n -L <chain> | grep -q fail2ban-<name>
2012-03-25 17:32:35,030 fail2ban.actions.action: INFO   Set actionBan = printf %b "Subject: [Fail2Ban] <name>: banned <ip>
2012-03-25 17:32:35,031 fail2ban.actions.action: INFO   Set actionUnban =
2012-03-25 17:32:35,032 fail2ban.actions.action: INFO   Set actionCheck =

```

I get an e-mail that all jails were started.

Does anybody have an idea what I am missing here? Why does Fail2Ban fail to recognize Asterisk intrusion attempts.

-- nick

---

### Post by collisionystm on 2012-03-25
Is it that Fail2Ban only blocks login attempts and not port scans?

Install UFW or setup better IPTABLES.

---

