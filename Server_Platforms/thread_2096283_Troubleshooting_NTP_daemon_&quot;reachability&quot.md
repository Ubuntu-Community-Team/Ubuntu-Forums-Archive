---
title: "Troubleshooting NTP daemon &quot;reachability&quot; with 12.04LTS"
date: 2012-12-19
forum: Server Platforms
---

### Post by cconstantine on 2012-12-19
I have a Dell R310 running Ubuntu 12.04LTS "Precise". The clock synchronization is very poor. Wobbling around 0 to ~100ms from the time sources.

I'm running two other Ubuntu 10.04LTS systems which sync to the same set of 4 time servers. All three systems are on the same IP subnet and have appropriate iptables rules to allow udp/123 traffic in/out. I'm working to retire one of the 10.04LTS time servers and replace it with this newer 12.04 system. These time servers provide time service to all our other internal systems. Here are the two systems which are sync'd nicely:

```
     remote refid st t when poll reach delay offset jitter
==============================================================================
+128.4.40.12 128.4.1.1 2 u 311 1024 377 13.852 -0.419 0.018
+128.118.25.3 147.84.59.145 2 u 37 1024 377 17.840 0.589 0.208
-128.2.136.71 69.65.40.29 3 u 238 1024 377 14.173 5.368 1.463
*208.90.144.52 172.23.7.201 2 u 542 1024 377 20.974 1.023 0.815

     remote refid st t when poll reach delay offset jitter
==============================================================================
+128.4.40.12 128.4.1.1 2 u 351 1024 377 31.752 -7.354 0.427
+128.118.25.3 147.84.59.145 2 u 212 1024 377 17.574 2.703 0.496
-128.2.136.71 69.65.40.29 3 u 190 1024 377 13.925 5.937 0.994
*208.90.144.52 172.23.7.201 2 u 537 1024 377 20.820 3.034 1.163
```

I note that both systems show a perfect 377 (octal version of binary 1111 1111) for their reachability registers.

Next here's the "ntpq -np" output from my 12.04LTS system showing poor reachibility across the board.

```
     remote refid st t when poll reach delay offset jitter
==============================================================================
+128.4.40.12 128.4.1.1 2 u 336 1024 17 31.504 371.879 313.883
+128.118.25.3 147.84.59.145 2 u 245 1024 17 17.370 269.816 212.188
+128.2.136.71 69.65.40.29 3 u 817 1024 37 14.219 210.001 161.045
*208.90.144.52 208.90.144.73 2 u 42 1024 37 20.901 292.619 228.770
```

also cross-posted on LaunchPad: [https://answers.launchpad.net/ubuntu/+source/ntp/+question/217123](https://answers.launchpad.net/ubuntu/+source/ntp/+question/217123)

---

