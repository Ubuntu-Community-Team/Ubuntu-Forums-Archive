---
title: "Iptables"
date: 2008-11-27
forum: Security
---

### Post by Drezard on 2008-11-27
im trying to get NAT going on a Linux server using iptables.

I have two interfaces eth0 (which is my internal) and eth1 (which is my external). Both are set up correctly and such.

Now heres the situation, when I use the rules:

- FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
- FORWARD -o eth0 -i eth1 -j ACCEPT
- -t nat -A POSTROUTING -o eth1 -j MASQUERADE

It all works perfectly. The packets are forwarded from eth0 to eth1 and out to the net perfectly. But when I a

- A FORWARD -j DROP

To my chain, the whole thing dies and nothing gets forwarded anymore from what I can see. What I want to be able to happen is connections to be made from inside my network eth0 to eth1 and then out to the internet to be allowed through the firewall but, I want all connections coming in from the internet and to eth1 to be blocked.

Its not exactly working though.

Whats wrong?

Daniel

---

### Post by kevdog on 2008-11-27
Can you list the following:

sudo iptables -L

This will tell me your default chain policy.

---

### Post by gombadi on 2008-11-27
> **Drezard said:**
> 
I have two interfaces eth0 (which is my internal) and eth1 (which is my external). Both are set up correctly and such.

Now heres the situation, when I use the rules:

- FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
- FORWARD -o eth0 -i eth1 -j ACCEPT
- -t nat -A POSTROUTING -o eth1 -j MASQUERADE



Are you sure the above rules are round the correct way.
According to your post -
eth0 = internal
eth1 = external

> 
- FORWARD -o eth0 -i eth1 -j ACCEPT

This says allow all packets from external (eth1) to get to internal (eth0)
> 
- FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
This says to only allow packets from internal (eth0) to get to external (eth1) if established or related.

When you add - A FORWARD -j DROP then try and connect to a web page for example it will be a new packet from internal (eth0) to external (eth1), therefore will not be accepted by the ESTABLISHED,RELATED rule and will be dropped by the DROP rule.

---

### Post by Drezard on 2008-11-27
This is one of the things I dont understand:

> 
servermin@internal:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTAB                                                                             LISHED
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination



It has no source and destinations???

When my rc.local reads [updated the ports though]:

> 
# Set up the firewall

        # Any established connections are allowed through
        # NAT rules to hide the Internal network topology using Overloaded
        # NAT (PAT)

        /sbin/iptables -A FORWARD -i eth1 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
        /sbin/iptables -A FORWARD -o eth1 -i eth0 -j ACCEPT
        /sbin/iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

        # Allow lo (loopback) connections
        /sbin/iptables -A INPUT -i lo -j ACCEPT
        /sbin/iptables -A OUTPUT -i lo -j ACCEPT

        # Drop anything that doesnt fall in the category of NAT traffic

        /sbin/iptables -A FORWARD -j DROP



So, should I technically be able to SSH access when plugged into eth0, but not when plugged into eth1? Because currently I have SSH access on both sides BUT, it does forward correctly???

Daniel

---

### Post by gombadi on 2008-11-28
> 
It has no source and destinations???


A better command to see your firewall is
```

sudo iptables -vnL

```

This will be verbose and show you more information.

> 
So, should I technically be able to SSH access when plugged into eth0, but not when plugged into eth1? Because currently I have SSH access on both sides BUT, it does forward correctly???


Not sure what you mean by this. Can you give us more information about the layout of your network.

Do you have machines that you can SSH from on each side of the firewall and from there are able to ssh to a machine on the other side of the firewall?

---

