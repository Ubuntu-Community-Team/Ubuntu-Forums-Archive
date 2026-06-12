---
title: "iptables configuration"
date: 2008-02-24
forum: Security Discussions
---

### Post by mmistroni on 2008-02-24
Hi all,
  i own a VPS, and as by checking logs i have found out many unsuccessfull attempts to connect  to it, i decided anyway to setup a firewall to discourage intruders.
the problem i have is that only access i have to my VPS is via remote ssh, so this limit what i can do (as i cannot say 'block everything except ip coming from xxx address' as my address is assigned dynamically)

to 'prevent' some ip address for connecting to my VPS i setup rules as this

ACCEPT   tcp  -- anywhere     anywhere    tcp dpt:ssh
DROP       tcp  -- 61.143.0.0    anywhere

i was wondering if the rule above block traffic coming from 61.143 addresses

Additionally, my VPS is an UBuntu Feisty Fawn server.... i want to figure out if iptables is running but everytime i type

ps aux |grep iptables    what i receive is

root  1928 0.0  0.5  2804   720   pts/0  R+    grep  iptables

anyone could tell me:
- if my configuration is fine for dropping connection from certain address
- how can i findout if iptables is running
- how do i deal with blocking everything except traffic coming from my ip address @home when my address is assigned dynamically?

thanks in advance and regarsd
 marco

---

### Post by k_grdn on 2008-02-24
Hi,

To view loaded iptables rules use: 

iptables -L -v 

For other tables use the -t switch, for full info on commands read man, if there are rules then iptables is running.

This rule will allow ssh on all filter chains from any host.
ACCEPT tcp -- anywhere anywhere tcp dpt:ssh

The second rule will drop all traffic from 61.143.0.0/16 network.
DROP tcp -- 61.143.0.0 anywhere.

If you have a small rule set it's better practice to set you default policies for all filter table chains to DROP, use -P, then explicitly allow hosts.

Also I sugest installing denyhosts or failtoban to block hosts who repeated failed ssh auth's to hosts.deny.

Going further you could use iptables to limit the number off ssh connections accross time, also running ssh via xinetd offers other means of security time restrictions etc...  PAM also offers protection to ssh pam_cracklib, pam_listfile etc.., force no root login, protocol 2, strict mode etc.. 

Regards,

k_grdn

---

### Post by mmistroni on 2008-02-24
k_grdn,
  thanks for your useful reply.
i have tried to modify the iptables as follows
```

Chain INPUT (policy ACCEPT 35542 packets, 21M bytes)
 pkts bytes target     prot opt in     out     source               destination

19626 3602K ACCEPT     tcp  --  any    any     anywhere             anywhere
        tcp dpt:www
25779 2478K ACCEPT     tcp  --  any    any     anywhere             anywhere
        tcp dpt:ssh
    0     0 DROP       tcp  --  any    any     61.143.0.0           anywhere

    0     0 DROP       tcp  --  any    any     217.19.0.0           anywhere

    0     0 SSH_CHECK  tcp  --  any    any     anywhere             anywhere
        tcp dpt:ssh state NEW

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 72558 packets, 51M bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain SSH_CHECK (1 references)
 pkts bytes target     prot opt in     out     source               destination

    0     0            0    --  any    any     anywhere             anywhere
        recent: SET name: SSH side: source
    0     0 DROP       0    --  any    any     anywhere             anywhere
        recent: UPDATE seconds: 60 hit_count: 4 name: SSH side: source

```

however, it looks like when i ssh from my home, i am actually connecting to ssh2... therefore i feel that rule above is not enough to prevent ssh access

and also, from logs i can see that many of intruders are trying to get  in using ssh2...

thanks and regards
 marco

---

### Post by k_grdn on 2008-02-24
Hi,

Your problem is your default policies are set to ACCEPT, you need to change these to DROP for all filter table chains.

iptables -A INPUT -P DROP do this for all filter chains (output,forward)

Post your scripted rule set.

Regarding your dynamic address problem I suggest getting a dynDNS name then create a script running via cron to check if your address has changed if so then replace the iptables ssh rule with the -R option or set your address as a variable in your firewall script:

MY_IP=`dig a +short`

When your address changes restart the firewall.

Regarding the address change script briefly: 

IP_FILE="/usr/local/bin/ip"
CURRENT_IP=`cat $IP_FILE`
IP=`dig a +short mydomain`

# Perform IP check

if [ $CURRENT_IP == $IP ]; then
        exit 0
else
    IPTABLES -R INPUT -i $EXT_INT -p tcp \
         -s $IP \
         --dport 22 -d $INT_IP \
         -m state --state NEW -j ACCEPT
fi


For trouble shooting remotely to stop yourself getting locked out of your machine use cron to flush your iptables ruleset.

SSH2? is ssh just using protocol version2 force this in your sshd_config.

Regards,

k_grdn

---

### Post by The Cog on 2008-02-24
Apart from the problem that your default action is to accept taht k_grdn points out, you have a logic problem with your rules. iptables works down the rules until it finds a match. Any SSH request coming from a bad guy is going to reach the ACCEPT SSH rule and therefore never reach the DROP from 61.143.0.0 rule. You probably want to put a rule dropping ssh from 61.143.0.0 before your rule accepting SSH frm anywhere.

---

