---
title: "Problems with both rbldnsd &amp; djbdns"
date: 2009-01-16
forum: Server Platforms
---

### Post by Narf on 2009-01-16
I need to setup a DNS blacklist with my own database and Google says that rbldnsd & djbdns are the best for this purpose.

rbldnsd seems to be both more lightweight and more flexible than anything else, so I tried it first. It was in my repositories, so I simply got if from there and in less than 2 minutes I had it running.
But there the problem appeared ... no warrning or error messages, program says it runs fine, but it doesn't bind to the specified address no matter what.

```
root@core:~/rbldnsd# -u rbldnsd -w /root/rbldnsd/ -b 127.0.0.1/53 -4 -c 5 -p dnsbl.pid -l dnsbl.log -s dnsbl.stats dnsbl.rbl:ip4tset:dnsbl.db
rbldnsd: listening on 127.0.0.1/53
rbldnsd: ip4tset:dnsbl.db: 20090116 103158: cnt=1159
rbldnsd: zones reloaded, time 0.1e/0.0u sec, mem arena=130 free=69 mmap=0 Kb
rbldnsd: rbldnsd version 0.996b (29 Mar 2008) started (1 socket(s), 1 zone(s))
root@core:~/rbldnsd# nmap 127.0.0.1 -p53

Starting Nmap 4.62 ( http://nmap.org ) at 2009-01-16 14:11 EET
Interesting ports on localhost (127.0.0.1):
PORT   STATE  SERVICE
53/tcp closed domain

Nmap done: 1 IP address (1 host up) scanned in 0.048 seconds
root@core:~/rbldnsd#
```

Log file doesn't say anything bad, the process is running, no other process is using the same ip/port, I've tried binding to other (both public and private) addresses and ports, compiling from source, etc. - it just doesn't bind.

After hours of searching for a solution on the net I gave it up and installed djbdns. Well, at least I tried to install it:

```
root@core:/# apt-get install djbdns
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  daemontools daemontools-run ucspi-tcp
The following NEW packages will be installed:
  daemontools daemontools-run djbdns ucspi-tcp
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 371kB of archives.
After this operation, 1835kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ubuntu.ipacct.com intrepid/universe daemontools 1:0.76-3 [65.5kB]
Get:2 http://ubuntu.ipacct.com intrepid/universe daemontools-run 1:0.76-3 [9372B]
Get:3 http://ubuntu.ipacct.com intrepid/universe djbdns 1:1.05-2 [206kB]
Get:4 http://ubuntu.ipacct.com intrepid/universe ucspi-tcp 1:0.88-2 [90.1kB]
Fetched 371kB in 0s (1453kB/s)
Selecting previously deselected package daemontools.
(Reading database ... 31350 files and directories currently installed.)
Unpacking daemontools (from .../daemontools_1%3a0.76-3_i386.deb) ...
Selecting previously deselected package daemontools-run.
Unpacking daemontools-run (from .../daemontools-run_1%3a0.76-3_all.deb) ...
Selecting previously deselected package djbdns.
Unpacking djbdns (from .../djbdns_1%3a1.05-2_i386.deb) ...
Selecting previously deselected package ucspi-tcp.
Unpacking ucspi-tcp (from .../ucspi-tcp_1%3a0.88-2_i386.deb) ...
Processing triggers for man-db ...
Setting up daemontools (1:0.76-3) ...
Setting up daemontools-run (1:0.76-3) ...
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
Adding SV inittab entry...
cp: cannot stat `/etc/inittab': No such file or directory
dpkg: error processing daemontools-run (--configure):
 subprocess post-installation script returned error exit status 1
Setting up djbdns (1:1.05-2) ...
Setting up ucspi-tcp (1:0.88-2) ...
Errors were encountered while processing:
 daemontools-run
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@core:/#
```

apt-get with --fix-broken doesn't help, nor downloading the .deb from another mirror.

Does anybody have a solution? Or at least an alternative to those two?

---

### Post by joebeasley on 2009-01-17
First make sure nothing is running on port 53 using netstat -vanu.  Run your command, but add a "&" (without the quotes) to the end to run the program in the background.  Then check netstat -vanu to see if it is listening on port 53.

---

### Post by Narf on 2009-01-18
> **joebeasley said:**
> First make sure nothing is running on port 53 using netstat -vanu.  Run your command, but add a "&" (without the quotes) to the end to run the program in the background.  Then check netstat -vanu to see if it is listening on port 53.

I did check everything and the program is a daemon, so it does run in the background.

---

