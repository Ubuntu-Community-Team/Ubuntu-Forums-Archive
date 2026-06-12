---
title: "Broadcom BCM4312 very slow wifi (another one abot this)"
date: 2023-10-14
forum: Ubuntu/Debian BASED
---

### Post by luispa on 2023-10-14
Hi,
Before posting this thread I did an intensive search (including the "Check If Already Posted" button) and tried to solve it using the solutions I found. But I had no luck. I'm trying to rescue an old Dell Studio 1555 and I'm using KDE Neon which is based on Ubuntu 22.04 LTS. I switched between wl and b43 drivers (blacklisting accordingly) and never was able to get more than 1Mb/s (measured with speedtest-cli) while ethernet connection is over 50Mb/s, another laptop with the same distro and an intel wifi device reaches easily 30Mb/s. I switched off the power management option as adviced in many posts but it had any impact.

```
sudo lspci | grep 4312
04:00.0 Network controller: Broadcom Inc. and subsidiaries BCM4312 802.11b/g LP-PHY (rev 01)

```

```
iwconfig
lo        no wireless extensions.

enp8s0    no wireless extensions.

wlan0     IEEE 802.11  ESSID:"lpgitsa2.4"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: F4:6B:EF:CC:70:EE   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

```
speedtest-cli
Retrieving speedtest.net configuration...
Testing from Personal (190.225.156.113)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by IXP CABASE - Servidor Nacional (Buenos Aires) [0.30 km]: 81.744 ms
Testing download speed................................................................................
Download: 0.64 Mbit/s
Testing upload speed......................................................................................................
Upload: 0.73 Mbit/s
```

Am I missing something? What can I do to get a decent wifi speed?

Thank you very much in advanced

---

### Post by jeremy31 on 2023-10-14
Moved to Ubuntu/Debian based

---

