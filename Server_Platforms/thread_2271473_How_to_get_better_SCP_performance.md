---
title: "How to get better SCP performance"
date: 2015-03-30
forum: Server Platforms
---

### Post by joker535 on 2015-03-30
Lately I have been transferring a lot of large files between my workstation and one of my servers. Both are connected to the same gigabit switch. 

[I]sudo scp bigfatfile.ISO root@192.168.0.3:/var/run/sr-mount/259d4aed-7361-2cc6-cbf4-74349f25e819/ISO_Storage/

bigfatfile 100% 4338MB  **58.6MB/s**   01:14 [/I]

On a 4G ISO file I am seeing 50-70MB/s max.** Is there a way to do better? **

Both machines are pretty beefy (Workstation - Dual quad core L5310 Xeon w/16G and SSDs on a hardware raid array | Server -  single quad HT Xeon E3-1230Lv3 w/16G and SSDs on a hardware raid array) so I don't think its a hardware issue.

Thanks

---

### Post by Doug S on 2015-03-30
> **joker535 said:**
> Both machines are pretty beefy (Workstation - Dual quad core L5310 Xeon w/16G and SSDs on a hardware raid array | Server -  single quad HT Xeon E3-1230Lv3 w/16G and SSDs on a hardware raid array) so I don't think its a hardware issue.The issue might still be CPU limitations. SCP is a single thread, and so there is little benefit from multiple CPUs and such.

I would suggest to examine each stage of your transfer (disk read rate on sender, sender CPU load, receiver disk write rate, receiver CPU load) to identify the bottleneck.
As an experiment, I did so on a couple of my Ubuntu servers, and found this (from top):```
top - 14:17:32 up 34 days, 23:47,  5 users,  load average: 1.20, 0.69, 0.32
Tasks: 108 total,   2 running, 106 sleeping,   0 stopped,   0 zombie
Cpu0  : 37.7%us, 10.0%sy,  0.0%ni, 43.8%id,  0.0%wa,  0.0%hi,  8.5%si,  0.0%st
Cpu1  : 38.1%us, 11.0%sy,  0.0%ni, 45.2%id,  5.4%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   3073824k total,  2994792k used,    79032k free,   142908k buffers
Swap:  3133436k total,        0k used,  3133436k free,  2520716k cached

  PID USER      PR  NI  VIRT  RES  SHR S [COLOR=#ff0000]%CPU[/COLOR] %MEM    TIME+  COMMAND
12076 doug      20   0  135m 6308  804 R   [COLOR=#ff0000]88[/COLOR]  0.2   3:19.29 [COLOR=#ff0000]sshd[/COLOR]
12077 doug      20   0 12772  772  636 S   [COLOR=#ff0000]11[/COLOR]  0.0   0:23.56 [COLOR=#ff0000]scp[/COLOR]
   27 root      20   0     0    0    0 S    2  0.0   3:06.27 kswapd0
  269 root      20   0     0    0    0 S    0  0.0   1:05.28 jbd2/dm-0-8
 1398 root      20   0     0    0    0 S    0  0.0   1:41.05 flush-252:0
...
```On my receiver server. From [this page]("http://www.openssh.com/features.html"), I decided to try a different cipher and my average transfer rate jumped. from ~40 megabytes per second to ~80 megabytes per second.
```
doug@s15:~/c$ [COLOR=#ff0000]scp big doug@bla:/home/doug/c/big[/COLOR]
big  100%   50GB  [COLOR=#ff0000]41.6MB/s[/COLOR]   20:32
```
```
doug@s15:~/c$ [COLOR=#ff0000]scp -oCiphers=arcfour big doug@bla:/home/doug/c/big[/COLOR]
big  100%   50GB  [COLOR=#ff0000]82.6MB/s[/COLOR]   10:20
```with this for top on the receiver:```
top - 15:57:39 up 35 days,  1:27,  5 users,  load average: 1.49, 0.58, 0.62
Tasks: 108 total,   2 running, 106 sleeping,   0 stopped,   0 zombie
Cpu0  : 20.2%us, 25.5%sy,  0.0%ni,  2.7%id, 35.7%wa,  0.0%hi, 16.0%si,  0.0%st
Cpu1  : 26.1%us, 29.4%sy,  0.0%ni, 34.4%id, 10.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3073824k total,  2994320k used,    79504k free,   146084k buffers
Swap:  3133436k total,        0k used,  3133436k free,  2517312k cached

  PID USER      PR  NI  VIRT  RES  SHR S [COLOR=#ff0000]%CPU[/COLOR] %MEM    TIME+  COMMAND
12816 doug      20   0  135m 6188  904 R   [COLOR=#ff0000]70[/COLOR]  0.2   0:29.82 [COLOR=#ff0000]sshd[/COLOR]
12817 doug      20   0 12772  776  636 S   [COLOR=#ff0000]26[/COLOR]  0.0   0:10.88 [COLOR=#ff0000]scp[/COLOR]
 1398 root      20   0     0    0    0 S    5  0.0   2:46.34 flush-252:0
   27 root      20   0     0    0    0 S    4  0.0   3:44.81 kswapd0
```Also notice the percent wait times are much higher, as I suspect for my case I am getting close to the disk write limit.

---

### Post by joker535 on 2015-03-30
Cool. I will try that out. 

Thanks

---

### Post by tgalati4 on 2015-03-30
Use *iperf* between the server and client to get an idea of the raw, network transfer speeds.

---

### Post by Doug S on 2015-03-31
> **tgalati4 said:**
> Use *iperf* between the server and client to get an idea of the raw, network transfer speeds.Agh, thanks. I could not remember the program name earlier. Here is what I get on my network for the above example:```
doug@s15:~/temp/dirk/cpuload3/cpuload$ [COLOR=#ff0000]iperf -f MBytes -t 10 -c bla[/COLOR]
------------------------------------------------------------
Client connecting to bla, TCP port 5001
TCP window size: 0.08 MByte (default)
------------------------------------------------------------
[  3] local 192.168.111.112 port 34376 connected with 192.168.111.1 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  1122 MBytes   [COLOR=#ff0000]112 MBytes/sec[/COLOR]
```

---

### Post by tgalati4 on 2015-03-31
So 58 MB/sec is about half of 112 MB/sec.  I would presume that the ssh connection (that scp uses) requires some overhead between the two machines to encrypt and decrypt the data.  It's also possible that other machines on your network are squawking which will reduce bandwidth.

Older versions of linux had a true version of *rcp*, which allows remote copy with out encryption.  But now *rcp* points to *scp*.  So you can't use *rcp* as a comparison.

> tgalati4@Mint17 ~ $ which rcp
/usr/bin/rcp
tgalati4@Mint17 ~ $ ls -la /usr/bin/rcp
lrwxrwxrwx 1 root root 21 Dec 19 10:54 /usr/bin/rcp -> /etc/alternatives/rcp
tgalati4@Mint17 ~ $ ls -la /etc/alternatives/rcp
lrwxrwxrwx 1 root root 12 Dec 19 10:54 /etc/alternatives/rcp -> /usr/bin/scp


Remove other devices from the switch and try again.  Check the policies on the switch, there may be some packet-shaping and QoS rules to allow VOIP priority, and that will limit your bandwidth.

---

### Post by nerdtron on 2015-03-31
And also, don't forget test the read/write speed of source and destination servers. I remember once, even with hardware raid setup on an old server, read/write speed are not really great. Adding scp encryption will just make the transfer slower.

Also, since your file is not very compressible you maybe already on your max transfer rate. But if you are transferring large file that are highly compressible (like databases), you can try "rsync" which have the compress option before transferring (small file = faster transfer)

---

