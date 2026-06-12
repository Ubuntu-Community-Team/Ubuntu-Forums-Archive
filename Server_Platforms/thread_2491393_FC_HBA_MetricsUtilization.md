---
title: "FC HBA Metrics/Utilization"
date: 2023-10-06
forum: Server Platforms
---

### Post by hxman on 2023-10-06
Hello,

I was wondering if anyone running 22.04 has a tool to monitor the performance and utilization of your FC HBA adapter ports? We are currently running FC attached storage using multipathd.

Thanks

---

### Post by MAFoElffen on 2023-10-07
Storage stats and benchmarks:
 
Probably like most here, I have to write my own scripts to scrape data for stats from iostat, iotop, llscsi, multipath, sar, the sysfs files at  /sys/class/fc_host/host*/ (port_name, node_name, speed, port_state, port_type, statistics), and lspci to create reports. 

I get benchmarks from fio, iozone, and  vdbench to verify the performance and bandwidth.

---

