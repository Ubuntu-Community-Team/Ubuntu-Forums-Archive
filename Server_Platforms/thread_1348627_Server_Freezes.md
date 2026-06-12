---
title: "Server Freezes"
date: 2009-12-07
forum: Server Platforms
---

### Post by jiriki on 2009-12-07
I have issue with an ubuntu server running several gaming servers. The problem is that under load the server freezes for a few seconds. This actually stops all other services aswell for the same time. First I thought it was a CPU issue but the HLDS is not taking more than 30-50% of one CPU (there are 8 since its Hyper-Threading, dunno if I should turn it off though).

The server is [i7 QuadCore with 8GB of RAM](http://www.hetzner.de/en/hosting/produkte_rootserver/eq4/).

I might have a clue since I get these messages in the dmesg, but they don't appear always with the freezes, just randomly. This would mean the NIC driver or the NIC itself can't handle the number of packets.

```
[5647741.993088] r8169: eth0: link up
[5648011.993460] r8169: eth0: link up
[5650136.003582] r8169: eth0: link up
```

```
Linux 2.6.28-15-server (medpack)        12/07/2009      _x86_64_        (8 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           5.89    0.00    2.06    0.11    0.00   92.05

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda              14.24      1005.16       569.77 5754180074 3261731544
sda1              0.05         4.70         1.21   26904888    6918808
sda2              0.02         2.21         0.02   12633288     115104
sda3             14.17       998.26       568.54 5714641682 3254697632
sdb              14.27      1002.00       575.90 5736075714 3296789720
sdb1              0.05         4.71         1.21   26965664    6918808
sdb2              0.02         2.21         0.02   12629986     115104
sdb3             14.20       995.08       574.67 5696479848 3289755808
md0               0.22         0.60         1.14    3457360    6523160
md1               0.00         0.00         0.02       9410     107584
md2              75.10       464.81       555.70 2660865738 3181185248
```

Memory shouldn't be an issue either:

```
             total       used       free     shared    buffers     cached
Mem:          7880       7793         87          0        246       3981
-/+ buffers/cache:       3564       4315
Swap:         4102       2062       2040
```

I have also a bunch of optimizations in sysctl.conf.

```
kernel.printk = 4 4 1 7
net.ipv4.icmp_echo_ignore_broadcasts = 1
net.ipv4.icmp_ignore_bogus_error_responses = 1
net.ipv4.conf.all.accept_redirects = 0
net.ipv6.conf.all.accept_redirects = 0
net.ipv4.conf.all.send_redirects = 0
net.ipv4.conf.all.accept_source_route = 0
net.ipv6.conf.all.accept_source_route = 0
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216
net.ipv4.tcp_rmem = 4096 87380 16777216
net.ipv4.tcp_wmem = 4096 65536 16777216
net.ipv4.tcp_congestion_control = cubic
net.ipv4.tcp_timestamps = 0
net.ipv4.tcp_rfc1337 = 1
net.ipv4.tcp_sack = 0
net.ipv4.tcp_window_scaling = 1
net.ipv4.route.flush = 1
net.ipv4.tcp_moderate_rcvbuf = 1
net.ipv4.tcp_no_metrics_save = 1
net.core.netdev_max_backlog = 2500
vm.swappiness=0
vm.vfs_cache_pressure=50
```

Iptraf shows this:

```
 IPTraf
&#9484; Statistics for eth0 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474;                                                                                                         &#9474;
&#9474;               Total      Total    Incoming   Incoming    Outgoing   Outgoing                            &#9474;
&#9474;             Packets      Bytes     Packets      Bytes     Packets      Bytes                            &#9474;
&#9474; Total:        22468    4447074       11163    1111908       11305    3335166                            &#9474;
&#9474; IP:           22468    4116580       11163     939684       11305    3176896                            &#9474;
&#9474; TCP:           8201    2967986        3235     397828        4966    2570158                            &#9474;
&#9474; UDP:          14257    1147238        7918     540500        6339     606738                            &#9474;
&#9474; ICMP:            10       1356          10       1356           0          0                            &#9474;
&#9474; Other IP:         0          0           0          0           0          0                            &#9474;
&#9474; Non-IP:           0          0           0          0           0          0                            &#9474;
&#9474;                                                                                                         &#9474;
&#9474;                                                                                                         &#9474;
&#9474; Total rates:       2496.1 kbits/sec        Broadcast packets:            0                              &#9474;
&#9474;                    1872.2 packets/sec      Broadcast bytes:              0                              &#9474;
&#9474;                                                                                                         &#9474;
&#9474; Incoming rates:     732.9 kbits/sec                                                                     &#9474;
&#9474;                     931.6 packets/sec                                                                   &#9474;
&#9474;                                            IP checksum errors:           0                              &#9474;
&#9474; Outgoing rates:    1763.2 kbits/sec                                                                     &#9474;
&#9474;                     940.6 packets/sec                                                                   &#9474;
```

netstat -s

```

Ip:
    1136541968 total packets received
    2875 with invalid addresses
    0 forwarded
    0 incoming packets discarded
    1136312461 incoming packets delivered
    1373982614 requests sent out
    184164 outgoing packets dropped
    1 dropped because of missing route
    39 fragments dropped after timeout
    257055 reassemblies required
    30426 packets reassembled ok
    613 packet reassembles failed
    13 fragments received ok
    26 fragments created
Icmp:
    2044482 ICMP messages received
    4436 input ICMP message failed.
    ICMP input histogram:
        destination unreachable: 1414029
        timeout in transit: 4143
        source quenches: 18
        redirects: 614609
        echo requests: 9575
        echo replies: 31
    552338 ICMP messages sent
    0 ICMP messages failed
    ICMP output histogram:
        destination unreachable: 542715
        time exceeded: 21
        echo request: 27
        echo replies: 9575
IcmpMsg:
        InType0: 31
        InType3: 1414029
        InType4: 18
        InType5: 614609
        InType8: 9575
        InType11: 4143
        OutType0: 9575
        OutType3: 542715
        OutType8: 27
        OutType11: 21
Tcp:
    158689 active connections openings
    2595182 passive connection openings
    11305 failed connection attempts
    148409 connection resets received
    105 connections established
    635023905 segments received
    893022294 segments send out
    3141278 segments retransmited
    4027 bad segments received.
    362393 resets sent
Udp:
    498459341 packets received
    608432 packets to unknown port received.
    173766 packet receive errors
    477262486 packets sent
    RcvbufErrors: 172717
    SndbufErrors: 179680
UdpLite:
TcpExt:
    56885 invalid SYN cookies received
    11089 resets received for embryonic SYN_RECV sockets
    11 packets pruned from receive queue because of socket buffer overrun
    32 ICMP packets dropped because they were out-of-window
    878698 TCP sockets finished time wait in fast timer
    630 time wait sockets recycled by time stamp
    1636 packets rejects in established connections because of timestamp
    21124894 delayed acks sent
    6868 delayed acks further delayed because of locked socket
    Quick ack mode was activated 128803 times
    3586105 packets directly queued to recvmsg prequeue.
    11463264 bytes directly in process context from backlog
    2469050645 bytes directly received in process context from prequeue
    156304483 packet headers predicted
    1144275 packets header predicted and directly queued to user
    274756173 acknowledgments not containing data payload received
    162258359 predicted acknowledgments
    19394 times recovered from packet loss due to fast retransmit
    886904 times recovered from packet loss by selective acknowledgements
    286 bad SACK blocks received
    Detected reordering 375 times using FACK
    Detected reordering 905 times using SACK
    Detected reordering 320 times using reno fast retransmit
    Detected reordering 136 times using time stamp
    311 congestion windows fully recovered without slow start
    834 congestion windows partially recovered using Hoe heuristic
    51287 congestion windows recovered without slow start by DSACK
    8459 congestion windows recovered without slow start after partial ack
    1228944 TCP data loss events
    TCPLostRetransmit: 36777
    3510 timeouts after reno fast retransmit
    185206 timeouts after SACK recovery
    15824 timeouts in loss state
    1835388 fast retransmits
    52271 forward retransmits
    326385 retransmits in slow start
    534071 other TCP timeouts
    6085 classic Reno fast retransmits failed
    40517 SACK retransmits failed
    1 times receiver scheduled too late for direct processing
    1046 packets collapsed in receive queue due to low socket buffer
    170554 DSACKs sent for old packets
    1038 DSACKs sent for out of order packets
    162631 DSACKs received
    1334 DSACKs for out of order packets received
    29205 connections reset due to unexpected data
    8129 connections reset due to early user close
    8178 connections aborted due to timeout
    TCPSACKDiscard: 133
    TCPDSACKIgnoredOld: 87456
    TCPDSACKIgnoredNoUndo: 30429
    TCPSpuriousRTOs: 4907
IpExt:
    InBcastPkts: 940

```

Ubuntu Server Edition 9.10 and out-of-the-box kernel Linux 2.6.28-15-server.

Another guy running Debian Lenny from same service provider has same kind of issues.

Maybe related to [this](https://bugs.launchpad.net/ubuntu/+bug/208012).

---

### Post by jiriki on 2010-10-18
I'm going to post a fix here. The issue was apparently the stock Ubuntu kernel missing R8168 network driver and using R8169 driver. My ISP had a nice article to set up the [R8168](http://wiki.hetzner.de/index.php/Installation_of_r8168_network_driver) driver manually. This fixed the issue.

---

