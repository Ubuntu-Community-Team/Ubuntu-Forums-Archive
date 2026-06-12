---
title: "SGE master/exec node doesn't work"
date: 2011-10-24
forum: Server Platforms
---

### Post by toontu on 2011-10-24
I am using Ubuntu 11.10 server. Installed SGE from Ubuntu repository. Java is the latest version. The current cluster structure is quite simple: one master node and one slave node. Both are execution nodes as well as submit nodes.

I edited /etc/hosts on both nodes. On the slave node, I added a new line of <ip> masternodename. On the master node, it looks like (which gives me headache)

127.0.0.1 localhost
#127.0.1.1 masternodename
<ip1> masternodename
<ip2> slavenodename
.....

/etc/nsswitch.conf:
.....
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
.....

If I run hostname --all-fqdns, the return is masternodename masternodename.local.

I know by default in Ubuntu, 127.0.1.1 shouldn't be commented out. But the current setting is the only way I can get qmaster connected and submit jobs.

The problem now I have is that if I submit a very simple job like displaying date and hostname from the master node, the job is straight sent to the slave node for execution. The output files will be sent to the slave node. Also if on the slave node there isn't a same directory as on the master node from which I submit a job, an error returns. E.g. a job sent from the master node ~/test; then if no ~/test on the slave node, "No such directory or file" will be reported.

I tried to restart gridengine-exec on the master node. I got this error: can't find connection
error: can't get configuration from qmaster -- backgrounding

This is probably what causes the problem. I tried many different ways of setting /etc/hosts, like

127.0.0.1 localhost
127.0.1.1 masternodename.local masternodename
<ip1> masternodename
<ip2> slavenodename

and also

in /etc/nsswitch.conf:

hosts: files dns mdns4_minimal [NOTFOUND=return] mdns4

with no luck and qmaster has stopped working.

I am a bit deflated but determined to solve the problem. So any help is warmly welcomed.

Many many thanks.

---

