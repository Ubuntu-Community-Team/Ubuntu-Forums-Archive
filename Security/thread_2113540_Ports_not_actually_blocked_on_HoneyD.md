---
title: "Ports not actually blocked on HoneyD"
date: 2013-02-07
forum: Security
---

### Post by nexusnode on 2013-02-07
Hey everyone!

First of all, thank you to everyone who reads or answers!

I am playing with honeyd for a little "weekend project" and I have it up and running but I am getting some off behaviour that I wanted to check by someone.  I have looked round the net but I can't find anything relevant, I don't know whether I am unique to my problem or possibly more likely that I just can't define the search terms well enough to get the right results.

I run Ubuntu 12.10 on my laptop, on which I have VMWare Player (5.0.1 build-894247) installed.  In VMWare Player I have an Ubuntu 12.04.1 Server installed.

In the VM I have HoneyD compiled from source and installed from [https://github.com/DataSoft/Honeyd](https://github.com/DataSoft/Honeyd) as of a few days ago.

My configuration is pretty simple - at this stage I am only testing really:
> create default
set default default tcp action block
set default default udp action block
set default default icmp action block

create windows
set windows default tcp action block
set windows default udp action block
set windows default icmp action allow
set windows personality "Microsoft Windows XP Professional SP3"
add windows tcp port 135 open
add windows tcp port 139 open
add windows tcp port 445 open

set windows ethernet "00:0c:38:8d:8c:17"
dhcp windows on eth0

and my honeyd init command is:
> sudo honeyd -d -f honeyd.conf 192.168.1.10-192.168.1.190

Just to be clear, I know that the DHCP in this network will give me an IP at roughly the .100 mark.

The only other thing to note is that for VMWare Player to allow the VM to use promiscuous mode I have also run this command:
> sudo chmod a+rw /dev/vmnet0

So that lot should be pretty standard.  Maybe a little boring, but would (and on the most part does) work:
> Honeyd V1.6a Copyright (c) 2002-2007 Niels Provos
honeyd[1053]: started with -d -f honeyd.conf 192.168.1.10-192.168.1.190
honeyd[1053]: listening promisciously on eth0: (arp or ip proto 47 or [and so on]
honeyd[1053]: [eth0] trying DHCP
honeyd[1053]: Demoting process privileges to uid 65534, gid 65534
honeyd[1053]: [eth0] got DHCP offer: 192.168.1.113
honeyd: Error opening the DHCP IP address dump file: Bad address
honeyd[1053]: Updating ARP binging: 00:0c:38:18:4f:a5 -> 192.168.1.113

And here is the weird bit.  On a third machine, i.e. completely seperated from the virtual host and virtual machine.  I run an nmap against the IP address that the honeypot has got (192.168.1.113) and it tells me that every single port is open...

---

### Post by nexusnode on 2013-02-07
Just realised I forgot to give a couple of bits of potentially useful info:

If I ping the honeypot IP I get responses and the following output is seen on the honeypot:

> honeyd[1045]: Sending ICMP Echo Reply: 192.168.1.113 -> 192.168.1.202

When I run "nmap 192.168.1.113" against it I get the following output on the machine running nmap:

> 
...
...
...
49165/tcp open  unknown
49167/tcp open  unknown
49175/tcp open  unknown
49176/tcp open  unknown
49400/tcp open  compaqdiag
49999/tcp open  unknown
50000/tcp open  ibm-db2
50001/tcp open  unknown
50002/tcp open  iiimsf
50003/tcp open  unknown
50006/tcp open  unknown
50300/tcp open  unknown
50389/tcp open  unknown
50500/tcp open  unknown
50636/tcp open  unknown
50800/tcp open  unknown
51103/tcp open  unknown
51493/tcp open  unknown
52673/tcp open  unknown
52822/tcp open  unknown
52848/tcp open  unknown
52869/tcp open  unknown
54045/tcp open  unknown
54328/tcp open  unknown
55055/tcp open  unknown
55056/tcp open  unknown
55555/tcp open  unknown
55600/tcp open  unknown
56737/tcp open  unknown
56738/tcp open  unknown
57294/tcp open  unknown
57797/tcp open  unknown
58080/tcp open  unknown
60020/tcp open  unknown
60443/tcp open  unknown
61532/tcp open  unknown
61900/tcp open  unknown
62078/tcp open  iphone-sync
63331/tcp open  unknown
64623/tcp open  unknown
64680/tcp open  unknown
65000/tcp open  unknown
65129/tcp open  unknown
65389/tcp open  unknown
(and it goes on up off the top of my ssh window buffer)

and on the honeypot I see:

> honeyd[1045]: Connection dropped by reset: tcp (192.168.1.202:60147 - 192.168.1.113:8402)
honeyd[1045]: Connection dropped by reset: tcp (192.168.1.202:55003 - 192.168.1.113:2701)
honeyd[1045]: Connection established: tcp (192.168.1.202:43470 - 192.168.1.113:10628) <-> block
honeyd[1045]: Connection dropped by reset: tcp (192.168.1.202:43470 - 192.168.1.113:10628)
honeyd[1045]: Connection established: tcp (192.168.1.202:36294 - 192.168.1.113:51103) <-> block
honeyd[1045]: Connection dropped by reset: tcp (192.168.1.202:36294 - 192.168.1.113:51103)honeyd[1045]: Connection established: tcp (192.168.1.202:47465 - 192.168.1.113:6543) <-> block
honeyd[1045]: Connection dropped by reset: tcp (192.168.1.202:47465 - 192.168.1.113:6543)
honeyd[1045]: Connection established: tcp (192.168.1.202:41826 - 192.168.1.113:667) <-> blockhoneyd[1045]: Connection dropped by reset: tcp (192.168.1.202:41826 - 192.168.1.113:667)
honeyd[1045]: Connection established: tcp (192.168.1.202:39115 - 192.168.1.113:49) <-> blockhoneyd[1045]: Connection dropped by reset: tcp (192.168.1.202:39115 - 192.168.1.113:49)


192.168.1.202 is the machine performing the nmap.

---

### Post by PherricOxide on 2013-02-08
That version of honeyd has slightly different words for describing port actions in order to match more with how nmap describes them. There's no longer a "block" keyword. It now uses,

For TCP,

 [INDENT]   filtered: ignore packets from that port
    open: responds with SYN ACK
    closed: responds with SYN RST[/INDENT]

For ICMP,
[INDENT]    open: respond to ICMP messages
    closed: don't respond to ICMP messages[/INDENT]

So your configuration file should be,

[INDENT]create default
set default default tcp action **filtered**
set default default udp action **filtered**
set default default icmp action **filtered**

create windows
set windows default tcp action **filtered**
set windows default udp action **filtered**
set windows default icmp action **closed**
set windows personality "Microsoft Windows XP Professional SP3"
add windows tcp port 135 open
add windows tcp port 139 open
add windows tcp port 445 open

set windows ethernet "00:0c:38:8d:8c:17"
dhcp windows on eth0[/INDENT]

You also might want to check out the **Nova** project, it provides a nice GUI for configuring honeyd so you don't have to deal with manually editing all the configuration files ([https://github.com/DataSoft/Nova](https://github.com/DataSoft/Nova)). (Shameless plug, I'm one of the developers of Nova)

---

### Post by nexusnode on 2013-02-08
Thank you very much good sir! That did the trick perfectly!

Was I being stupid or is this not documented anywhere?

---

### Post by PherricOxide on 2013-02-08
It's not documented very well. The man page for honeyd shows,

[INDENT]action  = ["tarpit"] ("filtered" | "open" | "closed" | cmd-string | "internal" cmd-string "proxy" ipaddr":"port )[/INDENT]

But other than that, afraid it isn't really documented well. We'll throw a note in the man page about it.

---

### Post by nexusnode on 2013-02-09
Thank you!

---

### Post by essra on 2013-05-25
> **nexusnode said:**
> Hey everyone!

First of all, thank you to everyone who reads or answers!

I am playing with honeyd for a little "weekend project" and I have it up and running but I am getting some off behaviour that I wanted to check by someone.  I have looked round the net but I can't find anything relevant, I don't know whether I am unique to my problem or possibly more likely that I just can't define the search terms well enough to get the right results.

I run Ubuntu 12.10 on my laptop, on which I have VMWare Player (5.0.1 build-894247) installed.  In VMWare Player I have an Ubuntu 12.04.1 Server installed.

In the VM I have HoneyD compiled from source and installed from [https://github.com/DataSoft/Honeyd](https://github.com/DataSoft/Honeyd) as of a few days ago.

My configuration is pretty simple - at this stage I am only testing really:


and my honeyd init command is:


Just to be clear, I know that the DHCP in this network will give me an IP at roughly the .100 mark.

The only other thing to note is that for VMWare Player to allow the VM to use promiscuous mode I have also run this command:


So that lot should be pretty standard.  Maybe a little boring, but would (and on the most part does) work:


And here is the weird bit.  On a third machine, i.e. completely seperated from the virtual host and virtual machine.  I run an nmap against the IP address that the honeypot has got (192.168.1.113) and it tells me that every single port is open...




I tried to use DHCP it gives error
"Need an ethernet address for DHCP"
In fact even using bind 192.168.1.10 windows
did not work  and I can not ping to it  from the same subnet "unreachable "
only nmap can detect it but can not detect open port
ICMP is open and all ports are open
I saw it in many videos connecting to the binded ip from external device 

can you pls help me sorting out this error in configuration

---

