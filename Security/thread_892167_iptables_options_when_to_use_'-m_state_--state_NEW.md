---
title: "iptables options: when to use '-m state --state NEW'"
date: 2008-08-16
forum: Security
---

### Post by velocity2 on 2008-08-16
Hi guys!
I'm setting up iptables on my machine and I've been looking at beginner tutorials on iptables and have seen these two types of rules come up all the time. I've been looking at man pages but haven't been able to figure out when to use each. I'm trying to secure a shhd port.

```
-A INPUT -p tcp --dport 2221 -j ACCEPT
```
and
```
-A INPUT -p tcp -m state --state NEW --dport 2221 -j ACCEPT
```

What exactly is the main difference between the two and when should I use one over the other? 

Thank you!

dave

---

### Post by dfreer on 2008-08-17
```
--state state
Where  state is a comma separated list of the connection states to match. Possible states are 

INVALID meaning that the packet could not be identified for some reason which includes running out of memory and ICMP errors which donât correspond to any known connection, 

ESTABLISHED meaning  that the packet is associated with a connection which has seen packets in both directions, 

NEW meaning that the packet has started a new connection, or otherwise associated with a connection which has not seen packets in both directions, and  

RELATED  meaning  that  the packet is starting a new connection, but is associated with an existing connection, such as an FTP data transfer, or an ICMP error.

```

So basically this rule:
-A INPUT -p tcp -m state --state NEW --dport 2221 -j ACCEPT
Means that any brand NEW packets on TCP port 2221 (generally the very first packet in a transmission) will be jumped to the ACCEPT chain.

Not sure why you would ever need to specify a rule for the state of NEW only, unless you were setting up some sort of port knocking scheme. Then again I only know enough about iptables to manage my own firewall.

---

### Post by velocity2 on 2008-08-17
Thanks :)

I'm still not sure what the deal with NEW is but I guess I can use either. I haven't seen any explanations of why it matters...

---

### Post by dfreer on 2008-08-18
> **velocity2 said:**
> Thanks :)

I'm still not sure what the deal with NEW is but I guess I can use either. I haven't seen any explanations of why it matters...

My advice? Don't use it unless you are for sure you need it. I use --state when setting up my firewall. Basically, I allow all incoming traffic of state ESTABLISHED and RELATED, then drop all other incoming traffic. This allows my programs like firefox to access the DNS server and have the DNS server talk back.

---

### Post by idontwannaregister on 2013-02-05
I belive he asks cuz he used the system config firewall tui script ... .

---

### Post by CharlesA on 2013-02-05
This thread is from 2008. I doubt the OP is coming back....

---

