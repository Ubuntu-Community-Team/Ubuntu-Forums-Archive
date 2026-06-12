---
title: "NAS datarate &lt; 8MB/s"
date: 2009-02-11
forum: Server Platforms
---

### Post by RoadRunner2000 on 2009-02-11
Hi,

recently I've setup a server. The main purpose is a fileserver for me and my family (4 PC's). The HW config is
Athlon X2 4850e, M3A-H/HDMI, DIMM 4 GB DDR2-800 Kit, 
1 x 60GB 2,5' system drive
3 x WD6400AACS 640 GB SW RAID6 (mdadm)
Xubuntu 8.10 x86

To have the possibilty for a remote desktop, I've chosen Xubuntu not the ubunutu server edition.

Performance:
Now I was expecting to get datarate at least as high as 40MB/s. My first tests with the RAID array and bonnie++ confirmed this:

Sequential Output Chr: 34896K/sec
Sequential Input Chr: 25032K/sec

I've also checked the network connection from the server to the client through netio:
Packet size 32k bytes: 114183 KByte/s Tx,  75699 KByte/s Rx.

But now when accessing the server through samba or ftp (vsftpd) the datarate stay constant @7-8MB/s. The strange thing for me is that for both ftp **and** samba the problem is the same, so no configuration issue. So I thought it might be something in the kernel that is limiting the bandwidth for certain services ...

Any ideas?

Thanks, RoadRunner

---

### Post by cariboo on 2009-02-11
You do realize that network speed is measured in Mbps not MBps, 7-8MBps = 70-80Mbps, which is what you expected.

I use iperf to test network speed between computers, it is available in the repositories. Once installed on two coputers setup one system as the server:

```
iperf -s
```

then on the other computer in a terminal type:

```
iperf -c <server>
```

You should get a result something like this:

```
 iperf -c willy
------------------------------------------------------------
Client connecting to willy, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.100 port 51643 connected with 192.168.1.200 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.1 sec    115 MBytes  95.7 Mbits/sec
```

The above result is acceptable as my network is running 100Mbps nics, and there are quite a few different connectors between my network in the house and the network in my stand alone garage.

Jim

---

### Post by RoadRunner2000 on 2009-03-02
FYI:

Linux -> Good :-)
Windows -> Bad!!!

After looking for 2month now into this problem, I've finally solved it. The bad guy is a Windows service called WebClient. Once disabled I get the expected datarates of 30MByte/s writing and 60MByte/s reading. I've no idea what this service is good for ...

---

### Post by JeppeM on 2009-03-02
It should be possible without disabling the WebClient service... We have a ubuntu 8.04 server set up on a 1 GBit network, and we get at least 50MB/s when transfering via. ftp to the server, from both windows, mac and linux computers - And we haven't changed anything on the windows computers to make this possible.

---

### Post by RoadRunner2000 on 2009-03-03
hhmmm...

I've reenabled the WebClient service and it still seems alright (30-50MByte/s). The server configuration has also not changed for a couple of weeks. I don't know whats going on ...

Right now I've run out of ideas, but I keep you updated in case something occurs [-o<

---

