---
title: "NFS Server Problem - atl1c driver issue?"
date: 2010-01-05
forum: Server Platforms
---

### Post by sir_blargh on 2010-01-05
I recently upgraded my file server's hardware from a P4 400MHz processor to an Atom 330.  With the new motherboard, I am now using the onboard NIC (Attansic Technology Corp. Device 1063 (rev c0) -- uses atl1c driver) as opposed to an Intel PCI (e1000) add-on card that I was using previously.  All of the disks are the same and the configuration was not changed, but I am now having problems with NFS clients connecting to that server.

Mostly the clients are able to mount and "ls" the NFS shares. 
```

(sir_blargh) file-client:~
502 -> sudo mount -t nfs file-server:/home/sir_blargh/Videos/Movies /home/sir_blargh/Videos/Movies

(sir_blargh) file-client:~
503 -> ls ~/Videos/Movies
Subtitles
*.avi
etc...

(sir_blargh) file_client:~
504 -> cat /proc/mounts | grep nfs
file-server:/home/sir_blargh/Videos/Movies /home/sir_blargh/Videos/Movies nfs rw,vers=3,rsize=131072,wsize=131072,namlen=255,hard,nointr,proto=tcp,timeo=600,retrans=2,sec=sys,mountaddr=192.168.1.110,mountvers=3,mountproto=tcp,addr=192.168.1.110 0 0

```

On the server, syslog shows the following output:

```
Jan  5 07:49:23 blargh-server mountd[1606]: authenticated mount request from 192.168.1.100:802 for /home/sir_blargh/Videos/Movies (/home/sir_blargh/Videos/Movies)
```

So you'd think it was working, right?  Unfortunately virtually as soon as you try to access a file, the I/O will hang and eventually the file client's dmesg output will show:

```
nfs: server file-server not responding, still trying
```

At the same time, from the client side:

```
(sir_blargh) file-client:~
507 -> rpcinfo -p file-server
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  41238  status
    100024    1   tcp  55833  status
    100021    1   udp  38360  nlockmgr
    100021    3   udp  38360  nlockmgr
    100021    4   udp  38360  nlockmgr
    100021    1   tcp  59774  nlockmgr
    100021    3   tcp  59774  nlockmgr
    100021    4   tcp  59774  nlockmgr
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp  42451  mountd
    100005    1   tcp  57648  mountd
    100005    2   udp  42451  mountd
    100005    2   tcp  57648  mountd
    100005    3   udp  42451  mountd
    100005    3   tcp  57648  mountd

(sir_blargh) file-client:~
504 -> ps aux | grep " D"
scott     4405  0.0  0.0   3428   920 pts/1    D+   08:04   0:00 cp Videos/Movies/*.avi /tmp/

```

So it looks like things are OK on the file-server from the rpcinfo output, but not really, as the client's I/O is hung.

Initially I thought it might be a hardware issue (since hey, that's what I changed!) But while the nfs server is unreachable, I am still fully able to ssh into it.  Additionally, I have a samba share of the same directory and it is also completely accessible and does not suffer the same fate.

Any other ideas, or is there some way to increase the verbosity of my NFS logs?

And no, there are no firewalls in place on either machine.

Thanks...

---

### Post by sir_blargh on 2010-01-05
I should also probably note:

```

(sir_blargh) file-server:~
505 -> uname -a
Linux file-server 2.6.31-16-generic-pae #53-Ubuntu SMP Tue Dec 8 05:20:21 UTC 2009 i686 GNU/Linux

(sir_blargh) file-client:~
501 -> uname -a
Linux file-client 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 18:57:07 UTC 2009 i686 GNU/Linux
```

The server is ubuntu server 9.10 32-bit, the client(s) are both ubuntu desktop 9.10 32 and 64 bit.   The problem exists on all clients.

---

### Post by sir_blargh on 2010-01-05
Also, I can scp large files back and forth between the client / server with no problems.

'ifconfig' shows a reasonable output:

```

(sir_blargh) file-server:/proc/irq/25
516 -> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:11:c6:b4:a6
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:11ff:fec6:b4a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50731 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89732 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:4068527 (4.0 MB)  TX bytes:113903842 (113.9 MB)
          Interrupt:25

```

---

### Post by sir_blargh on 2010-01-05
A suggestion on the ubuntu irc channel was to mount an NFS share locally on the server.  I did that and was able to able to copy large files without a problem.  So the new network card is certainly causing issues.

---

### Post by tad1073 on 2010-01-05
I am having the same issues, but I am unable to mount the nfs share through fstab. The problem with the fstab issue is due to the fact that I am on a wireless connection, I believe. When copying large files such as video's my system becomes unresponsive then the share is unmounted.

---

### Post by sir_blargh on 2010-01-05
Using the same network device?  Additionally I enabled more debug logging ('rpcdebug -m module -s all' for all modules) and am seeing lots of svc: transport %p busy, not enqueued messages on the server's dmesg output.

---

### Post by tad1073 on 2010-01-05
server ethernet controller

```
description: Ethernet interface
                product: 82540EM Gigabit Ethernet Controller
                vendor: Intel Corporation

Link encap:Ethernet  HWaddr 00:0d:56:1a:11:d8  
          inet addr:192.168.0.2  Bcast:192.168.0.7  Mask:255.255.255.248
          inet6 addr: fe80::20d:56ff:fe1a:11d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1378881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1620104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:995766266 (995.7 MB)  TX bytes:1780954117 (1.7 GB)


```


client wireless controller

```
description: Wireless interface
                product: AR5008 Wireless Network Adapter
                vendor: Atheros Communications Inc.
Link encap:Ethernet  HWaddr 00:21:91:06:37:28  
          inet addr:192.168.0.4  Bcast:192.168.0.7  Mask:255.255.255.248
          inet6 addr: fe80::221:91ff:fe06:3728/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1458 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1047 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1106739 (1.1 MB)  TX bytes:123038 (123.0 KB)

```

---

### Post by rockrman on 2010-01-26
could be similar to this ticket?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512764](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512764)

---

