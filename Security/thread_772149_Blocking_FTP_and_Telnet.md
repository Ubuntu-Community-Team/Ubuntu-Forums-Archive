---
title: "Blocking FTP and Telnet"
date: 2008-04-28
forum: Security
---

### Post by amai on 2008-04-28
I would like to block FTP and Telnet on my server.

What will be the commandto use in IPTABLES.

have raed the IPtables how-to's so far
Tried the following but still not working.

FOR Telnet,
1)iptables -A INPUT --dport 23 -j DROP
2)iptables -A INPUT -p tcp --destination-port telnet -j DROP 



FOR FTP,
iptables -A INPUT -p FTP -i eth0 -j REJECT 
iptables -I FORWARD 2 -p tcp --dport 21 -j DROP.

What will be the command to block and enable FTP and Telnet

---

### Post by hyper_ch on 2008-04-28
if you are behind a router to which you connect to the net, it would probably be simplest to block it there... so within your lan you still have those services then available.

---

### Post by Monicker on 2008-04-28
Are you sure the rules are even actives?  Are you using any other iptables rules  Did you receive any error messages?

Run this to see if your rules are even being matched:

```
iptables -v -n -L
```


Are there number is the pkts and bytes columns, or are they 0 ?



These should be sufficient to block those services:

```
iptables -A INPUT -p tcp -m tcp --dport 23 -j DROP
iptables -A INPUT -p tcp -m tcp --dport 21 -j DROP
```


To be more secure, you should drop/reject by default, and then only allow the services you need.  More details about the network and what/why you need to block those particular services would be helpful.

---

### Post by HermanAB on 2008-04-28
Hmm, in any self respecting firewall, the default should be DROP.  So if you are running Firestarter or Shorewall and you have not enabled Telnet and FTP, then it should be blocked already.

Cheers,

Herman

---

### Post by The Cog on 2008-04-28
> **amai said:**
> I would like to block FTP and Telnet on my server.

What will be the commandto use in IPTABLES.

have raed the IPtables how-to's so far
Tried the following but still not working.

FOR Telnet,
1)iptables -A INPUT --dport 23 -j DROP
2)iptables -A INPUT -p tcp --destination-port telnet -j DROP 

for 1), you cannot use the destination port clause without specifyng tcp or udp protocol. Since --dport and --destination-port are aliases and telnet uses port 23, adding the tcp protocol definition to 1) makes it the same as 2). This should work.
> 
FOR FTP,
iptables -A INPUT -p FTP -i eth0 -j REJECT 
iptables -I FORWARD 2 -p tcp --dport 21 -j DROP.

What will be the command to block and enable FTP and Telnet
-p can only be tcp, udp, icmp or all (see man iptables). You probably wanted:
**iptables -A INPUT -p tcp --dport ftp -i eth0 -j DROP** 
It looks like you are inserting to existing rules. Since we don't know what all the other rules in the FORWARD chain are, all bets are off, but it looks like a valid attempt to drop FTP providing rule 1 doesn't accept it.

As others have said, it is normal in a firewall to set the default policy to drop and then specifically accept stuff you know you want to allow.

---

### Post by The Cog on 2008-04-28
Oops - duplicate post. Sorry.

---

