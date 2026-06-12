---
title: "Still getting entries in auth.log for IP that should be blocked in iptables"
date: 2014-06-03
forum: Security
---

### Post by vRanger on 2014-06-03
I must be missing something fundamental, could use your help.  Have this in my iptables:
> -A INPUT -s 116.10.191.0/24 -j DROP
Still getting this in my auth.log
> Jun  3 07:31:34 mailhost sshd[28308]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=116.10.191.228  user=rootJun  3 07:31:36 mailhost sshd[28308]: Failed password for root from 116.10.191.228 port 10437 ssh2
Jun  3 07:31:47 mailhost sshd[28308]: PAM 5 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=116.10.191.228  user=root
Jun  3 07:31:48 mailhost sshd[28312]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=116.10.191.228  user=root
Jun  3 07:31:50 mailhost sshd[28312]: Failed password for root from 116.10.191.228 port 18593 ssh2
Jun  3 07:32:01 mailhost sshd[28312]: PAM 5 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=116.10.191.228  user=root
Jun  3 07:32:01 mailhost sshd[28318]: refused connect from 116.10.191.228 (116.10.191.228)
Jun  3 08:23:04 mailhost sshd[28814]: refused connect from 116.10.191.171 (116.10.191.171)
Jun  3 08:48:13 mailhost sshd[28911]: refused connect from 116.10.191.196 (116.10.191.196)

What am I missing?

---

### Post by tgalati4 on 2014-06-03
Without knowing your network topology, it is hard to say.  Perhaps something inside your network or your router is compromised.  I would install some rate-limiting such as *fail2ban*.  Use some network snooping to find the MAC address and compare it to your machines.

In the meantime, it would be good to remove ssh from the web-facing ports in your forwarding table, because someone or something is trying random ports to log into your ssh.  That would be bad.

---

### Post by vRanger on 2014-06-03
Thanks for trying, however, I don't understand your answer.  Should not all packets with 116.10.191.0 be dropped, thereby not even causing the entry in the auth.log?  The network topology is simple:
> Internet-->DSL Modem/Firewall-->Ubuntu server with iptables firewall
The DSL modem firewall has the SSH port open so I can remotely access it. There are many other failed attempts to log in as reported in auth.log, and I believe this is not unusual for any server exposed to the internet.  Fail2Ban is implemented.  It's primary purpose, so far as I understand, is to prevent (no rather, reduce the change of success of) outsiders being able to brute force an entry via guessing passwords by limiting the number of tries they are allowed to something reasonable, say one per minute rather than ten per second (I don't know what the max is without fail2ban, just an example).  116.10.191.0 is a well known offender for attempting brute force entry into servers around the world.  I want to specifically block that IP range and for there to be no entries with that subnet showing up in my auth.log.  Why is the entry I have in the iptables not doing that?  Thanks again!

---

### Post by tgalati4 on 2014-06-03
I am not an iptables expert.  But I would go through this documentation and then post your current ruleset.  Perhaps there is a conflict within the rules that is causing a problem.  Perhaps iptables is not running at all.  [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
At first glance, your rule should block all packets coming from that Class D subnet.  But it does not appear to be working.  So check to see if it is running and then go through some of the logging to see what is happening.

Then I would look into blocking at your modem.  Many modems support blocking IP ranges.  If not, then put ddwrt or tomato or some other firmware on your router and perform the blocking there.  As you know, you want a few layers of security.

---

### Post by vRanger on 2014-06-04
iptable config
```
:~$ sudo iptables -L -v
Chain INPUT (policy DROP 176K packets, 15M bytes)
 pkts bytes target     prot opt in     out     source               destination
 235K   28M fail2ban-postfix  tcp  --  any    any     anywhere             anywhere             multiport dports http,https,smtp,submission,pop3,pop3s,imap2,imaps,sieve
 234K   28M fail2ban-dovecot  tcp  --  any    any     anywhere             anywhere             multiport dports http,https,smtp,submission,pop3,pop3s,imap2,imaps,sieve
 234K   28M fail2ban-roundcube  tcp  --  any    any     anywhere             anywhere             multiport dports http,https,smtp,submission,pop3,pop3s,imap2,imaps,sieve
 4334  389K fail2ban-ssh  tcp  --  any    any     anywhere             anywhere             tcp dpt:ssh
 556K  101M ACCEPT     all  --  any    any     anywhere             anywhere             state RELATED,ESTABLISHED
14281  857K ACCEPT     all  --  lo     any     anywhere             anywhere
   57  2988 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:http
13907  723K ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:https
  742 36024 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:smtp
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:submission
    6   288 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:pop3
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:pop3s
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:imap2
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:imaps
  422 19448 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:ssh
 7003  347K ACCEPT     icmp --  any    any     anywhere             anywhere             icmp echo-request
    0     0 DROP       all  --  any    any     116.10.191.0/24      anywhere


Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 41726 packets, 6829K bytes)
 pkts bytes target     prot opt in     out     source               destination



```

---

### Post by untrustytahr on 2014-06-04
```
:~$ sudo iptables -L -v
Chain INPUT (policy DROP 176K packets, 15M bytes)
 pkts bytes target     prot opt in     out     source               destination
 235K   28M fail2ban-postfix  tcp  --  any    any     anywhere              anywhere             multiport dports  http,https,smtp,submission,pop3,pop3s,imap2,imaps,  sieve
 234K   28M fail2ban-dovecot  tcp  --  any    any     anywhere              anywhere             multiport dports  http,https,smtp,submission,pop3,pop3s,imap2,imaps,  sieve
 234K   28M fail2ban-roundcube  tcp  --  any    any     anywhere              anywhere             multiport dports  http,https,smtp,submission,pop3,pop3s,imap2,imaps,  sieve
 4334  389K fail2ban-ssh  tcp  --  any    any     anywhere             anywhere             tcp dpt:ssh
 556K  101M ACCEPT     all  --  any    any     anywhere             anywhere             state RELATED,ESTABLISHED
14281  857K ACCEPT     all  --  lo     any     anywhere             anywhere
   57  2988 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:http
13907  723K ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:https
  742 36024 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:smtp
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:submission
    6   288 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:pop3
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:pop3s
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:imap2
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:imaps
  [COLOR=#ff0000]**422 19448 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:ssh**[/COLOR]
 7003  347K ACCEPT     icmp --  any    any     anywhere             anywhere             icmp echo-request
    [COLOR=#ff0000][I][B]0     0 DROP       all  --  any    any     116.10.191.0/24      anywhere
[/B][/I][/COLOR]

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 41726 packets, 6829K bytes)
 pkts bytes target     prot opt in     out     source               destination
```

The drop needs to appear before the accept.  You can't drop it after it's already been accepted.

As mentioned earlier, the logical place to filter would be at the router.  As you can see from your logs, other ports have reached your Ubuntu box which means you have either forwarded more ports than what you've told us, or you have put the Ubuntu box in a DMZ or the modem/router is bridging instead of routing/nating.

---

### Post by vRanger on 2014-06-04
Thanks for the explanation.  I got the DROP to happen before the accept you highlighted.  Used
> sudo vi /etc/iptables/rules.v4
to edit, then
> sudo iptables-restore /etc/iptables/rules.v4
to load the change into memory.
Now sudo iptables -L looks like this
```
:~$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination
fail2ban-postfix  tcp  --  anywhere             anywhere             multiport dports http,https,smtp,submission,pop3,pop3s,imap2,imaps,sieve
fail2ban-dovecot  tcp  --  anywhere             anywhere             multiport dports http,https,smtp,submission,pop3,pop3s,imap2,imaps,sieve
fail2ban-roundcube  tcp  --  anywhere             anywhere             multiport dports http,https,smtp,submission,pop3,pop3s,imap2,imaps,sieve
fail2ban-ssh  tcp  --  anywhere             anywhere             tcp dpt:ssh
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  116.10.191.0/24      anywhere
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:smtp
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:submission
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:pop3
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:pop3s
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:imap2
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:imaps
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request

```

---

### Post by tgalati4 on 2014-06-05
Beat me to it.  And yes, it does appear to be an extensive port-forwarding table in the router which would compromise security as well.  Is this server connected to a DMZ port of the router?

---

### Post by vRanger on 2014-06-05
Really appreciate you taking the time, however, could you dumb it down a bit for me?  Not quite getting what your talking about here:
> 

[COLOR=#000000]**untrustytahr**[/COLOR][COLOR=#000000]As you can see from your logs, other ports have reached your Ubuntu box which means you have either forwarded more ports than what you've told us, or you have put the Ubuntu box in a DMZ or the modem/router is bridging instead of routing/nating.[/COLOR]
Yes, more ports are forwarded, but I wanted to stay focused on SSH.
> 

[COLOR=#000000]**_tgalati4_**[/COLOR][COLOR=#000000]And yes, it does appear to be an extensive port-forwarding table in the router which would compromise security as well. Is this server connected to a DMZ port of the router?[/COLOR]
It's a standard ISP DSL modem with limited capabilities for FW and Port Forwarding.  It is a NAT router.  I'll have to look up DMZ.

---

### Post by untrustytahr on 2014-06-05
> **vRanger said:**
> Really appreciate you taking the time, however, could you dumb it down a bit for me?  Not quite getting what your talking about here:

Yes, more ports are forwarded, but I wanted to stay focused on SSH.


I got the impression that you thought only ssh port was open.  I was just pointing out that the ubuntu box was more exposed than just ssh.

---

