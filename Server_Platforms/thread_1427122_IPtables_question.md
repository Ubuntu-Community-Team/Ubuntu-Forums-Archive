---
title: "IPtables question"
date: 2010-03-11
forum: Server Platforms
---

### Post by Pioden on 2010-03-11
Hi folks,

I'm trying to add a rule to an existing iptables firewall from the command line. The rule is to allow forwarding of traffic from a backup server to a virtualised fileserver. I ran the following command on the host server to allow forarding through the firewall

```
iptables -A FORWARD --source newbackup.mydomain.com  -j ACCEPT
```The command is fine BUT iptables has added it to the end of the FORWARD chain AFTER the drop command! :( 

```
ACCEPT     0    --  another.mydomain.com  anywhere
ACCEPT     0    --  anywhere             10.5.255.255
ACCEPT     0    --  anywhere             255.255.255.255
DROP       0    --  anywhere             anywhere
ACCEPT     0    --  newbackup.mydomain.com  anywhere
```
That of course means that the traffic from my backup server to the file server is dropped before it sees my new rule.

What did I do wrong? Can someone tell me how I should have done this? iptables isn't my strongest subject !!

---

### Post by Ryan Dwyer on 2010-03-11
Have a read of this - it talks about your problem in the first paragraph: [https://help.ubuntu.com/community/IptablesHowTo#Editing%20iptables](https://help.ubuntu.com/community/IptablesHowTo#Editing%20iptables)

---

### Post by Pioden on 2010-03-11
Thanks Ryan that's a good link. Reading around that page and Googling some more I *think* I have the answer. The -A in my command appended the rule to the end of the chain - creating the problem. Am I right in thinking that -I inserts the rule at the beginning of the rules without overwriting the first rule?

 i.e. what I should have written is: 

iptables -I FORWARD --source newbackup.mydomain.com  -j ACCEPT

---

### Post by Ryan Dwyer on 2010-03-11
Yes, I think that will work. You should also read the section about saving and configuring them to start automatically. That's probably easier because you can cut and paste them into the order you want.

---

