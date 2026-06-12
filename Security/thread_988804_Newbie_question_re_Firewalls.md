---
title: "Newbie question re Firewalls"
date: 2008-11-20
forum: Security
---

### Post by HDave on 2008-11-20
Does anybody know how to translate the following configuration into something that would work for Firestarter or UFW?

```
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP
transparent_squid 8080 "root root"
interface any world
policy drop
protection strong
client all accept
server cups accept
```

Recently I upgraded to Intrepid and due to [this]("https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/262794") bug, firehol is now broken.

I was using firehol to redirect all the internet traffic on my machine to Danguardian which is a content filter.  I don't understand firehol very much, but given that firehol is going to be broken for some time, I was hoping to use another solution.

---

### Post by cariboo on 2008-11-21
I would suggest using GUFW which is the prefered gui for Iptables, from what I've seen of it, it is fairly simple to use.

Jim

---

### Post by cdenley on 2008-11-21
> **cariboo907 said:**
> I would suggest using GUFW which is the prefered gui for Iptables, from what I've seen of it, it is fairly simple to use.

Jim

I don't think UFW can use the owner module in iptables. You can always use iptables directly.

---

### Post by bodhi.zazen on 2008-11-21
> **cdenley said:**
> I don't think UFW can use the owner module in iptables. You can always use iptables directly.

It can, sort of ....

You need to add any rules to the config files :

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw#Advanced%20Syntax](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw#Advanced%20Syntax)

You need to add you iptables rule to /etc/ufw/before.rules

Of course, if you are going to write complex rule sets it is probably easier to learn iptables directly.

---

### Post by HDave on 2008-11-23
> **bodhi.zazen said:**
> You need to add you iptables rule to /etc/ufw/before.rules

I think I understand, but I wonder why I should not put it in user.rules?  

However, my big problem is that ufw does not (I think) use the same syntax for rules as firehol.  I am afraid I don't understand these firehol rules so I don't know how to express them in ufw.

Sorry to sound so helpless, but I got the firehol rules from a website that just handed them out as a way to get Dansguardian working.  Any help on translation is much appreciated.  

My backup plan is to learn firehol and then learn iptables (yikes! :confused:).

---

### Post by bodhi.zazen on 2008-11-23
Well, this is why there are a number of GUI front ends for iptables.

IMO you are best off in the long run either learning the syntax of iptables or staying with a single gui config tool.

You need to add your rules in before.rules as in iptabes, order matters. First rule matching a packet == action taken. So if you have an accept all connections on port 22 (for example) you can not follow it with a black list as the accept all already matched the packet (if that makes sense).

So ...

Order is 

black list
accept port 22
deny all others

---

