---
title: "How to restore iptables starting script"
date: 2007-11-30
forum: Server Platforms
---

### Post by satimis on 2007-11-30
Hi folks,


Ubuntu 7.04 server amd64


Just found iptables NOT running which, I suppose, was caused by accidentally deleting /home/satimis previously.


$ sudo /etc/rc.local start/stop/restart
No response (w/o printout)


Neither I find;
$ sudo ls /etc/init.d/ | grep iptables
No printout


The file /etc/rc.local is still there with rules intact.


$ ls -l /sbin/iptables```

-rwxr-xr-x 1 root root 57336 2007-07-06 02:17 /sbin/iptables

```
is still there.


Please advise where can I get the starting script "iptables" back?

Which is the correct step starting iptables;
$ sudo /etc/rc.local
???

OR
$ sudo /etc/init.d/iptables
???


Please advise.  TIA


B.R.
satimis

---

### Post by MJN on 2007-12-01
I think there might be some misunderstanding here. **iptables** itself is not the firewall and hence is not constantly running. Rather, the actual firewall (ip**_**filter) is in the kernel and you merely use iptables as the tool to administer the firewall rules - it's a one-shot application that runs only when modifying the firewall rules.

Hence, there will be no iptables control script in /etc/init.d/ (given the firewall is automatically started by virtue of it being in the kernel) and similarly a ps aux will not reveal iptables as running because it isn't (well, you might be lucky and catch it for the brief moments it runs whilst modifying firewall rules).

If you run **lsmod |grep ip_tables** you will see if the firewall module is loaded/running (if you get any output then it is). Run **sudo iptables -L** and you will see your current firewall rules - given you've got a rule script in rc.local you should see your rules listed.

Does that make sense?

Mathew

---

### Post by satimis on 2007-12-01
> **MJN said:**
> I think there might be some misunderstanding here. **iptables** itself is not the firewall and hence is not constantly running. Rather, the actual firewall (ip**_**filter) is in the kernel and you merely use iptables as the tool to administer the firewall rules - it's a one-shot application that runs only when modifying the firewall rules.

Hence, there will be no iptables control script in /etc/init.d/ (given the firewall is automatically started by virtue of it being in the kernel) and similarly a ps aux will not reveal iptables as running because it isn't (well, you might be lucky and catch it for the brief moments it runs whilst modifying firewall rules).

If you run **lsmod |grep ip_tables** you will see if the firewall module is loaded/running (if you get any output then it is). Run **sudo iptables -L** and you will see your current firewall rules - given you've got a rule script in rc.local you should see your rules listed.

Does that make sense?
Hi Mathew,


Thanks for your advice.


In fact I have some confusion on iptables.  Several years ago I ran shorewall/monowall as firewall.  At that time to my understanding they were the front-end of iptables.  The backend was still iptables.  So I thought why should I need the front-end if I have the backend running.  Since then I only installed iptables on PC.  If I have a tool for configuring/controlling the packet inspection/filtering capabilities (Netfilter) in the kernel, that will be secure enough.

I found the start script on /etc/init.d/rc.local natvigated with only start/stop w/o restart/reload/status.  I hesitate whether it is the rigth script.  Iptables rules are on /etc/rc.local

$ lsmod | grep ip_tables```

ip_tables              23080  1 iptable_filter
x_tables               23688  4 ipt_REJECT,xt_tcpudp,xt_state,ip_tables

```
Why here iptables breaking into 2 parts connected with underscore?


$ sudo iptables -L```

Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             220.232.213.178     state RELATED,ESTAB
LISHED 
ACCEPT     tcp  --  anywhere             220.232.213.178     tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             220.232.213.178     tcp dpt:8222 
ACCEPT     tcp  --  anywhere             220.232.213.178     tcp dpt:8333 
ACCEPT     tcp  --  anywhere             220.232.213.178     tcp dpt:vmware-auth
d 
REJECT     0    --  anywhere             220.232.213.178     reject-with icmp-po
rt-unreachable 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  220.232.213.178      anywhere            state RELATED,ESTAB
LISHED 
ACCEPT     udp  --  220.232.213.178      anywhere            udp dpt:domain 
REJECT     0    --  localhost.localdomain  anywhere            reject-with icmp-
port-unreachable 
REJECT     0    --  220.232.213.178      anywhere            reject-with icmp-po
rt-unreachable 

```


Thanks



B.R.
satimis

---

### Post by MJN on 2007-12-01
The confusion is understandable given we (me included) seem to use the various terms interchangably even though technically speaking they are different aspects to firewalling.

To clarify, and starting at the lowest level, we have:

netfilter - this is merely the mechanism by which it becomes possible to hook into the network stack, for example to to allow...
ip_tables - this kernel module uses netfilter to intercept packets in the network stack and filter them based on rules defined by...
iptables - an administration tool to enable you to define the ruleset that ip_tables will follow.

At an even higher level we then have:

shorewall - a high-level admin tool to not only let you define (easily) firewall rules to be used by netfilter/ip_tables but also to provide other related features besides such as monitoring and general management etc
firestarter - yet another admin tool but providing a GUI frontend to iptables

Only netfilter and ip_tables are constantly running as they are effectively the firewall (i.e. something to intercept the packets and another to decide what to do with them).

I don't think you've got anything to worry about as your firewall is running, and configured. If you can get your head around the above then you're sorted.

Mathew

---

