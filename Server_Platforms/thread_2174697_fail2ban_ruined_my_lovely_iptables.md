---
title: "fail2ban ruined my lovely iptables"
date: 2013-09-15
forum: Server Platforms
---

### Post by sefs on 2013-09-15
Hi there,
I decided to install fail2ban to protect a dovecot and postfix server.

It trashed my iptables.  It set the forward and input chains to accept deleted all my rules and inserted two rules of its own.

Here is what it changed iptables too...
```

Chain INPUT (policy ACCEPT 418 packets, 34084 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 fail2ban-dovecot  tcp  --  any    any     anywhere             anywhere             multiport dports smtp,ssmtp,imap2,imap3,imaps,pop3,pop3s
    0     0 fail2ban-postfix  tcp  --  any    any     anywhere             anywhere             multiport dports smtp,ssmtp

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 418 packets, 68635 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain fail2ban-dovecot (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     all  --  any    any     anywhere             anywhere            

Chain fail2ban-postfix (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     all  --  any    any     anywhere             anywhere   

```

Is that normal?

---

