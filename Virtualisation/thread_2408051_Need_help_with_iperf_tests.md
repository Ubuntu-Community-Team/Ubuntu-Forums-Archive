---
title: "Need help with iperf tests"
date: 2018-12-13
forum: Virtualisation
---

### Post by pavuluri-kanthi-w on 2018-12-13
I am running performance tests using iperf on virtual machines  created using vagrant. One of my VMs acts as tcpclient where  iperf client runs and the other one acts as tcp server where my iperf  server runs

  They are run using the following commands: 

iperf3 -c 192.168.3.11  -t 1 -b 1G  -> client

  iperf3 -s -I 1  -> server

  
I have disabled checksum offloading on both the VMs

  If I send traffic at low rates, things seems to be fine. But if I  increase the traffic rate(500mbps/1gbps), iperf sends packets large sizes ie., beyond the MTU of the ethernet interface.
And when this happens, tcpdumps shows these packets with incorrect checksum

Shouldn't iperf/tcp automatically detect the MTU and adjust the segment sizes accordingly?

 
I even tried setting the segment size using --set-mss / packet length  using -l options of iperf client. But none of these seems to work.
Can you please help point the issue?


Thanks!

---

### Post by slickymaster on 2018-12-13
Thread moved to **Virtualisation** for a better fit

---

