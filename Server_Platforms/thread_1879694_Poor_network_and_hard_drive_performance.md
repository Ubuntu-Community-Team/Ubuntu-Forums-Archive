---
title: "Poor network and hard drive performance"
date: 2011-11-12
forum: Server Platforms
---

### Post by Xylian on 2011-11-12
Hi,
after having upgraded to Ubuntu server 11.10 on my small embedded AMD Geode home server, I've noticed a dramatic degrade of both network throughput and hard drive performance.. 
*hdparm -tT /dev/sda* (after few executions) shows a max read speed of 38 MB/s, while it was 55 MB/s on average before:
```

# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   410 MB in  2.00 seconds = 204.76 MB/sec
 Timing buffered disk reads: 116 MB in  3.04 seconds =  38.17 MB/sec

```

I used to connect through FTP to my server to download data and I always had a very good throughput for my 100Mbps connection, i.e. about 9-10 MB/s... now it sometimes starts at 9-10 MB/s and then it goes down to max 4.5 MB/s... I think it could be a problem related to TCP/IP stack that maybe erroneously slows down the connection (it should not, since there is no network congestion) or to the ethernet driver.. the vsftpd daemon uses 40/50% of CPU on the server, but I think this should not be the problem, since there is available CPU free. The ethernet interface connected to my switch is an integrated Realtek interface, while the VIA Technologies one is used to connect the server to the ADSL modem (maybe I could try swapping the two..)
```

00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0d.0 Ethernet controller: VIA Technologies, Inc. VT6105M [Rhine-III] (rev 96)

```

Did any of you had similar experiences? I think Kernel 3 has brought us more problems than only the energy management issues.

---

