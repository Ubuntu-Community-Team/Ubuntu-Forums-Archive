---
title: "[SOLVED] Disabling the Iptables firewall"
date: 2008-03-05
forum: Server Platforms
---

### Post by Stephen_at on 2008-03-05
This is driving me sodding mad.

How do I shut down the iptables firewall fully. I cleared the settings and flushed it and thought I'd done everything right. Reboot the box and the paranoid settings come back.


If I do :

[FONT="Courier New"]iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
[/FONT]
then I can actually access my server through things like SSH and things actually work rather than it sitting there like a rock and and iptables -L produces:
[FONT="Courier New"]Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy DROP)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination[/FONT]


but when I reboot it comes back to:
[FONT="Courier New"]
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  tty.org.uk           192.168.255.255
logaborted  tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED tcp flags:RST/RST
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem
nicfilt    all  --  anywhere             anywhere
srcfilt    all  --  anywhere             anywhere

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem
srcfilt    all  --  anywhere             anywhere

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem
s1         all  --  anywhere             anywhere

Chain f0to1 (3 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain state NEW
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds state NEW
logdrop    all  --  anywhere             anywhere

Chain f1to0 (1 references)
target     prot opt source               destination
logdrop    all  --  anywhere             anywhere

Chain logaborted (1 references)
target     prot opt source               destination
logaborted2  all  --  anywhere             anywhere            limit: avg 1/sec burst 10
LOG        all  --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED '

Chain logaborted2 (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `ABORTED '
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED

Chain logdrop (4 references)
target     prot opt source               destination
logdrop2   all  --  anywhere             anywhere            limit: avg 1/sec burst 10
LOG        all  --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED '
DROP       all  --  anywhere             anywhere

Chain logdrop2 (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `DROPPED '
DROP       all  --  anywhere             anywhere

Chain logreject (0 references)
target     prot opt source               destination
logreject2  all  --  anywhere             anywhere            limit: avg 1/sec burst 10
LOG        all  --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED '
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset
REJECT     udp  --  anywhere             anywhere            reject-with icmp-port-unreachable
DROP       all  --  anywhere             anywhere

Chain logreject2 (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `REJECTED '
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset
REJECT     udp  --  anywhere             anywhere            reject-with icmp-port-unreachable
DROP       all  --  anywhere             anywhere

Chain nicfilt (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere
logdrop    all  --  anywhere             anywhere

Chain s0 (1 references)
target     prot opt source               destination
f0to1      all  --  anywhere             tty.org.uk
f0to1      all  --  anywhere             192.168.255.255
f0to1      all  --  anywhere             localhost
logdrop    all  --  anywhere             anywhere

Chain s1 (1 references)
target     prot opt source               destination
f1to0      all  --  anywhere             anywhere

Chain srcfilt (2 references)
target     prot opt source               destination
s0         all  --  anywhere             anywhere
[/FONT]

So how do I get it to remember the empty set of rules?

---

### Post by faulkes on 2008-03-05
What package did you install to provide you with iptables firewalling (i.e. paranoid settings).

The server by default does not install any rules.

Faulkes

---

### Post by Stephen_at on 2008-03-05
Oddly enough I had to install fiestarter because from the start there was no external access to the box.

I have NO firewall related packages installed now..

So where are the rules usually kept?

---

### Post by faulkes on 2008-03-05
As I have never needed a iptables package installed (by default I have my own scripts)
I can't answer that, especially for a gui package.

I would hazard a guess that they would be in /etc/ somewhere, probably 
/etc/network/if-pre-up.d or /etc/network/if-up.d

Faulkes

---

### Post by cdenley on 2008-03-05
Try this
```

sudo dpkg -P firestarter

```

---

### Post by Stephen_at on 2008-03-06
I'd been playing round with various things and it looks like when you remove guarddog it leaves its iptables scripts in the /etc/network if folders.

So I removed them and its now coming up with NO firewall rules in place at all.

So now I guess I can start working up a small set of rules to tighten up access to the mail server.

---

