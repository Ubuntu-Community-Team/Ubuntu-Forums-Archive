---
title: "Iptables Configuration probelm"
date: 2007-09-25
forum: Server Platforms
---

### Post by nwk2007 on 2007-09-25
I recently setup a server and installed the homeLANsecurity, iptables result shown difference from other server:

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED
FLOOD      tcp  --  anywhere             anywhere
ICMP       icmp --  anywhere             anywhere
INVALID    tcp  --  anywhere             anywhere
BASIC      0    --  anywhere             anywhere
ACCEPT     0    --  anywhere             anywhere
ACCEPT     0    --  anywhere             anywhere

-------------------------------------------------------
The protocol should be "all" , instead of "0" for the first line of the INPUT chain and the rest. Anyone could help? Thanks in advance !

---

### Post by koenn on 2007-09-25
the 0 stands for "all"

---

### Post by nwk2007 on 2007-09-26
Thanks Koenn ! My exact problem is the Citrix ICA client for windows shown connected to server but it's windows doesn't show up, same as while using the VNC client. My PC is connected via Ubuntu 7.04 Gateway. I even open up the Citrix ICA protocol, but it doesn't help.

iptables -A INPUT-p tcp --dport 1494 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 1494 -j ACCEPT

Please help. Thanks.

---

