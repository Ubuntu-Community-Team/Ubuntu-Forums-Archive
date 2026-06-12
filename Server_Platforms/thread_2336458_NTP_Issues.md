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

### Post by TheFu on 2016-09-08
Really sounds like a WAN connection issue, not specific to NTP.

BTW, more than 3 external servers is a waste, IMHO. If low msec correct time is that important, use a GPS device as source. Those numbers are huge!  Use a local server and sync off it. That way, only 1 machine will be bouncing around and sending packets externally.
```
$ ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*romulus         4.53.160.75      3 u   60 1024  377    0.326   -0.027   0.024

```
Oh ... no need to sudo it. Over use of sudo can get you into trouble.

Where is the driftfile specified?
Do you restrict access to only the LAN systems?

I have 1 system that goes externally to get time from 3 pool servers (small network here). This box is the only time server for all the systems internally. They all point at it, including a few Windows systems.  Just add the **restrict** and **broadcast** options to make an NTP server.  Generally, perfectly accurate time really isn't that important, so anything within a few minutes is close enough. Systems on the same network just need to closely have the same time.  I've never seen any Unix machine off more than about 0.5 sec ... though Windows systems seem to drift wildly for some reason.  Too keep Windows times accurate, I had to force time checking every 15 minutes - anything longer than that, even 60 min, and the clock would be off 5+ minutes. Over a week, and it would be off almost an hour.  The exact same system running Linux never has any time issues, so it is definitely a Windows problem.  Plus this has happened to my Windows machines since the mid-90s. They just don't keep time for some reason.  

I agree with using non-Ubuntu time servers, though suspect they just point to the normal NTP pools.  NTP is a good way for a distro to track running systems and the DNS redirect ... well ... those can be scary from a security standpoint.

---

### Post by hammons2012 on 2016-09-08
TheFu,


I wish I could say it's the WAN, but I'm testing internally and the company I am doing this for is an ISP..... 


Thanks for the note on "sudo", I get into the habit of sudoing everything, and I'm not about to open the root account. It's a love/hate thing. 


The drift file is the default location: /var/lib/ntp/ntp.drift. Driftfile output is 22.816.


I have not restricted access to any subnets that will be using it, yet. What I can't understand, is that how is the 14.04 server allowing all these connections without issue, yet 16.04 will only answer the first 2-3 and drop the rest. I even disabled apparmor to see if that was the issue, but nope. Likewise with the firewall, it's disabled. I assure you, minus the updates I listed in the original posts, both servers have the same ntp.conf setup.


We are running Calix devices that rely heavily on the NTP servers, and when I updated them a few weeks ago, they broke due to this. I personally don't have experience with Calix stuff, but from what I could tell, it's crazy. I could tell them to test use the Windows Server 2012 R2 hosts as the NTP servers (I forgot to mention, we are running the servers via Hyper-V). I'm half way tempted to just leave them on 14.04 for now. It's just crazy that I can't upgrade the server from 14.04 to 16.04 and have NTP not allow these devices to query for NTP.

---

### Post by TheFu on 2016-09-08
VMs change everything with keeping time. There are usually guest additions that passthru the physical host's time to all clients.  But I don't know **anything**, zero, nada, nichts about hyper-v.  IME, Windows can't keep time, so I'd never have it in my infrastructure where that was important.

Test if this is an issue on a physical 16.04 machine.  I only have 1 16.04 install (zero servers and only a play chromebook) and it doesn't show any time issues.
BTW - it appears that NTP changed between 16.04 and 14.04. Check the release notes. The "server" entry isn't what is being used anymore. There is a "pool" entry now in the default configs that I don't recall previously.  We use ansible to maintain ntp.conf files across all the systems, so checking any others for differences won't be any help. 

A guess (and it is only that) is to look for hyper-v updates related to the 16.04 release.

Interesting and frustrating problem. At an ISP, time is critical, since you should provide that as a service to the clients.  Setup 3 time servers internally and get 3 GPS-based time devices for those to sync.  Then point all the others at those 3 machines.  Did this a few decades ago on a network that wasn't connected to the internet. Bet it is cheaper and easier now. ;)  I wouldn't use any internet-based time pools at all.

---

### Post by hammons2012 on 2016-09-08
TheFu,

I have an old E-Machine laying around that I might be able to put Ubuntu on to test at home. If not, maybe I can get my Raspberry Pi to run the ARM version of 16.04. Or, I can turn my laptop into a NTP server (running desktop 16.04). I'll test and report when I can get this setup. I should be good on the NTP server side though, I can see that I am connected to a Stratum 2 NTP server, which isn't too shabby. There is no way that they will purchase an atomic clock, though it would be cool if they did.

---

### Post by TheFu on 2016-09-08
$35 for a GPS bluetooth device doesn't seem that expensive. That level of time accuracy should be plenty for everyone except crypto operators.
IMHO.
[https://blog.logentries.com/2015/07/adding-a-gps-time-source-to-ntpd/](https://blog.logentries.com/2015/07/adding-a-gps-time-source-to-ntpd/)

I have an old BT GPS receiver that needs to be repurposed for this use myself. Gotta keep learning.

---

### Post by hammons2012 on 2016-09-08
TheFU,

That looks neat, but the issue isn't getting Ubuntu to sync with an NTP server. The issue is getting other devices to connect to the Ubuntu server with NTP. However, I've always wanted to get a Raspberry Pi, a breadboard, and a GPS module to create an atomic clock.......

---

### Post by TheFu on 2016-09-08
I'm fairly certain that virtual-PC is the issue (or whatever they call it now).
Any luck changing the server to pool in the config files?

---

### Post by darkod on 2016-09-08
In case you are using iptables filtering on the ntp servers, did you double check them after the upgrade? In 16.04 the naming of the interfaces is changed so that might affect any services that are strictly linked to interface names. Maybe this was the issue?

---

### Post by hammons2012 on 2016-09-08
TheFu,

I did change them, but I wasn't any closer to getting the clients to connect.

Darkod,

In reference to the iptables, the current server, I'm unsure of (I would bet it's not running, we use a Cisco ASA and just NAT the NTP server to an external IP). As for the new server, the one giving me the troubles, iptables is turned off (along with ufw).

Right now, I'm updating my Ubuntu desktop laptop (as I type!!!) to set as a NTP server to see if using a physical box makes a difference.

UPDATE: I just got done testing, and it's the same story. I'm going to revisit the firewall in the AM, just to make sure that it's fully disabled. Also, I'll create a 14.04 virtual machine to see if it does the same thing without configuring.

---

### Post by hammons2012 on 2016-09-09
Ok, so, I just got done creating an Ubuntu 14.04 server, patched it up, and installed NTP. I get no drops. This has got to be something going on specifically for 16.04........

---

### Post by darkod on 2016-09-09
Did you tried fresh install of 16.04 as opposed to an upgraded one? In that same test machine instead of 14.04 try 16.04 now. NTP is such a basic function, I doubt there is much difference between 14 and 16.

How does it perform on a clean 16.04 install?

---

### Post by hammons2012 on 2016-09-09
darkod,

I did build new NTP servers after the upgrade. Note my experience below:

1.) Updated the current 14.04 servers to 16.04, which caused the initial issues (clients couldn't poll these servers anymore for NTP info).
2.) I built fresh 16.04 servers, and still had issues with getting the NTP Tool app to connect to it (would stop connections after 2-3 successful packets).
3.) I then built fresh 14.04 servers, only updated/patches and installed NTP, and it works just fine (allows all connections).
4.) Iptables/ufw is disabled on the current and new servers, as well as apparmor on one of the the new servers (I thought I read somewhere that apparmor can wreak havoc on some systems), which didn't do anything.

I can't think of any other default applications that are installed in 16 that aren't in 14.

---

### Post by TheFu on 2016-09-09
I'm puling a 16.04.1 server ISO now.  Will install a base system [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server) with NTP server and connect a few clients.
This will be installed inside a KVM VM on a 14.04.5 VM host (assuming that works).

Need about 45 min. ISO just finished.

---

### Post by hammons2012 on 2016-09-09
TheFu,

Please tell me I am going crazy. This is the tool that I am using:

[http://www.ntp-time-server.com/ntp-server-tool.html](http://www.ntp-time-server.com/ntp-server-tool.html)

---

### Post by TheFu on 2016-09-09
Don't know anything about that tool. Don't use Windows enough that it matters. Only have Windows for video stuff (editing/recording) and taxes.

Ok - it is setup as a server with all the defaults. No "guest additions" added. It is a pure server with minimal other stuff. Love the new installer - 1.3G used, plus virt-manager defaults to qcow2 storage and QXL video (that actually works!). Very nice.

 ```

$ ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 0.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000
 1.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000
 2.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000
 3.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000
 ntp.ubuntu.com  .POOL.          16 p    -   64    0    0.000    0.000   0.000
*jtsage.com      216.218.254.202  2 u   18   64   17   43.371    0.462   2.956
+y.ns.gin.ntt.ne 249.224.99.213   2 u   17   64   17   23.188    0.618   3.706
-freemont.nerdbo 127.67.113.92    2 u   18   64   17   93.229   -6.950   7.148
-ha2.smatwebdesi 130.207.244.240  2 u   15   64   17   44.120   -5.318   7.370
+linode227395.st 192.5.41.209     2 u   19   64   17   43.006    0.159   6.545
-clock.trit.net  134.121.64.62    2 u   19   64   17   73.200    2.713   2.947
-jarvis.arlen.io 209.51.161.238   2 u   17   64   17   43.137   -2.873   6.948
-lithium.constan 18.26.4.105      2 u   16   64   17   54.008   -6.986   2.504
-208.94.243.142  132.163.4.101    2 u   19   64   17   53.233    7.082   4.294
+clock.team-cymr 204.9.54.119     2 u   19   64   17   34.439   -0.001   1.911
```

Have pointed 1 client machine (physical), at it.  Will need a few hours for things to quiet down. On the client side ...
```
$ ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*dhcp247         208.75.88.4      3 u   60   64    7    0.896    0.923   0.713

``` things look a little off. That should get better, slowly. There will always be issues - it is a VM after all.
[https://serverfault.com/questions/106501/what-are-the-limits-of-running-ntp-servers-in-virtual-machines](https://serverfault.com/questions/106501/what-are-the-limits-of-running-ntp-servers-in-virtual-machines)

---

### Post by hammons2012 on 2016-09-09
TheFu,

I dare say that we don't mind the gap as much as much as we mind that these devices can't poll (if that makes sense). My best guess is that these clients would eventually take, it will just take like 10 years. I may setup a NTP server in CentOS or some other flavor to see if I get the same results. I'll even try to see if this is the issue with the other NTP server (Ubuntu 16.04) I setup for another customer. I just agree that this is a weird issue for such a simple process.

Oh, also, I added the server's to each other's ntp.conf files, and they do sync with each other (stratum 2). So that's good, I guess.

```

ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
-172.25.1.111 (a 132.163.4.101    2 u  225 1024  377    0.156    0.257   0.724      <---- Current NTP
+172.25.1.112    152.2.133.55     2 u  432 1024  377    0.377   -0.782   1.129      <---- Current NTP
 TVSNTP01.tvscab .INIT.          16 u    - 1024    0    0.000    0.000   0.000           <---- New NTP (Server I pulled the info from...... I know, I know. I'll eventually remove it)
*172.25.1.114    132.163.4.102    2 u    9 1024  377    0.371   -1.280   2.286       <---- New NTP
-biisoni.miuku.n 129.250.35.251   3 u  420 1024  377   70.379   -2.498   0.635
-clockb.ntpjs.or 20.162.227.208   2 u  968 1024  173   17.938    0.094   6.970
-107.170.224.8 ( 132.163.4.102    2 u  351 1024  151   76.555    4.776   1.272
-lithium.constan 18.26.4.105      2 u  955 1024  337   42.255    1.584   1.690
+time.tritn.com  66.220.9.122     2 u 1420 1024  376   66.565   -2.464   1.737
-static-71-175-6 69.164.203.231   3 u 1053 1024  367   51.844    1.227   5.931
-zero.gotroot.ca 30.114.5.31      2 u  983 1024  377   67.975    1.297   2.020
#ntp.newfxlabs.c 69.75.229.42     2 u  438 1024  377   78.036   -9.066   2.210

```

---

### Post by TheFu on 2016-09-09
Physical 14.04 server as NTP server :
```
$ ntpq -p 
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*4.53.160.75     64.113.32.5      2 u  487 1024  377   60.952   -0.079   2.039
+golem.canonical 145.238.203.14   2 u  737 1024  377  109.584    5.770  10.591
 172.22.22.255   .BCST.          16 u    -   64    0    0.000    0.000   0.000
```

16.04.1 VM as NTP server```

$ ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
-sola-dal-09.ser 10.0.77.54       5 u  407  512  377   41.279    0.312   5.550
-romulus         4.53.160.75      3 u  311  512  377    0.196   -4.612   0.655
 0.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000
 1.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000
 2.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000
 3.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000
 ntp.ubuntu.com  .POOL.          16 p    -   64    0    0.000    0.000   0.000
+host39.0dd0.net 51.117.5.38      3 u  405  512  377   36.043   -0.727   3.315
*66.96.98.9 (66- 142.66.101.13    2 u  490  512  377   55.467    1.821   6.089
+ntp.wdc1.us.lea 209.51.161.238   2 u  344  512  377   37.093   -0.246  10.227
```

Physical 16.04 client using 16.04.1 ntpd:
```
$ ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*dhcp247         66.96.98.9       3 u  452  512  377    0.661    0.905   6.115

```

Not seeing any issues here.  Gonna wipe the VM tonight unless there's something you'd like me to try.

---

### Post by hammons2012 on 2016-09-09
TheFu,

Nope, I don't believe so. Attached (hopefully) are the outputs from the NTP Tool. NTP1 is the 14.04 server that is successful, and NTP3 is the 16.04 server that isn't. I hope seeing these make better sense.

---

### Post by TheFu on 2016-09-09
Perhaps they compiled with defaults that prevent a DDOS to NTP?  I dunno. Too many requests can appear to be an attack.

---

### Post by 1clue on 2016-09-09
I have comments about several aspects of this discussion:

NTP servers:  

[LIST]
[*]Given the reliance on accurate time/ntp servers and that this is a business for you, I strongly recommend 2 or 3 hardware stratum 1 time servers.
[*]The entire point of time servers it to reduce latency of the time source. Putting the ntp server on a VM increases latency even if only slightly.
[*]I have a stratum 1 Raspberry Pi time server. I would recommend you get something a little beefier. Maybe an atom processor like minnowboard?
[*]My time server, all in, was about $100 USD. A pi has latency problems due to both network and "disk" being run through a single low-bandwidth USB chip. My server is stratum 1 but is not as accurate as I would like.
[*]Get something with gigabit ethernet and benchmarks suggesting that the system can push it at wire speed, even if it's just pushing /dev/zero. This system will be fast enough to reduce latency and get you a better time server.
[*]Best practices suggests a dedicated system with a high quality time source (gps or some other source) on it, OR a system which has a pretty constant load and plenty of CPU overhead available. You also want constant temperature if possible.
[/LIST]
 
VMs: 
[LIST]
[*]The best practices AFAIK is to sync from the host OS (not in a VM) and then pass the time through to the VMs.
[*]Otherwise you're running the same code multiple times to try to control a single clock.
[*]Not only is that redundant it's somewhat ridiculous and possibly prone to thrashing.
[/LIST]

Syncing:
[LIST]
[*]Do you have multiple processes trying to control the system clock on the same physical hardware?
[*]Are you running some sort of circular reference in your ntp configuration? Meaning A depends on B depends on C depends on A.
[*]This still seems like a networking error to me.
[/LIST]

---

### Post by bob_jones2 on 2016-09-10
@1clue,

I'm not convinced about the value of many of the suggestions you are making here, for example (but not limited to) your statement *"Get something with gigabit ethernet and benchmarks suggesting that the system can push it at wire speed"*.... come on, be serious !

Fact of the matter is NTP was never designed for high-accuracy.  It was developed as an efficient means to synchronise time over networks to reasonable degree of accuracy, that's exactly what the NTP RFC tells you :

>   The purpose of the NTP protocol is to convey timekeeping information
   from these primary servers to secondary time servers and clients via
   both private networks and the public Internet.

Premature and excessive "optimisation" (i.e. many of the suggestions you are making), will in reality have not much effect on NTP.

If you're obsessed over getting the time as accurate as you can, then you want to look at tools that are better suited to the job, such as PTP :

> The accuracy expectations of PTP synchronized clocks is in the order of  100 ns determined primarily by the resolution and stability of a  dedicated clock oscillator and counter. The accuracy expectations of NTP  vary widely, depending on the motherboard oscillator and counter.  Typical results range from a few microseconds in PPS-assisted primary  servers to tens of milliseconds in widely dispersed Internet networks.

(from [https://www.eecis.udel.edu/~mills/ptp.html](https://www.eecis.udel.edu/~mills/ptp.html))

---

### Post by 1clue on 2016-09-10
Surely ntp does not require anything like gigabit speeds, or even 10mbps. What gigabit ethernet does is reduce latency.

All I'm really saying is that my raspberry pi stratum 1 time server is at the lower end of accuracy rather than the higher end. Just about the same money would have made it higher end, and a bit more would have made it much more accurate.

I confess to not being much on an ntp expert, but I have experience with raspberry pi time servers and so spoke up. Take it or leave it.

My time server is at my home, and syncs 5 pieces of hardware, some of which are VM hosts. The nature of my work makes accurately synced time desirable. My stratum 1 time server is preferable to others on the Internet according to my ntp clients, as they choose my time server most of the time.  But IMO a little bit faster system would have made it much more rare that the clients would choose an exterior server.

---

### Post by bob_jones2 on 2016-09-10
> What gigabit ethernet does is reduce latency

Yes, but its totally un-necessary to worry about latency with NTP.

The whole point of NTP and the algorithms built into it, is it is designed to deal with variable-latency networks. 

I am about to prove it to you....

> The nature of my work makes accurately synced time desirable

That may be the case, but you can get incredibly accurate time just over the internet, here's a NTP server for a network I run, getting access to a GPS signal is difficult because of the high-security location, so I sync with remote stratum 1 (having gone through the proper notification and authorisation processes), and yet I manage to get precision of 2^-24 seconds (see below).  This is over the internet, and not gigabit or any of the questionable "optimisations" you are suggesting.  The NTP server isn't even on a physical machine, its a VMware virtual machine !

Does the "nature of your work" really require a precision greater than 2^-24 seconds (i.e. approx 1 microsecond if my rough conversion is correct) ??  If so, as I said, you need PTP or something more serious !

> 
associd=0 status=0615 leap_none, sync_ntp, 1 event, clock_sync,
version="ntpd 4.2.8p4@1.3265-o Tue Aug  2 08:19:53 UTC 2016 (1)",
processor="x86_64", system="Linux/4.4.0-36-generic", leap=00, stratum=2,
precision=-24, rootdelay=9.008, rootdisp=40.902, refid=XXXXXXXXXX,
reftime=XXXXXXXX  Sat, Sep 10 2016 21:23:07.750,
clock=XXXXXXXX  Sat, Sep 10 2016 21:51:18.077, peer=23273,
tc=10, mintc=3, offset=-0.075166, frequency=-10.953, sys_jitter=0.113289,
clk_jitter=0.328, clk_wander=0.005


And as you can see below, the preferred server is 9ms away and the secondary  servers are all more than 10ms away ... that's way more than your 1gb  !!!!


> 
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
#name_removed   .PPS.            1 u  468 1024  377   37.695    3.348   0.272
#name_removed    .PPS.            1 u  398 1024  377   37.576    3.284   0.067
#name_removed     .PPS.            1 u   80 1024  377   41.219    4.056   0.087
#name_removed     .PPS.            1 u   45 1024  377   41.162    4.081   0.129
-name_removed    .PPS.            1 u  691 1024  337   35.639    0.248   0.249
#name_removed    .PPS.            1 u  243 1024  377   31.511    2.361   0.138
#name_removed     .PPS.            1 u  645 1024  377   37.370    2.397   0.942
#name_removed    .PPS.            1 u  837 1024  377   37.537    2.388   0.132
-name_removed .ATOM.           1 u  233 1024  377   26.639   -0.125   0.154
-name_removed .ATOM.           1 u  758 1024  377   26.435   -0.053   0.093
-name_removed .ATOM.           1 u  112 1024  377   26.704    0.035   0.114
*name_removed     .MRS.            1 u  279 1024  377    9.486   -0.161   0.213   
-name_removed   .PPS.            1 u  588 1024  375   13.983   -0.840   0.765
#name_removed  name_removed  3 u  329 1024  377   32.259    5.616   0.273
-name_removed .PPS.            1 u  643 1024  377   36.302    0.615   0.461
#name_removed .PPS.            1 u  709 1024  377   36.628    0.646   0.944
+name_removed .PTB.            1 u  534 1024  377   20.901    0.525   0.068
+name_removed .PTB.            1 u 1050 1024  377   20.809    0.301   0.113
-name_removed .PTB.            1 u  887 1024  377   20.701    0.387   0.589




Even my laptop can maintain a precision of 2^-20 seconds and that's over Wifi and all sorts of poor latency connections to stratum 2 servers!!

> 
associd=0 status=c018 leap_alarm, sync_unspec, 1 event, no_sys_peer,
version="ntpd",
processor="x86_64", system="XXXXXXXX", leap=11, stratum=16,
precision=-20, rootdelay=0.000, rootdisp=4.110, refid=XXXXXX,
clock=XXXXXXXX  Sat, Sep 10 2016 22:08:00.028, peer=0, tc=10,
mintc=3, offset=0.000, frequency=-51.537, sys_jitter=0.001,
clk_jitter=0.001, clk_wander=0.100



My guess is that you just don't understand the NTP algorithm.

If you have between 4 and 10 upstream servers defined in your NTP confg, then NTP has some very smart built-in algorithms and mathematics that will do a surprisingly good job of giving you incredibly accurate time.   The more servers, the more accurate the algorithm can make the result.   You don't need more than 10 defined (NTP only uses 10 at a time, the ones it decides not to use are merely monitored for availability incase of a need to switch).

---

### Post by hammons2012 on 2016-09-11
Out of curiosity, what OS/version are you guys running on your NTP servers? 1clue, you mentioned a Pi, so I assume you are running Raspbian? I haven't had the oportunity to build an NTP server and test a different flavor. I'll be honest too, I know nothing of NTP. I just find that I can't have more than 2 sequential queries be successful on the 16.04 servers, yet 14.04 takes them like a champ. Sounds weird. I agree it has something to do with some mechanism with blocking multiple queries on the same port to the server. If so, is there a way to allow the queries? Sounds like I have some research to do.

---

### Post by 1clue on 2016-09-11
I'm running the latest raspbian on the pi with the gps-based stratum 1 time server. I'm currently under a lot of load at work so I can't research or respond to most of the recent discussion on this thread which was directed to me. bob_jones2 is probably right.

FWIW Linux is Linux with respect to ntp. I run ntpd on 3 flavors of Ubuntu of various versions, Gentoo, Suse, straight Debian, CentOS and Raspbian. I literally copy and paste the config file between boxes, and it works. The only interesting bit to me is setting up the gps device.

As I said before I'm no expert.

---

### Post by hammons2012 on 2016-09-12
Well, I got me a patched Debian server, ran the same tests, and it performs the same way the Ubuntu 14.04 server does (it takes all of the queries like a champ). I may suggest to the customer to run a Debian OS then, so that way they can get an updated/patched OS, and everything still works as they wish. Even though, technically, this issue isn't resolved, I'm going ahead and marking it as such. There's got to be some crazy thing in 16.04 that is blocking the queries. Anywho, I'd like to thank you all for the assistance.

---

### Post by TheFu on 2016-09-12
I suspect it was something with your setup, since nothing funny happened here on my test NTP system.

---

### Post by 1clue on 2016-09-12
Since the thread is closed and I have a bit of time to parse this, I hope nobody minds me continuing the discussion.

> **bob_jones2 said:**
> ...That may be the case, but you can get incredibly accurate time just over the internet, here's a NTP server for a network I run, getting access to a GPS signal is difficult because of the high-security location, so I sync with remote stratum 1 (having gone through the proper notification and authorisation processes), and yet I manage to get precision of 2^-24 seconds (see below).  This is over the internet, and not gigabit or any of the questionable "optimisations" you are suggesting.  The NTP server isn't even on a physical machine, its a VMware virtual machine !


So this led to some really interesting data.

From my Raspberry Pi:
```

# ntpq -c rl -pn
associd=0 status=0118 leap_none, sync_pps, 1 event, no_sys_peer,
version="ntpd 4.2.8p6@1.3265-o Wed Aug 24 20:25:52 UTC 2016 (1)",
processor="armv6l", system="Linux/4.4.19+", leap=00, stratum=1,
precision=-18, rootdelay=0.000, rootdisp=1.090, refid=GPS,
reftime=XXXXXXXXXX  Mon, Sep 12 2016 16:45:49.033,
clock=XXXXXXXXXX  Mon, Sep 12 2016 16:45:55.735, peer=46575, tc=4,
mintc=3, offset=-0.001192, frequency=-6.886, sys_jitter=0.003815,
clk_jitter=0.004, clk_wander=0.001
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
o127.127.22.0    .GPS.            0 l    6   16  377    0.000   -0.001   0.004
*24.56.178.140   .ACTS.           1 u   47   64  377   62.479   13.288   5.811
+50.205.244.27   .GPS.            1 u   56   64  377   55.649    1.464   2.294
+128.138.141.172 .NIST.           1 u   44   64  377   48.014    6.042   0.937
-131.107.13.100  .ACTS.           1 u   46   64  273  110.771   21.048   0.620
+208.75.89.4     66.220.9.122     2 u   53   64  377   54.890    2.248   2.524
+72.14.188.52    129.7.1.66       2 u   51   64  377   44.405   -4.172   2.941
-2001:418:8405:4 44.24.199.34     3 u   65   64  377   85.342   -4.984   6.713
-45.56.105.98    128.59.0.245     2 u   53   64  377   74.136    2.799   1.331

```

As you can see above, my precision is -18 on a stratum 1 time server. This is considerably less than your time server, which turns out to be accurate to around 59 nanoseconds.

Now, on my router which is an enterprise-quality C2758 system from SuperMicro:

```

# ntpq -c rl -pn
associd=0 status=0615 leap_none, sync_ntp, 1 event, clock_sync,
version="ntpd 4.2.8p8@1.3265-o Tue Jun  7 20:05:56 UTC 2016 (1)",
processor="x86_64", system="Linux/4.4.8-hardened-r1-k2", leap=00,
stratum=2, precision=-22, rootdelay=0.389, rootdisp=28.073,
refid=192.168.1.2,
reftime=XXXXXXXXXX  Mon, Sep 12 2016 16:51:10.868,
clock=XXXXXXXXXX  Mon, Sep 12 2016 16:56:54.629, peer=47642,
tc=10, mintc=3, offset=2.244189, frequency=-8.258, sys_jitter=4.434699,
clk_jitter=2.890, clk_wander=0.251
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*192.168.1.2     .GPS.            1 u  344 1024  377    0.389    2.244   4.435
+171.66.97.126   .shm0.           1 u  125 1024  367   79.747    6.510   4.683
+168.215.194.18  200.98.196.212   2 u  306 1024  377   40.496    5.473   5.336
-193.170.62.252  131.188.3.222    2 u   71 1024  377  156.578   10.010   4.042
-129.6.15.29     .ACTS.           1 u   54 1024  323  123.207   44.495   5.025

```

You can see here that my router is using my pi as a reference, but it's more precise than the pi.  How is this possible?

I went to an i7 box I have and it's at -24 precision, same story.  I'm baffled.

I noticed that the 'when' column has 344 on it which is huge relatively, so i bounced the ntpd on my router. It's pulling single digits several minutes later (time enough to settle) and it has grabbed my pi again as its preferred server. It's still at -22 precision. This must not have anything to do with the precision on the pi.

> 
Does the "nature of your work" really require a precision greater than 2^-24 seconds (i.e. approx 1 microsecond if my rough conversion is correct) ??  If so, as I said, you need PTP or something more serious !


No, but I'm not getting that on my pi, which is why I suggested something with a little more speed. The numbers on my pi just aren't as good as similar projects with even slightly faster host systems. As I said before, a little more money would get you a long ways toward a better time server.

My work is happy with my setup. My comments are based on the idea that, if one is going to try to make a stratum 1 time server, you want the best results you can get for a reasonable price, defining 'reasonable' as your personal situation allows.  My choice of hardware would probably have been different had I done a little research before I built my rig.  That's all I was saying.

> 
My guess is that you just don't understand the NTP algorithm.

If you have between 4 and 10 upstream servers defined in your NTP confg, then NTP has some very smart built-in algorithms and mathematics that will do a surprisingly good job of giving you incredibly accurate time.   The more servers, the more accurate the algorithm can make the result.   You don't need more than 10 defined (NTP only uses 10 at a time, the ones it decides not to use are merely monitored for availability incase of a need to switch).


I understand the offset and round trip delay formulas but can't say that I understand the entire process.

---

### Post by hammons2012 on 2016-09-13
Well, I understand the essentials/basics of NTP, but I don't quite understand how to calculate the ntpq graph. All I know is that the closer to 0 you are, the better.


PS, this is one of the new servers I created (16.04).

```
ntpq -c rl -pnassocid=0 status=0615 leap_none, sync_ntp, 1 event, clock_sync,
version="ntpd 4.2.8p4@1.3265-o Tue Aug  2 08:19:53 UTC 2016 (1)",
processor="x86_64", system="Linux/4.4.0-36-generic", leap=00, stratum=3,
precision=-23, rootdelay=74.975, rootdisp=33.956, refid=199.182.221.110,
reftime=db82b18d.656d730e  Tue, Sep 13 2016 13:10:37.396,
clock=db82b2b6.a2b0c39c  Tue, Sep 13 2016 13:15:34.635, peer=1250, tc=10,
mintc=3, offset=-0.762149, frequency=20.181, sys_jitter=3.542234,
clk_jitter=1.429, clk_wander=0.007
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
-172.25.1.111    132.163.4.101    2 u  108 1024  377    0.140   -4.070   0.910
-172.25.1.112    152.2.133.55     2 u   83 1024  377    0.328   -3.018   0.249
 172.25.1.113    .INIT.          16 u    - 1024    0    0.000    0.000   0.000
+172.25.1.114    132.163.4.102    2 u   10 1024  377    0.439   -3.517   1.061
-173.255.246.13  204.2.134.162    3 u 1008 1024  377   70.468   -3.070   0.426
-45.127.113.2    18.26.4.105      2 u  629 1024  347   17.832   -0.105   7.315
#107.170.224.8   132.163.4.102    2 u  612 1024  377   78.253    6.403   3.085
+108.61.56.35    18.26.4.105      2 u  514 1024  377   42.428    0.278   0.307
-208.75.89.4     198.60.22.240    2 u  268 1024  377   66.673   -4.246   2.952
-71.175.64.35    69.164.203.231   3 u  363 1024  377   47.194   -2.798   1.683
*199.182.221.110 30.114.5.31      2 u  297 1024  377   67.987    0.459   0.238
-104.232.3.3     127.67.113.92    2 u  732 1024  377   78.023   -4.279   0.858

```

---

### Post by 1clue on 2016-09-13
Based on taking ntpq shots of 7 different boxes, the precision field does not measure how close to the correct time you are, but only how close it COULD be.  On any given box, the precision is always the same. It doesn't matter if ntp has just started or been running for a month, or what stratum it shows.  It's just my guess but I think precision indicates the smallest unit of time the hardware can support. Or something like that.

Think of it as precision on integer types. A byte has 2^8 bits of precision. An int has 2^16 bits (this has changed over the years) and a long has 2^32. That said, if somebody puts a number in there it has questionable accuracy, which has nothing to do with precision. Let's say somebody thought they saw about 700 cattle and so puts 700 a field not knowing that there were 643 cattle, the field is precise but not the value is not accurate.

---

### Post by 1clue on 2016-09-14
Thinking on this more, I realize that if we can measure how accurate an ntp server is, then we can make it more accurate.

Since this thread started and I played around with ntp, I did an update on my raspberry pi stratum 1 server and broke it. While fixing the setup I did some reading.

I found it frustrating that all the ntp documentation suggests that stratum 1 servers are usually <this> accurate, and then for each additional stratum they're usually <this much less> accurate.  But that's all we get. If we could actually measure how far off we are then we could use the source we're measuring against and be more accurate. Ntp is accurate within reason given the abilities of the hardware and the accuracy of the available reference servers. It's all we can ask.

BTW to the OP I'm running Ubuntu 16.04 with ntp as a client on my workstation, and it works fine. I did nothing special to get it working.

Also having done the reading, it seems to me that at least some of my suggestions on this thread hold merit:

[LIST]
[*]Faster hardware does make more accurate time *possible* within reason when comparing hardware like a Raspberry Pi.
[LIST]
[*]However it wouldn't take much more than a pi to be much more than adequate. 
[*]You could still be within the realm of single-board hobbyist computers which are not really fast enough for a desktop. 
[/LIST]
  
[*]Latency can be measured but that does not mean that the latency is consistent. Part of what ntp does is average all this out over time, but huge latencies over inconsistent networks probably (in my opinion) won't let you calculate really accurate time. 
[*]For any real business where accurate time matters, it's still best to have 2 or more local stratum 1 time servers. 
[*]It's best to sync the VM host to ntp, and pass the clock through to VM guests.
[LIST]
[*]At the very least, only one process should be in charge of keeping time on any given piece of physical hardware. 
[*]That software should be able to set the system clock on the host, and write it to the hardware clock. 
[*]Having ntp or anything like it on multiple VMs and the host is very definitely a waste of processor time. 
[/LIST]
  
[/LIST]

More observations:
[LIST]
[*]Maintaining a stratum 1 ntp server with gps on a pi, pretty much every major upgrade breaks the time server in some way. 
[*]Frequently this means recompiling ntp or some other piece of software which does not, on the raspberry pi, have the correct options compiled in. 
[*]It usually takes an hour or two, sometimes more, to fix it on hardware this small. 
[*]IMO this is why you have 2 or more stratum 1 servers for your local network in a time-sensitive business setting. 
[*]If someone is making a stratum 1 time server on Linux of any kind, I'd suggest you take all this into account. 
[/LIST]

---

### Post by hammons2012 on 2016-09-15
Just wanted to let you all know that we got a CentOS server up and going and we will be migrating to that. I don't have any doubt that if you were take a Ubuntu 16.04 box, set it up as a NTP server, and manually configure the other clients to use that box as the primary NTP server that it would work. I'm not even sure how these Calix devices query the server for time, but all that I know is that when I use the NTP Tool for Windows ([http://www.ntp-time-server.com/ntp-server-tool.html](http://www.ntp-time-server.com/ntp-server-tool.html)) and point it at the 16.04 box, I don't get any more than 2-3 packets through out of 100. It's just a really weird thing that is going on. As for all of that info about the graph/data that ntpq outputs, that helps me understand NTP just a bit more. Thanks!

---

