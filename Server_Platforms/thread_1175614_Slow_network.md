---
title: "Slow network"
date: 2009-06-01
forum: Server Platforms
---

### Post by Arkaman on 2009-06-01
I am running a windows network and it is slow on Mac and Ubuntu.  Is that just how its going to be? On windows it takes about 1 sec to load a network directory but on Ubuntu it takes 40 seconds.  Any advice would be helpful.  If there is no way to make it go faster then I might just make another server that is running Linux.  Maybe that is the best way to do it IDK. Like I said any help would be helpful. Thanks!


-ARKaMAN

---

### Post by cariboo on 2009-06-01
It sounds like you have a misconfiguration of some sort, connecting to shares running ubuntu is quicker for me than  running Vista or Win 7, and about the same for XP. A lot depends on how your network is configured.

Are you using Samba to connect to shares? NFS?

We need more infoprmation about your network setup.

---

### Post by cariboo on 2009-06-01
I would suggest using iperf to check your network speeds. Iperf is in the rpositories, and there is a mac and windows version available. Once you have iperf installed, setup one computer as a server:

```
iperf -s
```

then from one of the other computers on your network run:

```
iperf -c <server>
```

you should get a result something like this:

```
iperf -c willy
------------------------------------------------------------
Client connecting to willy, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.100 port 49569 connected with 192.168.1.250 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    113 MBytes  94.5 Mbits/sec
```

The results indicate 94.3Mbps which is about right for my network.

BTW to run iperf in Windows you also have to use the command line.

---

