---
title: "Apt-get archive.ubuntu.com failing"
date: 2008-04-25
forum: Server Platforms
---

### Post by vital101 on 2008-04-25
Hey Everyone,

I'm running a server with Dapper Server installed on it.  I've had it running for about 1.5 years with no problems at all.  However, now when I try to install something, I get the following:

```

admin@DapperServer:/etc/apt$ sudo apt-get install bind9
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libdns21 libisc11 libisccc0 libisccfg1
Suggested packages:
  bind9-doc
The following NEW packages will be installed:
  bind9
The following packages will be upgraded:
  libdns21 libisc11 libisccc0 libisccfg1
4 upgraded, 1 newly installed, 0 to remove and 83 not upgraded.
Need to get 1137kB of archives.
After unpacking 721kB of additional disk space will be used.
Do you want to continue [Y/n]? y
0% [Connecting to archive.ubuntu.com (91.189.92.3)]


```

It just hangs while trying to connect to archive.ubuntu.com.  My tracepath looks like:

```

 1:  192.168.1.101 (192.168.1.101)                          0.366ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                            asymm 36   1.634ms 
 2:  10.67.80.1 (10.67.80.1)                               10.512ms 
 3:  172.19.49.117 (172.19.49.117)                         21.382ms 
 4:  172.19.47.153 (172.19.47.153)                         17.991ms 
 5:  24-247-236-20.static.aldl.mi.charter.com (24.247.236.20)  22.038ms 
 6:  172.19.49.219 (172.19.49.219)                         35.937ms 
 7:  64.127.129.9 (64.127.129.9)                           27.181ms 
 8:  nyc-ten1-4-ord-ten1-2.wvfiber.net (66.216.48.206)     58.297ms 
 9:  66.216.48.214 (66.216.48.214)                        125.587ms 
10:  66.216.50.78 (66.216.50.78)                          163.730ms 
11:  ge2-24-0-cr0.nik.nl.as6908.net (195.69.145.145)      139.487ms 
12:  78.41.155.186 (78.41.155.186)                        151.579ms 
13:  ugni.canonical.com (91.189.92.2)                     169.665ms reached
     Resume: pmtu 1500 hops 13 back 13 

```

I haven't installed anything that would effect this, and none of this traffic would be getting blocked on my end.  Any ideas on what might be going on? Is anyone else having this problem?

Thanks,
vital101

---

### Post by guj4_n3b3sk4 on 2008-04-25
Same problem with me. I have tried several times to do sudo apt-get update, and when it should connect to archive.ubuntu.com, terminal line just stands there, and no responce at all. I tried like 3 times, and eventualy, I've downloaded that 400 bytes I've waited for 20 minutes.

---

### Post by vital101 on 2008-04-25
Still, it shouldn't be lagging (if it could be called that) this badly.  Any ideas on WHY this is happening?

---

### Post by hggdh on 2008-04-25
Only a Canonical/Ubuntu admin can actually say, but we just released Hardy... I would expect a *lot* of people upgrading. Response time will be from bad to extremely bad.

It might be a good idea to try a mirror instead of the main archive.

---

### Post by Scotty Bones on 2008-04-25
There has to be something wrong here. It can't just be high network traffic.
The last update I preformed was one day prior to the final release of hardy.  Repos are now failing (security and archive (and also remastersys repo that has nothing to do with the ubuntu repos)) and I have not been able to receive a single update since.  The strange thing is that update manager reports "the package information was last updated 5 days ago."

---

### Post by aboutblank on 2008-04-25
I want to say it's largely a load-balancing problem. Here's my suggestion:

System - Administration - Software Sources

Ubuntu Software Tab - "Download from" drop down menu - Other - Select Best Server

This little known utility will do a pretty good job of picking a good server based on the response time it gets from them. I had the same problem you all are having until I did this and now can max out my connection from an MIT mirror.

---

### Post by gtdaqua on 2008-04-26
Its been so slow because of Hardy's release. apt-get installs took ages to download small packages! However, the speed was improving over time.

---

