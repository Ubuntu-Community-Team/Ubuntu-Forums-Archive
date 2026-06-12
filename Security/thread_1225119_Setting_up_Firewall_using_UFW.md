---
title: "Setting up Firewall using UFW"
date: 2009-07-28
forum: Security
---

### Post by moritz on 2009-07-28
hi
im trying to set up my firewall/iptables using ufw. my server is webserver and router for my network. i got two NIC eth0 with 192.168.0.1 (intranet) and eth1 with 192.168.2.30 (internet). i only whant some specific ports to be open to the internet. but there are always all ports open.

Output of ufw status verbose:
```
Status: active
Logging: on (low)
Default: reject
New profiles: skip

To                         Action  From
--                         ------  ----
Anywhere                   REJECT  Anywhere
192.168.0.1                ALLOW   192.168.0.0/24
22                         ALLOW   Anywhere
80                         ALLOW   Anywhere
8245                       ALLOW   Anywhere
6667                       ALLOW   Anywhere

```

Output of nmap from the "outside":
```
Not shown: 986 closed ports
PORT     STATE    SERVICE
22/tcp   open     ssh
25/tcp   open     smtp
53/tcp   open     domain
80/tcp   open     http
111/tcp  open     rpcbind
135/tcp  filtered msrpc
139/tcp  filtered netbios-ssn
445/tcp  filtered microsoft-ds
901/tcp  open     samba-swat
2000/tcp open     callbook
2049/tcp open     nfs
5060/tcp open     sip
6667/tcp open     irc
8089/tcp open     unknown
```

I also tried to disable and re-enable ufw.

Any ideas?

---

