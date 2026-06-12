---
title: "Firewall rules and Minecraft"
date: 2012-03-09
forum: Security
---

### Post by Fenlig on 2012-03-09
Hey Guys,

So I am trying to close as many ports as possible, but its giving me issue with my minecraft server.

```
skay@Servertron:~$ sudo iptables -L
[sudo] password for skay:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:25565
DROP       all  --  anywhere             anywhere

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

Minecraft runs on port 25565.

Now I can see the server running but cannot connect.

I have another Minecraft server running on 25566 and it isn't showing as running at all which is to be expected as there is no rule to all that port.

Im still fairly new to linux.

Anyone got an Idea?

---

### Post by Doug S on 2012-03-10
I think you might need a return path via a related, established rule.
Another way might be to allow for source port 25565 (thus allowing both directions for packet travel to your minecract server (dpt=25565) and from your minecraft server (spt=25565)).
 
Perahps look at the packet counters also with:```
sudo iptables -v -x -n -L
``` to see which paths are being taken. Also add logging rules to help.

---

### Post by Fenlig on 2012-03-10
I tried opening the port both ways, but no luck.

I looked back over the Ubuntu guide from the link below:
[https://help.ubuntu.com/community/IptablesHowTo#Further_Information](https://help.ubuntu.com/community/IptablesHowTo#Further_Information)

I seen one part I had not entered.

```

sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

```

This Resolved the issue.

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:25566
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:25565
DROP       all  --  anywhere             anywhere

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

---

