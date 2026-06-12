---
title: "NTP Issues"
date: 2016-09-08
forum: Server Platforms
---

### Post by hammons2012 on 2016-09-08
Good Afternoon,

Let me start out by saying I'm a noob at Linux as well as these forums. 

I'm currently trying to update my NTP servers from 14.04 to 16.04. When I did the upgrade, it caused all havoc, and my network devices that rely heavily on NTP sent massive amounts of alerts. Thusly, I created new NTP servers from scratch, using 16.04. I'm using NTP Tool to troubleshoot client connectivity to the server. On the existing 14.04, I get no drops at 100 packets a second. On the new 16.04, I get 97-98 drops at 100 packets a second. The servers have synced to their NTP sources (ntp.org pools). This has really got me stumped, and any help will be greatly appreciated.


My syslogs for NTP.

```

Sep  8 10:36:21 TVSNTP02 ntp[52825]:  * Starting NTP server ntpd
Sep  8 10:36:21 TVSNTP02 ntpd[52835]: ntpd 4.2.8p4@1.3265-o Tue Aug  2 08:19:53 UTC 2016 (1): Starting
Sep  8 10:36:21 TVSNTP02 ntpd[52835]: Command line: /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 111:117
Sep  8 10:36:21 TVSNTP02 ntpd[52837]: proto: precision = 0.200 usec (-22)
Sep  8 10:36:21 TVSNTP02 ntpd[52837]: Listen and drop on 0 v6wildcard [::]:123
Sep  8 10:36:21 TVSNTP02 ntpd[52837]: Listen and drop on 1 v4wildcard 0.0.0.0:123
Sep  8 10:36:21 TVSNTP02 ntpd[52837]: Listen normally on 2 lo 127.0.0.1:123
Sep  8 10:36:21 TVSNTP02 ntpd[52837]: Listen normally on 3 eth0 x.x.x.x:123
Sep  8 10:36:21 TVSNTP02 ntpd[52837]: Listen normally on 4 lo [::1]:123
Sep  8 10:36:21 TVSNTP02 ntpd[52837]: Listen normally on 5 eth0 [fe80::215:5dff:fe01:ca15%2]:123
Sep  8 10:36:21 TVSNTP02 ntpd[52837]: Listening on routing socket on fd #22 for interface updates
Sep  8 10:36:22 TVSNTP02 kernel: [  391.193138] audit: type=1400 audit(1473345382.090:46): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=52851 comm="apparmor_parser"
Sep  8 10:36:22 TVSNTP02 ntpd[52837]: Soliciting pool server 198.55.111.5
Sep  8 10:36:23 TVSNTP02 ntpd[52837]: Soliciting pool server 104.155.144.4
Sep  8 10:36:23 TVSNTP02 ntpd[52837]: Soliciting pool server 96.244.96.19
Sep  8 10:36:24 TVSNTP02 ntpd[52837]: Soliciting pool server 104.156.99.226
Sep  8 10:36:24 TVSNTP02 ntpd[52837]: Soliciting pool server 23.239.26.89
Sep  8 10:36:25 TVSNTP02 ntpd[52837]: Soliciting pool server 198.58.105.63
Sep  8 10:36:25 TVSNTP02 ntpd[52837]: Soliciting pool server 97.107.128.58
Sep  8 10:36:25 TVSNTP02 ntpd[52837]: Soliciting pool server 52.0.56.137
Sep  8 10:36:25 TVSNTP02 ntpd[52837]: Soliciting pool server 198.211.106.151
Sep  8 10:36:25 TVSNTP02 ntpd[52837]: Soliciting pool server 206.209.110.2
Sep  8 10:37:23 TVSNTP02 ntp[2467]:  * Starting NTP server ntpd
Sep  8 10:37:24 TVSNTP02 ntpd[2515]: ntpd 4.2.8p4@1.3265-o Tue Aug  2 08:19:53 UTC 2016 (1): Starting
Sep  8 10:37:24 TVSNTP02 ntpd[2515]: Command line: /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 111:117
Sep  8 10:37:24 TVSNTP02 ntpd[2535]: proto: precision = 0.200 usec (-22)
Sep  8 10:37:24 TVSNTP02 ntpd[2535]: Listen and drop on 0 v6wildcard [::]:123
Sep  8 10:37:24 TVSNTP02 ntpd[2535]: Listen and drop on 1 v4wildcard 0.0.0.0:123
Sep  8 10:37:24 TVSNTP02 ntpd[2535]: Listen normally on 2 lo 127.0.0.1:123
Sep  8 10:37:24 TVSNTP02 ntpd[2535]: Listen normally on 3 eth0 x.x.x.x:123
Sep  8 10:37:24 TVSNTP02 ntpd[2535]: Listen normally on 4 lo [::1]:123
Sep  8 10:37:24 TVSNTP02 ntpd[2535]: bind(21) AF_INET6 fe80::215:5dff:fe01:ca15%2#123 flags 0x11 failed: Cannot assign requested address
Sep  8 10:37:24 TVSNTP02 ntpd[2535]: unable to create socket on eth0 (5) for fe80::215:5dff:fe01:ca15%2#123
Sep  8 10:37:24 TVSNTP02 ntpd[2535]: failed to init interface for address fe80::215:5dff:fe01:ca15%2
Sep  8 10:37:24 TVSNTP02 ntpd[2535]: Listening on routing socket on fd #21 for interface updates
Sep  8 10:37:25 TVSNTP02 ntpd[2535]: Soliciting pool server 104.155.144.4
Sep  8 10:37:26 TVSNTP02 ntpd[2535]: Listen normally on 6 eth0 [fe80::215:5dff:fe01:ca15%2]:123
Sep  8 10:37:26 TVSNTP02 ntpd[2535]: new interface(s) found: waking up resolver
Sep  8 10:42:53 TVSNTP02 ntpd[2535]: kernel reports TIME_ERROR: 0x41: Clock Unsynchronized
Sep  8 10:43:28 TVSNTP02 ntp[2988]:  * Stopping NTP server ntpd
Sep  8 10:43:28 TVSNTP02 ntpd[2535]: ntpd exiting on signal 15 (Terminated)
Sep  8 10:43:28 TVSNTP02 ntpd[2535]: 159.203.158.197 local addr x.x.x.x -> <null>
Sep  8 10:43:28 TVSNTP02 ntpd[2535]: 129.6.15.28 local addr x.x.x.x -> <null>
Sep  8 10:43:28 TVSNTP02 ntpd[2535]: 97.107.128.58 local addr x.x.x.x -> <null>
Sep  8 10:43:28 TVSNTP02 ntpd[2535]: 137.190.2.4 local addr x.x.x.x -> <null>
Sep  8 10:43:28 TVSNTP02 ntpd[2535]: 206.108.0.133 local addr x.x.x.x -> <null>
Sep  8 10:43:28 TVSNTP02 ntpd[2535]: 204.2.134.164 local addr x.x.x.x -> <null>
Sep  8 10:43:28 TVSNTP02 ntpd[2535]: 216.229.4.66 local addr x.x.x.x -> <null>
Sep  8 10:43:28 TVSNTP02 ntpd[2535]: 216.229.0.49 local addr x.x.x.x -> <null>
Sep  8 10:43:28 TVSNTP02 ntpd[2535]: 104.155.144.4 local addr x.x.x.x -> <null>
Sep  8 10:43:28 TVSNTP02 ntp[3002]:  * Starting NTP server ntpd
Sep  8 10:43:28 TVSNTP02 ntpd[3012]: ntpd 4.2.8p4@1.3265-o Tue Aug  2 08:19:53 UTC 2016 (1): Starting
Sep  8 10:43:28 TVSNTP02 ntpd[3012]: Command line: /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 111:117
Sep  8 10:43:28 TVSNTP02 ntpd[3014]: proto: precision = 0.200 usec (-22)
Sep  8 10:43:28 TVSNTP02 ntpd[3014]: Listen and drop on 0 v6wildcard [::]:123
Sep  8 10:43:28 TVSNTP02 ntpd[3014]: Listen and drop on 1 v4wildcard 0.0.0.0:123
Sep  8 10:43:28 TVSNTP02 ntpd[3014]: Listen normally on 2 lo 127.0.0.1:123
Sep  8 10:43:28 TVSNTP02 ntpd[3014]: Listen normally on 3 eth0 x.x.x.x:123
Sep  8 10:43:28 TVSNTP02 ntpd[3014]: Listen normally on 4 lo [::1]:123
Sep  8 10:43:28 TVSNTP02 ntpd[3014]: Listen normally on 5 eth0 [fe80::215:5dff:fe01:ca15%2]:123
Sep  8 10:43:28 TVSNTP02 ntpd[3014]: Listening on routing socket on fd #22 for interface updates
Sep  8 10:43:29 TVSNTP02 ntpd[3014]: Soliciting pool server 199.233.236.226
Sep  8 10:43:30 TVSNTP02 ntpd[3014]: Soliciting pool server 204.2.134.164
Sep  8 10:43:30 TVSNTP02 ntpd[3014]: Soliciting pool server 104.155.144.4
Sep  8 10:43:31 TVSNTP02 ntpd[3014]: Soliciting pool server 167.88.117.204
Sep  8 10:43:31 TVSNTP02 ntpd[3014]: Soliciting pool server 198.23.200.19
Sep  8 10:43:31 TVSNTP02 ntpd[3014]: Soliciting pool server 96.126.105.86
Sep  8 10:43:32 TVSNTP02 ntpd[3014]: Soliciting pool server 107.170.224.8
Sep  8 10:43:32 TVSNTP02 ntpd[3014]: Soliciting pool server 198.100.156.225
Sep  8 10:43:32 TVSNTP02 ntpd[3014]: Soliciting pool server 74.120.8.2
Sep  8 10:43:33 TVSNTP02 ntpd[3014]: Soliciting pool server 96.244.96.19
Sep  8 10:43:33 TVSNTP02 ntpd[3014]: Soliciting pool server 208.53.158.34
Sep  8 10:43:33 TVSNTP02 ntpd[3014]: Soliciting pool server 38.113.126.207
Sep  8 10:43:33 TVSNTP02 ntpd[3014]: Soliciting pool server 91.189.89.199
Sep  8 10:51:15 TVSNTP02 ntp[2491]:  * Starting NTP server ntpd
Sep  8 10:51:15 TVSNTP02 ntpd[2544]: ntpd 4.2.8p4@1.3265-o Tue Aug  2 08:19:53 UTC 2016 (1): Starting
Sep  8 10:51:15 TVSNTP02 ntpd[2544]: Command line: /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 111:117
Sep  8 10:51:15 TVSNTP02 ntpd[2549]: proto: precision = 0.200 usec (-22)
Sep  8 10:51:15 TVSNTP02 ntpd[2549]: Listen and drop on 0 v6wildcard [::]:123
Sep  8 10:51:15 TVSNTP02 ntpd[2549]: Listen and drop on 1 v4wildcard 0.0.0.0:123
Sep  8 10:51:15 TVSNTP02 ntpd[2549]: Listen normally on 2 lo 127.0.0.1:123
Sep  8 10:51:15 TVSNTP02 ntpd[2549]: Listen normally on 3 eth0 x.x.x.x:123
Sep  8 10:51:15 TVSNTP02 ntpd[2549]: Listen normally on 4 lo [::1]:123
Sep  8 10:51:15 TVSNTP02 ntpd[2549]: Listen normally on 5 eth0 [fe80::215:5dff:fe01:ca15%2]:123
Sep  8 10:51:15 TVSNTP02 ntpd[2549]: Listening on routing socket on fd #22 for interface updates
Sep  8 10:51:16 TVSNTP02 ntpd[2549]: Soliciting pool server 104.156.99.226
Sep  8 10:51:17 TVSNTP02 ntpd[2549]: Soliciting pool server 198.211.106.151
Sep  8 10:51:17 TVSNTP02 ntpd[2549]: Soliciting pool server 69.41.163.31
Sep  8 10:51:18 TVSNTP02 ntpd[2549]: Soliciting pool server 104.155.144.4
Sep  8 10:51:18 TVSNTP02 ntpd[2549]: Soliciting pool server 209.208.79.69
Sep  8 10:51:18 TVSNTP02 ntpd[2549]: Soliciting pool server 23.239.26.89
Sep  8 10:51:19 TVSNTP02 ntpd[2549]: Soliciting pool server 204.11.201.12
Sep  8 10:51:19 TVSNTP02 ntpd[2549]: Soliciting pool server 198.100.156.225
Sep  8 10:51:19 TVSNTP02 ntpd[2549]: Soliciting pool server 73.37.183.90
Sep  8 10:51:19 TVSNTP02 ntpd[2549]: Soliciting pool server 4.53.160.75
Sep  8 10:51:20 TVSNTP02 ntpd[2549]: Soliciting pool server 66.228.59.187
Sep  8 10:51:20 TVSNTP02 ntpd[2549]: Soliciting pool server 198.60.22.240
Sep  8 10:51:20 TVSNTP02 ntpd[2549]: Soliciting pool server 108.61.194.85
Sep  8 10:51:20 TVSNTP02 ntpd[2549]: Soliciting pool server 91.189.89.198
Sep  8 10:56:48 TVSNTP02 ntpd[2549]: kernel reports TIME_ERROR: 0x41: Clock Unsynchronized
Sep  8 11:33:07 TVSNTP02 ntp[4014]:  * Stopping NTP server ntpd
Sep  8 11:33:07 TVSNTP02 ntpd[2549]: ntpd exiting on signal 15 (Terminated)
Sep  8 11:33:07 TVSNTP02 ntpd[2549]: 104.156.99.226 local addr x.x.x.x -> <null>
Sep  8 11:33:07 TVSNTP02 ntpd[2549]: 198.211.106.151 local addr x.x.x.x -> <null>
Sep  8 11:33:07 TVSNTP02 ntpd[2549]: 69.41.163.31 local addr x.x.x.x -> <null>
Sep  8 11:33:07 TVSNTP02 ntpd[2549]: 104.155.144.4 local addr x.x.x.x -> <null>
Sep  8 11:33:07 TVSNTP02 ntpd[2549]: 209.208.79.69 local addr x.x.x.x -> <null>
Sep  8 11:33:07 TVSNTP02 ntpd[2549]: 23.239.26.89 local addr 172.25.1.114 -> <null>
Sep  8 11:33:07 TVSNTP02 ntpd[2549]: 198.100.156.225 local addr x.x.x.x -> <null>
Sep  8 11:33:07 TVSNTP02 ntpd[2549]: 73.37.183.90 local addr x.x.x.x -> <null>
Sep  8 11:33:07 TVSNTP02 ntpd[2549]: 4.53.160.75 local addr x.x.x.x -> <null>
Sep  8 11:33:07 TVSNTP02 ntpd[2549]: 204.11.201.12 local addr x.x.x.x -> <null>
Sep  8 11:33:07 TVSNTP02 ntpd[2549]: 66.228.59.187 local addr x.x.x.x -> <null>
Sep  8 11:33:07 TVSNTP02 ntpd[2549]: 198.60.22.240 local addr x.x.x.x -> <null>
Sep  8 11:33:07 TVSNTP02 ntpd[2549]: 108.61.194.85 local addr x.x.x.x -> <null>
Sep  8 11:33:07 TVSNTP02 ntpd[2549]: 91.189.89.198 local addr x.x.x.x -> <null>
Sep  8 11:33:07 TVSNTP02 ntp[4027]:  * Starting NTP server ntpd
Sep  8 11:33:07 TVSNTP02 ntpd[4039]: ntpd 4.2.8p4@1.3265-o Tue Aug  2 08:19:53 UTC 2016 (1): Starting
Sep  8 11:33:07 TVSNTP02 ntpd[4039]: Command line: /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 111:117
Sep  8 11:33:07 TVSNTP02 ntpd[4041]: proto: precision = 0.200 usec (-22)
Sep  8 11:33:07 TVSNTP02 ntpd[4041]: Listen and drop on 0 v6wildcard [::]:123
Sep  8 11:33:07 TVSNTP02 ntpd[4041]: Listen and drop on 1 v4wildcard 0.0.0.0:123
Sep  8 11:33:07 TVSNTP02 ntpd[4041]: Listen normally on 2 lo 127.0.0.1:123
Sep  8 11:33:07 TVSNTP02 ntpd[4041]: Listen normally on 3 eth0 x.x.x.x:123
Sep  8 11:33:07 TVSNTP02 ntpd[4041]: Listen normally on 4 lo [::1]:123
Sep  8 11:33:07 TVSNTP02 ntpd[4041]: Listen normally on 5 eth0 [fe80::215:5dff:fe01:ca15%2]:123
Sep  8 11:33:07 TVSNTP02 ntpd[4041]: Listening on routing socket on fd #22 for interface updates
Sep  8 11:33:14 TVSNTP02 ntpd[4041]: Soliciting pool server 91.189.89.198
Sep  8 11:33:15 TVSNTP02 ntpd[4041]: Soliciting pool server 91.189.94.4
Sep  8 11:33:16 TVSNTP02 ntpd[4041]: Soliciting pool server 91.189.91.157
Sep  8 11:36:50 TVSNTP02 ntp[4123]:  * Stopping NTP server ntpd
Sep  8 11:36:50 TVSNTP02 ntpd[4041]: ntpd exiting on signal 15 (Terminated)
Sep  8 11:36:50 TVSNTP02 ntpd[4041]: 173.208.177.234 local addr x.x.x.x -> <null>
Sep  8 11:36:50 TVSNTP02 ntpd[4041]: 132.163.4.102 local addr x.x.x.x -> <null>
Sep  8 11:36:50 TVSNTP02 ntpd[4041]: 66.241.101.63 local addr x.x.x.x -> <null>
Sep  8 11:36:50 TVSNTP02 ntpd[4041]: 67.18.187.111 local addr x.x.x.x -> <null>
Sep  8 11:36:50 TVSNTP02 ntpd[4041]: 108.59.2.24 local addr x.x.x.x -> <null>
Sep  8 11:36:50 TVSNTP02 ntpd[4041]: 50.22.155.163 local addr x.x.x.x -> <null>
Sep  8 11:36:50 TVSNTP02 ntpd[4041]: 64.6.144.6 local addr x.x.x.x -> <null>
Sep  8 11:36:50 TVSNTP02 ntpd[4041]: 104.131.118.129 local addr x.x.x.x -> <null>
Sep  8 11:36:50 TVSNTP02 ntpd[4041]: 91.189.89.198 local addr x.x.x.x -> <null>
Sep  8 11:36:50 TVSNTP02 ntpd[4041]: 91.189.94.4 local addr x.x.x.x -> <null>
Sep  8 11:36:50 TVSNTP02 ntpd[4041]: 91.189.91.157 local addr x.x.x.x -> <null>
Sep  8 11:36:50 TVSNTP02 ntp[4135]:  * Starting NTP server ntpd
Sep  8 11:36:50 TVSNTP02 ntpd[4148]: ntpd 4.2.8p4@1.3265-o Tue Aug  2 08:19:53 UTC 2016 (1): Starting
Sep  8 11:36:50 TVSNTP02 ntpd[4148]: Command line: /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 111:117
Sep  8 11:36:50 TVSNTP02 ntpd[4150]: proto: precision = 0.200 usec (-22)
Sep  8 11:36:50 TVSNTP02 ntpd[4150]: Listen and drop on 0 v6wildcard [::]:123
Sep  8 11:36:50 TVSNTP02 ntpd[4150]: Listen and drop on 1 v4wildcard 0.0.0.0:123
Sep  8 11:36:50 TVSNTP02 ntpd[4150]: Listen normally on 2 lo 127.0.0.1:123
Sep  8 11:36:50 TVSNTP02 ntpd[4150]: Listen normally on 3 eth0 x.x.x.x:123
Sep  8 11:36:50 TVSNTP02 ntpd[4150]: Listen normally on 4 lo [::1]:123
Sep  8 11:36:50 TVSNTP02 ntpd[4150]: Listen normally on 5 eth0 [fe80::215:5dff:fe01:ca15%2]:123
Sep  8 11:36:50 TVSNTP02 ntpd[4150]: Listening on routing socket on fd #22 for interface updates

```

The ntp.conf is mostly default, I commented out the Ubuntu servers and added the ntp.org pools (note below).

```

# Servers from pool.ntp.org website.
server 0.us.pool.ntp.org iburst
server 1.us.pool.ntp.org
server 2.us.pool.ntp.org
server 3.us.pool.ntp.org
server 0.north-america.pool.ntp.org
server 1.north-america.pool.ntp.org
server 2.north-america.pool.ntp.org
server 3.north-america.pool.ntp.org

```

Here is the sync status of the servers.

```

 sudo ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
-x.ns.gin.ntt.ne 249.224.99.213   2 u   81  128  377   45.897  -26.351   0.801
-108.38.172.2 (s 192.168.0.6      3 u   61  128  377   74.101  -17.260   0.916
-104.156.99.226  204.123.2.72     2 u   86  128  377   62.191  -13.834   0.785
+cheezum.mattnor 129.7.1.66       2 u  152  128  376   39.771  -14.626   1.153
-a1.pcloud.com   128.4.1.1        2 u   66  128  377   43.574  -13.828   1.138
+linode.appus.or 127.67.113.92    2 u   14  128  377   75.499  -14.748   1.024
-ntp2.torix.ca   192.168.100.252  2 u   73  128  377   45.439  -21.991   0.875
*208.94.243.142  132.163.4.101    2 u   78  128  377   37.853  -14.404   1.959

```

---

### Post by cariboo on 2016-09-08
closed double post.

---

