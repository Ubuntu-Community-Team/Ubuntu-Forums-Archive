---
title: "Help with heartbeat &amp; pacemaker on EC2 1"
date: 2011-01-09
forum: Server Platforms
---

### Post by tnine on 2011-01-09
Hi all,
  I'm using the ubuntu 10.10 images here 
[http://uec-images.ubuntu.com/releases/10.10/release/](http://uec-images.ubuntu.com/releases/10.10/release/)
for my servers.  I have everything running correctly except our load balancer failover.  We have the following requirements.

1. Load balancer will be installed on 3 nodes.  An elastic IP will be assigned to the "leader" node in the quorum of servers.

2. When the leader node is terminated, I need a hook on the newly elected leader to run updates.  Pacemaker seems to fit the bill, so I can execute a script when a node becomes the leader node.

I've read through a lot of examples and documentation on both, but I'm still having some issues.  Any help with the following would be greatly appreciated.


1. My nodes in EC2 can't seem to communicate with one another.  I have installed pacemaker with the following command.


```

apt-get install heartbeat

```

I have this configuration file on every node at /etc/ha.d/ha.cf.

```

#Auto generated ha.conf file for all load balancer nodes
logfacility daemon
autojoin none
bcast eth0
use_logd yes
udpport 694
keepalive 2
warntime 5
deadtime 10
initdead 60
auto_failback on

node ip-10-160-138-192
node ip-10-160-233-27
node ip-10-160-58-200

```

all hosts share the same auth information

```

auth 1
1 sha1 imasupersecretkey

```


I've run nmap on every node to every other node to check that UDP 
port 694 is listening on every node and can be viewed from the other 2 nodes.  They all appear to be able to communicate at the network level.  I receive this from nmap.

```

root@ip-10-160-233-27:~# nmap -p 694 -sU -P0 ip-10-160-138-192

Starting Nmap 5.00 ( http://nmap.org ) at 2011-01-09 19:33 UTC
Interesting ports on ip-10-160-138-192.us-west-1.compute.internal (10.160.138.192):
PORT    STATE         SERVICE
694/udp open|filtered unknown

Nmap done: 1 IP address (1 host up) scanned in 2.42 seconds

```

When I run crm_mon -1, I receive the following output.

```

root@ip-10-160-58-200:~# crm_mon -1
============
Last updated: Sun Jan  9 19:28:08 2011
Stack: Heartbeat
Current DC: ip-10-160-58-200 (79170a75-1b64-43c8-80a1-ff4f490149e5) - partition WITHOUT quorum
Version: 1.0.8-042548a451fce8400660f6031f4da6f0223dd5dd
1 Nodes configured, unknown expected votes
0 Resources configured.
============

Online: [ ip-10-160-58-200 ]

root@ip-10-160-58-200:~# 

```

As you can see, each node can only view itself.


2. How do I configure Pacemaker via a file?  All of the examples I see are interactive.  We use chef to manage our server, so I need to programmatically create an input file to give Pacemaker that can execute the script only on the leader node.


Thanks in advance for any help you can provide!

Todd

---

