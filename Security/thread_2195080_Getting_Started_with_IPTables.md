---
title: "Getting Started with IPTables"
date: 2013-12-22
forum: Security
---

### Post by sniper8752 on 2013-12-22
So I have decided to start learning about IPTables because it seems like it would be good to know, especially for running a server.  Please be patient with me as I try to pick it up.  
I tried to add my first rule, which was a simple block to ICMP requests.  The command I ran in the terminal was:
```
sudo iptables -A OUPTPUT -p icmp --icmp-type echo-request -j DROP
```
I view the IPTable, and it shows the following:
```
DROP     icmp     --     anywhere     anywhere     icmp echo-request
```

I ping the server, and I get replies.  Why did it not block the requests?

Also, how do you save the rules so they do not get cleared on re-boot?
Lastly, what are some good resources to look at on learning how to use IPTables?  And just curious, did a quick search on basic server IPTables.  could anybody recommend any good ones?  I understand that a template won't fit everyones' needs, and would need to be modified.

---

### Post by cariboo on 2013-12-22
Moved to Security Discussions.

---

### Post by Doug S on 2013-12-23
> **sniper8752 said:**
> I ping the server, and I get replies.  Why did it not block the requests?Your rule for dropping echo requests is on the OUTPUT chain and the incoming pings would come via the INPUT chain. The replies would go via the OUTPUT chain, but they would be of the type "echo-reply", so the rule does not stop them as it is looking for echo-request type packets to DROP.

> Also, how do you save the rules so they do not get cleared on re-boot?There are many ways. [See method 3 in this thread]("http://ubuntuforums.org/showthread.php?t=1876124").

> Lastly, what are some good resources to look at on learning how to use IPTables?Again, there are so many, and several are pretty obsolete. Many of us like [this one]("http://bodhizazen.net/Tutorials/iptables/") as a good starting point reference, with links to further good references.

---

