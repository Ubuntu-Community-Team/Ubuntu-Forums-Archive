---
title: "ssh server trouble"
date: 2006-07-13
forum: Server Platforms
---

### Post by ballin' on 2006-07-13
Hi, I am trying to setup openssh server at home so I can access my home comp from university.

I have installed server through synaptic.
used command: sudo /etc/init.d/ssh restart
and checked if its running using:  ps -ef | grep sshd
root     10252     1  0 17:36 ?        00:00:00 /usr/sbin/sshd
looks fine untill now?
i have also done ssh localhost and that works fine.

but I think that problem is that port 22 is not open. it says connection refused when I try to connect to my host name.
I have installed firestarter and put in the allow access rule for port 22, but still doesn't work. 

I have gone to [http://www.canyouseeme.org/](http://www.canyouseeme.org/) to check if the port 22 is open but it still isn't open.

I have a d-link dsl modem and alos put in a nat rule for port 22, don't now if that will help and still doesn't work. Can someone help me out with this problem?

cheers.

---

### Post by fabiand on 2006-07-13
To answers this question, it might be helpfull if you post your firewall rules ...

---

### Post by ballin' on 2006-07-13
Chain FIREWALL (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTAB LISHED
TRUSTED    all  --  anywhere             anywhere
DROP       all  --  anywhere             anywhere

Chain INPUT (policy ACCEPT)
target     prot opt source               destination
FIREWALL   all  --  anywhere             anywhere

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain TRUSTED (1 references)
target     prot opt source               destination
ACCEPT     udp  --  anywhere             anywhere            udp spt:https
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:https
ACCEPT     udp  --  anywhere             anywhere            udp spt:ssh
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ssh
ACCEPT     udp  --  anywhere             anywhere            udp dpt:5349
ACCEPT     udp  --  anywhere             anywhere            udp dpt:5351
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:5348
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ircd
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:auth
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6889

---

