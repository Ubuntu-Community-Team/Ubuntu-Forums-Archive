---
title: "What are they trying ?"
date: 2011-07-04
forum: Security
---

### Post by Antoniya001 on 2011-07-04
Hello,
 
The last few days ip numbers from all around the globe have been pounding my server. Most of them are hopefully crashing at the firewall, but I wish to know what they are trying to do ?
 
Here is a Firestarter log. Anybody knows what port 26721 is ? They managed to overload my router 4 days ago. Needed a full reboot. my.ip.range used in the log was my real ip. Anybody ??? 
 
Getting nervous, I'm just running a personal blog. And some file services for inside the network.
 
Arjan
 
This is the blocked event list from firestarter : 
 
```

Time:Jul 3 08:19:41 Direction: Unknown In:eth0 Out: Port:5900 Source:80.84.63.237 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:VNC
Time:Jul 3 08:28:22 Direction: Unknown In:eth0 Out: Port:23 Source:189.27.91.17 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Telnet
Time:Jul 3 08:35:19 Direction: Unknown In:eth0 Out: Port:67 Source:0.0.0.0 Destination:255.255.255.255 Length:342 TOS:0x00 Protocol:UDP Service:DHCP
Time:Jul 3 08:48:55 Direction: Unknown In:eth0 Out: Port:26721 Source:92.247.209.135 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 08:53:38 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 3 08:53:53 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 09:02:39 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:147 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 09:06:48 Direction: Unknown In:eth0 Out: Port:26721 Source:212.5.131.209 Destination:my.ip.range Length:138 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 09:07:33 Direction: Unknown In:eth0 Out: Port:5900 Source:81.138.231.209 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:VNC
Time:Jul 3 09:08:29 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:138 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 09:16:15 Direction: Unknown In:eth0 Out: Port:26721 Source:212.5.131.209 Destination:my.ip.range Length:138 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 09:18:04 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:147 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 09:18:27 Direction: Unknown In:eth0 Out: Port:34917 Source:213.206.96.251 Destination:my.ip.range Length:1500 TOS:0x08 Protocol:TCP Service:Unknown
Time:Jul 3 09:19:27 Direction: Unknown In:eth0 Out: Port:38339 Source:213.206.96.251 Destination:my.ip.range Length:1500 TOS:0x08 Protocol:TCP Service:Unknown
Time:Jul 3 09:20:00 Direction: Unknown In:eth0 Out: Port:34917 Source:213.206.96.251 Destination:my.ip.range Length:1500 TOS:0x08 Protocol:TCP Service:Unknown
Time:Jul 3 09:20:12 Direction: Unknown In:eth0 Out: Port:38339 Source:213.206.96.251 Destination:my.ip.range Length:1500 TOS:0x08 Protocol:TCP Service:Unknown
Time:Jul 3 09:21:01 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:138 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 09:22:12 Direction: Unknown In:eth0 Out: Port:35437 Source:213.206.96.251 Destination:my.ip.range Length:1500 TOS:0x08 Protocol:TCP Service:Unknown
Time:Jul 3 09:22:23 Direction: Unknown In:eth0 Out: Port:26721 Source:2.96.18.163 Destination:my.ip.range Length:46 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 09:22:33 Direction: Unknown In:eth0 Out: Port:35437 Source:213.206.96.251 Destination:my.ip.range Length:1500 TOS:0x08 Protocol:TCP Service:Unknown
Time:Jul 3 09:22:38 Direction: Unknown In:eth0 Out: Port:26721 Source:2.96.18.163 Destination:my.ip.range Length:46 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 09:22:57 Direction: Unknown In:eth0 Out: Port:35437 Source:213.206.96.251 Destination:my.ip.range Length:1500 TOS:0x08 Protocol:TCP Service:Unknown
Time:Jul 3 09:23:46 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 09:26:20 Direction: Unknown In:eth0 Out: Port:42183 Source:213.206.96.251 Destination:my.ip.range Length:1500 TOS:0x08 Protocol:TCP Service:Unknown
Time:Jul 3 09:29:16 Direction: Unknown In:eth0 Out: Port:26721 Source:212.5.131.209 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 09:31:16 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 09:31:32 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:147 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 09:32:36 Direction: Unknown In:eth0 Out: Port:36116 Source:213.206.96.251 Destination:my.ip.range Length:1500 TOS:0x08 Protocol:TCP Service:Unknown
Time:Jul 3 09:37:25 Direction: Unknown In:eth0 Out: Port:67 Source:0.0.0.0 Destination:255.255.255.255 Length:576 TOS:0x00 Protocol:UDP Service:DHCP
Time:Jul 3 09:38:26 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 09:38:27 Direction: Unknown In:eth0 Out: Port:1433 Source:121.11.81.11 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 3 09:38:30 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 09:41:31 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 09:41:50 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:147 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 09:51:46 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 09:52:08 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:147 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 09:52:45 Direction: Unknown In:eth0 Out: Port:3306 Source:222.189.238.114 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Mysql
Time:Jul 3 09:58:27 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 3 10:02:01 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 10:02:26 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:147 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 10:11:17 Direction: Unknown In:eth0 Out: Port:22 Source:122.72.9.20 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:SSH
Time:Jul 3 10:12:17 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 10:34:32 Direction: Unknown In:eth0 Out: Port:26721 Source:217.79.13.13 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 10:34:34 Direction: Unknown In:eth0 Out: Port:443 Source:217.79.13.13 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 10:34:35 Direction: Unknown In:eth0 Out: Port:26721 Source:217.79.13.13 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 10:34:37 Direction: Unknown In:eth0 Out: Port:443 Source:217.79.13.13 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 10:38:48 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:147 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 10:43:14 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 10:45:11 Direction: Unknown In:eth0 Out: Port:26721 Source:217.79.13.13 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 10:45:14 Direction: Unknown In:eth0 Out: Port:443 Source:217.79.13.13 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 10:45:14 Direction: Unknown In:eth0 Out: Port:26721 Source:217.79.13.13 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 10:45:17 Direction: Unknown In:eth0 Out: Port:443 Source:217.79.13.13 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 10:53:25 Direction: Unknown In:eth0 Out: Port:1434 Source:69.13.128.102 Destination:my.ip.range Length:404 TOS:0x00 Protocol:UDP Service:Ms-sql-m
Time:Jul 3 10:53:36 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 10:53:38 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:147 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 10:53:43 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 10:53:44 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:147 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 10:55:43 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:124 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 11:03:33 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 3 11:04:12 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 11:04:30 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:130 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 11:05:14 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:147 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 11:05:39 Direction: Unknown In:eth0 Out: Port:26721 Source:75.109.212.192 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 11:07:30 Direction: Unknown In:eth0 Out: Port:26721 Source:109.224.33.204 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 11:08:27 Direction: Unknown In:eth0 Out: Port:26721 Source:115.124.66.30 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 11:11:07 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 11:12:41 Direction: Unknown In:eth0 Out: Port:1434 Source:217.149.11.169 Destination:my.ip.range Length:404 TOS:0x00 Protocol:UDP Service:Ms-sql-m
Time:Jul 3 11:14:34 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 11:15:20 Direction: Unknown In:eth0 Out: Port:67 Source:0.0.0.0 Destination:255.255.255.255 Length:338 TOS:0x00 Protocol:UDP Service:DHCP
Time:Jul 3 11:15:26 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.221 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 11:15:26 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.212 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 11:15:26 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.204 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 11:15:26 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.206 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 11:15:26 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.214 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 11:15:28 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.213 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 11:15:30 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.211 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 11:15:32 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.203 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 11:15:32 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:147 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 11:15:34 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.213 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 11:15:34 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:147 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 11:15:41 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.206 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 11:15:43 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.221 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 11:15:45 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.212 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 11:16:23 Direction: Unknown In:eth0 Out: Port:443 Source:94.210.53.35 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 11:16:23 Direction: Unknown In:eth0 Out: Port:443 Source:94.210.53.35 Destination:my.ip.range Length:47 TOS:0x00 Protocol:UDP Service:HTTPS
Time:Jul 3 11:16:26 Direction: Unknown In:eth0 Out: Port:443 Source:94.210.53.35 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 11:16:32 Direction: Unknown In:eth0 Out: Port:443 Source:110.252.207.140 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 11:16:32 Direction: Unknown In:eth0 Out: Port:443 Source:110.252.207.140 Destination:my.ip.range Length:47 TOS:0x08 Protocol:UDP Service:HTTPS
Time:Jul 3 11:16:35 Direction: Unknown In:eth0 Out: Port:443 Source:110.252.207.140 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 11:30:58 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.217 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 11:31:00 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.206 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 11:31:02 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.221 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 11:31:52 Direction: Unknown In:eth0 Out: Port:443 Source:92.114.154.135 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 11:31:52 Direction: Unknown In:eth0 Out: Port:443 Source:92.114.154.135 Destination:my.ip.range Length:47 TOS:0x08 Protocol:UDP Service:HTTPS
Time:Jul 3 11:31:55 Direction: Unknown In:eth0 Out: Port:443 Source:92.114.154.135 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 11:38:08 Direction: Unknown In:eth0 Out: Port:23 Source:46.70.128.217 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Telnet
Time:Jul 3 11:39:40 Direction: Unknown In:eth0 Out: Port:23 Source:41.232.171.119 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Telnet
Time:Jul 3 11:46:02 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.213 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 11:46:04 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.206 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 11:46:06 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.218 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 11:51:37 Direction: Unknown In:eth0 Out: Port:5060 Source:202.103.52.143 Destination:my.ip.range Length:439 TOS:0x00 Protocol:UDP Service:SIP
Time:Jul 3 12:01:05 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.218 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 12:01:07 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.221 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 12:01:09 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.203 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 12:09:13 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 3 12:09:25 Direction: Unknown In:eth0 Out: Port:67 Source:0.0.0.0 Destination:255.255.255.255 Length:338 TOS:0x00 Protocol:UDP Service:DHCP
Time:Jul 3 12:22:18 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.229 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 12:22:18 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.240 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 12:22:22 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.236 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 12:22:24 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.240 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 12:22:26 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.238 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 12:38:17 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.222 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 12:38:19 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.234 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 12:38:21 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.223 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 12:52:16 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:123 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 12:52:47 Direction: Unknown In:eth0 Out: Port:26721 Source:87.209.116.41 Destination:my.ip.range Length:46 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 12:53:03 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:123 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 12:53:21 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.231 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 12:53:23 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.238 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 12:53:25 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.224 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 12:55:28 Direction: Unknown In:eth0 Out: Port:26721 Source:91.140.63.114 Destination:my.ip.range Length:46 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 12:56:21 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:122 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:01:38 Direction: Unknown In:eth0 Out: Port:26721 Source:86.82.168.173 Destination:my.ip.range Length:46 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:06:38 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:136 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:07:49 Direction: Unknown In:eth0 Out: Port:26721 Source:92.85.153.99 Destination:my.ip.range Length:46 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:08:25 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.238 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 13:08:28 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:122 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:08:28 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.236 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 13:08:30 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:122 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:09:39 Direction: Unknown In:eth0 Out: Port:26721 Source:94.209.252.41 Destination:my.ip.range Length:46 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:12:42 Direction: Unknown In:eth0 Out: Port:26721 Source:77.162.217.26 Destination:my.ip.range Length:46 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:13:57 Direction: Unknown In:eth0 Out: Port:26721 Source:112.110.71.102 Destination:my.ip.range Length:46 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:14:29 Direction: Unknown In:eth0 Out: Port:22 Source:88.190.15.188 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:SSH
Time:Jul 3 13:15:03 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 3 13:16:56 Direction: Unknown In:eth0 Out: Port:26721 Source:62.45.238.108 Destination:my.ip.range Length:46 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:17:38 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:23:28 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.229 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 13:23:30 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.231 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 13:28:44 Direction: Unknown In:eth0 Out: Port:46167 Source:203.135.230.241 Destination:my.ip.range Length:154 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:28:56 Direction: Unknown In:eth0 Out: Port:46167 Source:64.191.21.230 Destination:my.ip.range Length:155 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:29:01 Direction: Unknown In:eth0 Out: Port:46167 Source:78.12.160.1 Destination:my.ip.range Length:189 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:31:42 Direction: Unknown In:eth0 Out: Port:26721 Source:87.212.119.75 Destination:my.ip.range Length:46 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:32:14 Direction: Unknown In:eth0 Out: Port:443 Source:213.46.65.91 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 13:32:14 Direction: Unknown In:eth0 Out: Port:443 Source:213.46.65.91 Destination:my.ip.range Length:48 TOS:0x08 Protocol:UDP Service:HTTPS
Time:Jul 3 13:32:14 Direction: Unknown In:eth0 Out: Port:26721 Source:82.171.149.5 Destination:my.ip.range Length:52 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 13:32:14 Direction: Unknown In:eth0 Out: Port:26721 Source:82.171.149.5 Destination:my.ip.range Length:47 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:32:17 Direction: Unknown In:eth0 Out: Port:443 Source:213.46.65.91 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 13:32:17 Direction: Unknown In:eth0 Out: Port:26721 Source:82.171.149.5 Destination:my.ip.range Length:52 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 13:32:23 Direction: Unknown In:eth0 Out: Port:443 Source:213.46.65.91 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 13:33:29 Direction: Unknown In:eth0 Out: Port:26721 Source:86.33.112.12 Destination:my.ip.range Length:46 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:33:30 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:129 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:34:33 Direction: Unknown In:eth0 Out: Port:443 Source:86.181.172.234 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 13:34:33 Direction: Unknown In:eth0 Out: Port:443 Source:86.181.172.234 Destination:my.ip.range Length:48 TOS:0x08 Protocol:UDP Service:HTTPS
Time:Jul 3 13:34:33 Direction: Unknown In:eth0 Out: Port:26721 Source:124.186.94.155 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 13:34:33 Direction: Unknown In:eth0 Out: Port:26721 Source:124.186.94.155 Destination:my.ip.range Length:48 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:34:36 Direction: Unknown In:eth0 Out: Port:443 Source:86.181.172.234 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 13:34:36 Direction: Unknown In:eth0 Out: Port:26721 Source:124.186.94.155 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 13:34:42 Direction: Unknown In:eth0 Out: Port:443 Source:86.181.172.234 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 13:34:42 Direction: Unknown In:eth0 Out: Port:26721 Source:124.186.94.155 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 13:34:56 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:123 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:38:34 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.223 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 13:38:36 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.229 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 13:38:38 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.236 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 13:38:42 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.240 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 13:41:07 Direction: Unknown In:eth0 Out: Port:26721 Source:95.214.30.60 Destination:my.ip.range Length:46 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 13:53:36 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.239 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 13:53:37 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.230 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 13:53:39 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.231 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 13:54:36 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.233 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 13:54:38 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.229 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 13:54:40 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.235 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 13:56:14 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.65.61 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 14:06:06 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:136 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 14:20:43 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 3 14:20:54 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:125 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 14:22:46 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.65.61 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 14:27:15 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 14:29:40 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 14:48:18 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:136 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 14:49:00 Direction: Unknown In:eth0 Out: Port:26721 Source:83.86.54.154 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 14:49:01 Direction: Unknown In:eth0 Out: Port:443 Source:83.86.54.154 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 14:49:03 Direction: Unknown In:eth0 Out: Port:26721 Source:83.86.54.154 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 14:49:04 Direction: Unknown In:eth0 Out: Port:443 Source:83.86.54.154 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 14:52:09 Direction: Unknown In:eth0 Out: Port:45634 Source:113.210.231.226 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 14:52:25 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 14:52:58 Direction: Unknown In:eth0 Out: Port:23 Source:41.34.89.157 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Telnet
Time:Jul 3 14:53:46 Direction: Unknown In:eth0 Out: Port:45634 Source:113.210.231.226 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 14:58:34 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:136 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 14:58:34 Direction: Unknown In:eth0 Out: Port:45634 Source:113.210.231.226 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 14:58:36 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:136 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 14:58:40 Direction: Unknown In:eth0 Out: Port:45634 Source:113.210.231.226 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 15:01:38 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 15:04:23 Direction: Unknown In:eth0 Out: Port:45634 Source:113.210.231.226 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 15:08:52 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 15:10:34 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 15:16:17 Direction: Unknown In:eth0 Out: Port:45634 Source:113.210.231.226 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 15:19:11 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:136 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 15:19:26 Direction: Unknown In:eth0 Out: Port:45634 Source:113.210.231.226 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 15:19:53 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 15:20:54 Direction: Unknown In:eth0 Out: Port:45634 Source:113.210.231.226 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 15:25:11 Direction: Unknown In:eth0 Out: Port:26721 Source:89.218.117.114 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 15:25:55 Direction: Unknown In:eth0 Out: Port:26721 Source:190.2.46.222 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 15:26:24 Direction: Unknown In:eth0 Out: Port:45634 Source:113.210.231.226 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 15:26:36 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 3 15:26:40 Direction: Unknown In:eth0 Out: Port:26721 Source:190.2.46.222 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 15:28:01 Direction: Unknown In:eth0 Out: Port:45634 Source:113.210.231.226 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 15:28:25 Direction: Unknown In:eth0 Out: Port:26721 Source:46.107.227.250 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 15:28:35 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 15:29:02 Direction: Unknown In:eth0 Out: Port:26721 Source:119.36.138.131 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 15:33:09 Direction: Unknown In:eth0 Out: Port:22 Source:216.241.32.13 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:SSH
Time:Jul 3 15:35:04 Direction: Unknown In:eth0 Out: Port:45634 Source:113.210.231.226 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 15:39:33 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 15:53:28 Direction: Unknown In:eth0 Out: Port:45634 Source:113.210.231.226 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 16:03:11 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:125 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 16:08:59 Direction: Unknown In:eth0 Out: Port:45634 Source:113.210.231.226 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 16:10:46 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:143 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 16:13:11 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:125 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 16:22:20 Direction: Unknown In:eth0 Out: Port:26721 Source:213.46.65.120 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 16:22:23 Direction: Unknown In:eth0 Out: Port:443 Source:213.46.65.120 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 16:22:23 Direction: Unknown In:eth0 Out: Port:26721 Source:213.46.65.120 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 16:22:25 Direction: Unknown In:eth0 Out: Port:443 Source:213.46.65.120 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 16:29:46 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 16:32:57 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 3 16:38:04 Direction: Unknown In:eth0 Out: Port:26721 Source:123.131.165.154 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 16:38:44 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.65.61 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 16:40:00 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:143 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 16:40:52 Direction: Unknown In:eth0 Out: Port:26721 Source:109.69.0.195 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 16:43:56 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:146 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 16:50:16 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:143 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 16:50:53 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.65.61 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 17:00:29 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 17:03:19 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.65.61 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 17:10:56 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:154 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 17:11:23 Direction: Unknown In:eth0 Out: Port:22 Source:210.22.12.36 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:SSH
Time:Jul 3 17:17:08 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.65.61 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 17:17:30 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:147 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 17:19:05 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.65.61 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 17:23:22 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:136 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 17:28:22 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:158 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 17:33:36 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:143 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 17:33:39 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:148 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 17:33:43 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:143 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 17:33:45 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:148 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 17:35:57 Direction: Unknown In:eth0 Out: Port:2222 Source:122.152.166.10 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 17:38:46 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 3 17:44:31 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:147 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 17:51:26 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.65.61 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 17:54:46 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:143 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 18:03:00 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.65.61 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 18:06:57 Direction: Unknown In:eth0 Out: Port:1434 Source:192.139.81.98 Destination:my.ip.range Length:404 TOS:0x00 Protocol:UDP Service:Ms-sql-m
Time:Jul 3 18:08:29 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.65.61 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 18:10:00 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:154 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 18:10:46 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.65.61 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 18:20:23 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:154 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 18:33:19 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.65.61 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 18:33:56 Direction: Unknown In:eth0 Out: Port:67 Source:0.0.0.0 Destination:255.255.255.255 Length:338 TOS:0x00 Protocol:UDP Service:DHCP
Time:Jul 3 18:34:05 Direction: Unknown In:eth0 Out: Port: Source:192.88.99.1 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 18:34:11 Direction: Unknown In:eth0 Out: Port:443 Source:86.92.131.123 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 18:34:11 Direction: Unknown In:eth0 Out: Port:443 Source:86.92.131.123 Destination:my.ip.range Length:47 TOS:0x08 Protocol:UDP Service:HTTPS
Time:Jul 3 18:34:12 Direction: Unknown In:eth0 Out: Port: Source:192.88.99.1 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 18:34:14 Direction: Unknown In:eth0 Out: Port:443 Source:86.92.131.123 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 18:34:21 Direction: Unknown In:eth0 Out: Port:443 Source:82.54.65.209 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 18:34:21 Direction: Unknown In:eth0 Out: Port:443 Source:82.54.65.209 Destination:my.ip.range Length:48 TOS:0x08 Protocol:UDP Service:HTTPS
Time:Jul 3 18:34:24 Direction: Unknown In:eth0 Out: Port:443 Source:82.54.65.209 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 18:34:25 Direction: Unknown In:eth0 Out: Port:23 Source:122.172.236.145 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Telnet
Time:Jul 3 18:34:30 Direction: Unknown In:eth0 Out: Port:443 Source:82.54.65.209 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 18:37:45 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.65.61 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 18:45:11 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 3 18:49:41 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.65.61 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 18:49:42 Direction: Unknown In:eth0 Out: Port:443 Source:94.98.178.9 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 18:49:42 Direction: Unknown In:eth0 Out: Port:443 Source:94.98.178.9 Destination:my.ip.range Length:47 TOS:0x08 Protocol:UDP Service:HTTPS
Time:Jul 3 18:49:44 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.65.61 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 18:49:45 Direction: Unknown In:eth0 Out: Port:443 Source:94.98.178.9 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 18:49:50 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.65.61 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 18:49:51 Direction: Unknown In:eth0 Out: Port:443 Source:94.98.178.9 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 18:50:03 Direction: Unknown In:eth0 Out: Port: Source:192.88.99.1 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 19:04:22 Direction: Unknown In:eth0 Out: Port:48019 Source:94.72.146.166 Destination:my.ip.range Length:56 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 19:05:07 Direction: Unknown In:eth0 Out: Port: Source:192.88.99.1 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 19:05:18 Direction: Unknown In:eth0 Out: Port:443 Source:210.89.88.134 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 19:12:50 Direction: Unknown In:eth0 Out: Port:23 Source:90.60.143.21 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Telnet
Time:Jul 3 19:20:13 Direction: Unknown In:eth0 Out: Port: Source:192.88.99.1 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 19:20:54 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.65.61 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 19:36:15 Direction: Unknown In:eth0 Out: Port: Source:192.88.99.1 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 19:39:56 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.65.61 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 19:46:36 Direction: Unknown In:eth0 Out: Port:4899 Source:31.47.136.104 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Radmin-port
Time:Jul 3 19:49:52 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.65.61 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 19:51:20 Direction: Unknown In:eth0 Out: Port: Source:192.88.99.1 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 19:51:36 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 3 19:52:19 Direction: Unknown In:eth0 Out: Port: Source:192.88.99.1 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 19:52:47 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.65.61 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 20:07:37 Direction: Unknown In:eth0 Out: Port: Source:192.88.99.1 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 20:15:31 Direction: Unknown In:eth0 Out: Port:23 Source:190.42.156.126 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Telnet
Time:Jul 3 20:24:29 Direction: Unknown In:eth0 Out: Port: Source:192.88.99.1 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 20:50:04 Direction: Unknown In:eth0 Out: Port:443 Source:217.120.178.193 Destination:my.ip.range Length:52 TOS:0x00 Protocol:TCP Service:HTTPS
Time:Jul 3 20:50:04 Direction: Unknown In:eth0 Out: Port:443 Source:217.120.178.193 Destination:my.ip.range Length:47 TOS:0x00 Protocol:UDP Service:HTTPS
Time:Jul 3 20:50:07 Direction: Unknown In:eth0 Out: Port:443 Source:217.120.178.193 Destination:my.ip.range Length:52 TOS:0x00 Protocol:TCP Service:HTTPS
Time:Jul 3 20:53:49 Direction: Unknown In:eth0 Out: Port:22 Source:201.65.70.66 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:SSH
Time:Jul 3 20:56:35 Direction: Unknown In:eth0 Out: Port: Source:192.88.99.1 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 3 20:57:07 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 3 20:59:19 Direction: Unknown In:eth0 Out: Port:22 Source:201.65.70.66 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:SSH
Time:Jul 3 22:13:20 Direction: Unknown In:eth0 Out: Port:26721 Source:95.42.232.96 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 22:13:30 Direction: Unknown In:eth0 Out: Port:137 Source:my.ip.range Destination:192.168.1.255 Length:96 TOS:0x00 Protocol:UDP Service:Samba (SMB)
Time:Jul 3 22:14:08 Direction: Unknown In:eth0 Out: Port:26721 Source:78.83.103.253 Destination:my.ip.range Length:55 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 22:17:14 Direction: Unknown In:eth0 Out: Port:26721 Source:87.210.118.171 Destination:my.ip.range Length:138 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 22:20:18 Direction: Unknown In:eth0 Out: Port:26721 Source:31.20.218.180 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 22:20:47 Direction: Unknown In:eth0 Out: Port:67 Source:0.0.0.0 Destination:255.255.255.255 Length:576 TOS:0x00 Protocol:UDP Service:DHCP
Time:Jul 3 22:20:53 Direction: Unknown In:eth0 Out: Port:26721 Source:31.20.218.180 Destination:my.ip.range Length:138 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 22:23:31 Direction: Unknown In:eth0 Out: Port:26721 Source:87.210.118.171 Destination:my.ip.range Length:138 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 22:23:57 Direction: Unknown In:eth0 Out: Port:26721 Source:95.42.232.96 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 22:24:59 Direction: Unknown In:eth0 Out: Port:26721 Source:86.91.199.83 Destination:my.ip.range Length:52 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 22:25:02 Direction: Unknown In:eth0 Out: Port:443 Source:86.91.199.83 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 22:25:02 Direction: Unknown In:eth0 Out: Port:26721 Source:86.91.199.83 Destination:my.ip.range Length:52 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 22:25:05 Direction: Unknown In:eth0 Out: Port:443 Source:86.91.199.83 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 22:32:12 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:147 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 22:32:26 Direction: Unknown In:eth0 Out: Port:45634 Source:60.49.35.157 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 22:33:48 Direction: Unknown In:eth0 Out: Port:26721 Source:87.210.118.171 Destination:my.ip.range Length:138 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 22:34:20 Direction: Unknown In:eth0 Out: Port:26721 Source:95.42.232.96 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 22:34:40 Direction: Unknown In:eth0 Out: Port:45634 Source:60.49.35.157 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 22:35:32 Direction: Unknown In:eth0 Out: Port:26721 Source:31.20.218.180 Destination:my.ip.range Length:138 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 22:36:33 Direction: Unknown In:eth0 Out: Port:45634 Source:60.49.35.157 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 22:41:11 Direction: Unknown In:eth0 Out: Port:23 Source:190.43.1.103 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Telnet
Time:Jul 3 22:42:26 Direction: Unknown In:eth0 Out: Port:45634 Source:60.49.35.157 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 22:42:38 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:140 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 22:44:06 Direction: Unknown In:eth0 Out: Port:26721 Source:87.210.118.171 Destination:my.ip.range Length:138 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 22:44:34 Direction: Unknown In:eth0 Out: Port:45634 Source:60.49.35.157 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 22:44:36 Direction: Unknown In:eth0 Out: Port:26721 Source:95.42.232.96 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 22:44:37 Direction: Unknown In:eth0 Out: Port:45634 Source:60.49.35.157 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 22:44:39 Direction: Unknown In:eth0 Out: Port:26721 Source:95.42.232.96 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 22:44:43 Direction: Unknown In:eth0 Out: Port:45634 Source:60.49.35.157 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 22:44:44 Direction: Unknown In:eth0 Out: Port:26721 Source:95.42.232.96 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 22:46:08 Direction: Unknown In:eth0 Out: Port:45634 Source:60.49.35.157 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 22:46:52 Direction: Unknown In:eth0 Out: Port:26721 Source:31.20.218.180 Destination:my.ip.range Length:138 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 22:47:33 Direction: Unknown In:eth0 Out: Port:23 Source:85.105.188.24 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Telnet
Time:Jul 3 22:48:07 Direction: Unknown In:eth0 Out: Port:45634 Source:60.49.35.157 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 22:52:06 Direction: Unknown In:eth0 Out: Port:26721 Source:62.195.127.68 Destination:my.ip.range Length:138 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 22:52:50 Direction: Unknown In:eth0 Out: Port:45634 Source:60.49.35.157 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 22:53:26 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:140 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 22:54:07 Direction: Unknown In:eth0 Out: Port:45634 Source:60.49.35.157 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 22:54:53 Direction: Unknown In:eth0 Out: Port:26721 Source:95.42.232.96 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 22:55:37 Direction: Unknown In:eth0 Out: Port:45634 Source:60.49.35.157 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 23:04:21 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:140 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 23:04:27 Direction: Unknown In:eth0 Out: Port:45634 Source:60.49.35.157 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 23:04:27 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:140 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 23:05:32 Direction: Unknown In:eth0 Out: Port:26721 Source:95.42.232.96 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 23:05:45 Direction: Unknown In:eth0 Out: Port:45634 Source:60.49.35.157 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 23:07:31 Direction: Unknown In:eth0 Out: Port:26721 Source:31.20.218.180 Destination:my.ip.range Length:138 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 23:08:20 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 3 23:08:32 Direction: Unknown In:eth0 Out: Port:45634 Source:60.49.35.157 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 23:15:32 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:140 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 23:15:58 Direction: Unknown In:eth0 Out: Port:26721 Source:125.161.170.186 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 23:16:03 Direction: Unknown In:eth0 Out: Port:26721 Source:95.42.232.96 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 23:16:08 Direction: Unknown In:eth0 Out: Port:45634 Source:60.49.35.157 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 23:16:10 Direction: Unknown In:eth0 Out: Port:26721 Source:95.42.232.96 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 23:16:11 Direction: Unknown In:eth0 Out: Port:45634 Source:60.49.35.157 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 23:17:44 Direction: Unknown In:eth0 Out: Port:26721 Source:84.151.221.208 Destination:my.ip.range Length:138 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 23:17:48 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:243 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 23:17:51 Direction: Unknown In:eth0 Out: Port:26721 Source:84.151.221.208 Destination:my.ip.range Length:138 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 23:17:54 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:243 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 23:18:08 Direction: Unknown In:eth0 Out: Port:26721 Source:84.151.221.208 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 3 23:18:15 Direction: Unknown In:eth0 Out: Port:45634 Source:60.49.35.157 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 23:19:14 Direction: Unknown In:eth0 Out: Port:26721 Source:217.73.27.46 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 23:20:07 Direction: Unknown In:eth0 Out: Port:45634 Source:60.49.35.157 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 23:20:38 Direction: Unknown In:eth0 Out: Port:26721 Source:96.18.37.64 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 23:21:27 Direction: Unknown In:eth0 Out: Port:45634 Source:60.49.35.157 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 23:24:48 Direction: Unknown In:eth0 Out: Port:33437 Source:66.35.46.194 Destination:my.ip.range Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Jul 3 23:26:17 Direction: Unknown In:eth0 Out: Port:26721 Source:178.183.163.56 Destination:my.ip.range Length:52 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 23:26:19 Direction: Unknown In:eth0 Out: Port:443 Source:178.183.163.56 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 23:26:20 Direction: Unknown In:eth0 Out: Port:26721 Source:178.183.163.56 Destination:my.ip.range Length:52 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 23:26:22 Direction: Unknown In:eth0 Out: Port:443 Source:178.183.163.56 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 23:26:26 Direction: Unknown In:eth0 Out: Port:26721 Source:178.183.163.56 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 3 23:26:28 Direction: Unknown In:eth0 Out: Port:443 Source:178.183.163.56 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 23:26:41 Direction: Unknown In:eth0 Out: Port:33437 Source:66.35.46.194 Destination:my.ip.range Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Jul 3 23:42:33 Direction: Unknown In:eth0 Out: Port:67 Source:0.0.0.0 Destination:255.255.255.255 Length:338 TOS:0x00 Protocol:UDP Service:DHCP
Time:Jul 3 23:43:08 Direction: Unknown In:eth0 Out: Port:443 Source:79.168.168.174 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 23:43:08 Direction: Unknown In:eth0 Out: Port:443 Source:79.168.168.174 Destination:my.ip.range Length:47 TOS:0x08 Protocol:UDP Service:HTTPS
Time:Jul 3 23:43:11 Direction: Unknown In:eth0 Out: Port:443 Source:79.168.168.174 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 23:43:18 Direction: Unknown In:eth0 Out: Port:443 Source:81.103.21.146 Destination:my.ip.range Length:47 TOS:0x08 Protocol:UDP Service:HTTPS
Time:Jul 3 23:43:18 Direction: Unknown In:eth0 Out: Port:443 Source:81.103.21.146 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 3 23:49:32 Direction: Unknown In:eth0 Out: Port:34275 Source:87.119.113.170 Destination:my.ip.range Length:48 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 00:03:02 Direction: Unknown In:eth0 Out: Port:67 Source:0.0.0.0 Destination:255.255.255.255 Length:338 TOS:0x00 Protocol:UDP Service:DHCP
Time:Jul 4 00:03:14 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.222 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 00:03:14 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.239 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 00:03:27 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.240 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 00:03:29 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.235 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 00:03:31 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.229 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 00:14:33 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 4 00:18:37 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.233 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 00:18:39 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.230 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 00:18:41 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.236 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 00:24:05 Direction: Unknown In:eth0 Out: Port:47604 Source:65.54.55.121 Destination:my.ip.range Length:466 TOS:0x08 Protocol:TCP Service:Unknown
Time:Jul 4 00:24:53 Direction: Unknown In:eth0 Out: Port:42613 Source:65.54.55.121 Destination:my.ip.range Length:466 TOS:0x08 Protocol:TCP Service:Unknown
Time:Jul 4 00:25:26 Direction: Unknown In:eth0 Out: Port:48659 Source:65.54.55.121 Destination:my.ip.range Length:465 TOS:0x08 Protocol:TCP Service:Unknown
Time:Jul 4 00:33:41 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.234 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 00:33:45 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.230 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 00:44:31 Direction: Unknown In:eth0 Out: Port:23 Source:78.175.205.15 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Telnet
Time:Jul 4 00:50:18 Direction: Unknown In:eth0 Out: Port:26721 Source:193.110.216.138 Destination:my.ip.range Length:140 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 01:08:29 Direction: Unknown In:eth0 Out: Port:3306 Source:222.134.200.46 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Mysql
Time:Jul 4 01:18:23 Direction: Unknown In:eth0 Out: Port:26721 Source:193.110.216.138 Destination:my.ip.range Length:140 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 01:20:37 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 4 01:28:35 Direction: Unknown In:eth0 Out: Port:26721 Source:193.110.216.138 Destination:my.ip.range Length:140 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 02:19:10 Direction: Unknown In:eth0 Out: Port:45179 Source:65.54.55.120 Destination:my.ip.range Length:466 TOS:0x08 Protocol:TCP Service:Unknown
Time:Jul 4 02:26:46 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 4 02:36:16 Direction: Unknown In:eth0 Out: Port:45634 Source:113.210.230.179 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 02:46:28 Direction: Unknown In:eth0 Out: Port:45758 Source:65.54.55.120 Destination:my.ip.range Length:466 TOS:0x08 Protocol:TCP Service:Unknown
Time:Jul 4 02:46:37 Direction: Unknown In:eth0 Out: Port:47994 Source:65.54.55.120 Destination:my.ip.range Length:466 TOS:0x08 Protocol:TCP Service:Unknown
Time:Jul 4 02:47:17 Direction: Unknown In:eth0 Out: Port:45634 Source:113.210.230.179 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 02:57:47 Direction: Unknown In:eth0 Out: Port:23 Source:93.182.202.211 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Telnet
Time:Jul 4 02:58:31 Direction: Unknown In:eth0 Out: Port:45634 Source:113.210.230.179 Destination:my.ip.range Length:56 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 03:11:53 Direction: Unknown In:eth0 Out: Port:47639 Source:65.54.55.121 Destination:my.ip.range Length:466 TOS:0x08 Protocol:TCP Service:Unknown
Time:Jul 4 03:33:34 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 4 04:10:59 Direction: Unknown In:eth0 Out: Port:26721 Source:41.134.66.22 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 04:13:44 Direction: Unknown In:eth0 Out: Port:26721 Source:81.180.66.36 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 04:14:14 Direction: Unknown In:eth0 Out: Port:26721 Source:125.162.233.75 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 04:16:20 Direction: Unknown In:eth0 Out: Port:22 Source:78.109.84.160 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:SSH
Time:Jul 4 04:29:27 Direction: Unknown In:eth0 Out: Port:43438 Source:65.55.79.89 Destination:my.ip.range Length:465 TOS:0x08 Protocol:TCP Service:Unknown
Time:Jul 4 04:39:10 Direction: Unknown In:eth0 Out: Port:23 Source:178.95.88.91 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Telnet
Time:Jul 4 04:41:45 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 4 04:43:26 Direction: Unknown In:eth0 Out: Port:2220 Source:218.87.16.135 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 04:43:35 Direction: Unknown In:eth0 Out: Port:26721 Source:95.42.177.204 Destination:my.ip.range Length:140 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 04:52:12 Direction: Unknown In:eth0 Out: Port:26721 Source:182.23.34.242 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 04:52:44 Direction: Unknown In:eth0 Out: Port:26721 Source:118.96.94.36 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 04:53:08 Direction: Unknown In:eth0 Out: Port:26721 Source:95.42.177.204 Destination:my.ip.range Length:141 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 04:54:54 Direction: Unknown In:eth0 Out: Port:26721 Source:87.250.115.246 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 04:55:13 Direction: Unknown In:eth0 Out: Port:26721 Source:202.152.59.91 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 05:29:27 Direction: Unknown In:eth0 Out: Port:23 Source:89.211.163.203 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Telnet
Time:Jul 4 05:49:44 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 4 06:10:08 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 06:44:05 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:141 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 06:52:40 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 06:57:31 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 4 07:01:00 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:142 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 07:01:17 Direction: Unknown In:eth0 Out: Port:26721 Source:68.68.40.189 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 07:01:38 Direction: Unknown In:eth0 Out: Port:26721 Source:187.115.82.130 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 07:03:38 Direction: Unknown In:eth0 Out: Port:26721 Source:189.208.110.210 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 07:03:59 Direction: Unknown In:eth0 Out: Port:26721 Source:200.107.55.141 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 07:12:10 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:142 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 07:20:48 Direction: Unknown In:eth0 Out: Port:26721 Source:95.42.177.204 Destination:my.ip.range Length:141 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 07:22:51 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:142 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 07:27:06 Direction: Unknown In:eth0 Out: Port:26721 Source:95.42.177.204 Destination:my.ip.range Length:243 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 07:33:08 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:142 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 07:41:49 Direction: Unknown In:eth0 Out: Port:67 Source:0.0.0.0 Destination:255.255.255.255 Length:576 TOS:0x00 Protocol:UDP Service:DHCP
Time:Jul 4 07:43:26 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:142 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 07:49:18 Direction: Unknown In:eth0 Out: Port:22 Source:184.107.18.248 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:SSH
Time:Jul 4 07:53:58 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:143 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 07:57:55 Direction: Unknown In:eth0 Out: Port:65500 Source:221.2.173.5 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 08:05:57 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 4 08:15:08 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:143 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 08:35:42 Direction: Unknown In:eth0 Out: Port:25 Source:118.160.219.244 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:SMTP
Time:Jul 4 08:38:06 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:143 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 08:55:35 Direction: Unknown In:eth0 Out: Port:67 Source:0.0.0.0 Destination:255.255.255.255 Length:342 TOS:0x00 Protocol:UDP Service:DHCP
Time:Jul 4 09:12:10 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:143 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 09:14:08 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 4 09:20:04 Direction: Unknown In:eth0 Out: Port:49347 Source:182.53.160.166 Destination:my.ip.range Length:223 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 09:22:27 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:143 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 09:34:46 Direction: Unknown In:eth0 Out: Port:67 Source:0.0.0.0 Destination:255.255.255.255 Length:338 TOS:0x00 Protocol:UDP Service:DHCP
Time:Jul 4 09:36:52 Direction: Unknown In:eth0 Out: Port:443 Source:82.73.193.192 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 09:36:52 Direction: Unknown In:eth0 Out: Port:443 Source:82.73.193.192 Destination:my.ip.range Length:47 TOS:0x00 Protocol:UDP Service:HTTPS
Time:Jul 4 09:36:55 Direction: Unknown In:eth0 Out: Port:443 Source:82.73.193.192 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 09:37:02 Direction: Unknown In:eth0 Out: Port:443 Source:83.196.146.209 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 09:37:02 Direction: Unknown In:eth0 Out: Port:443 Source:83.196.146.209 Destination:my.ip.range Length:47 TOS:0x08 Protocol:UDP Service:HTTPS
Time:Jul 4 09:37:05 Direction: Unknown In:eth0 Out: Port:443 Source:83.196.146.209 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 09:38:20 Direction: Unknown In:eth0 Out: Port:67 Source:0.0.0.0 Destination:255.255.255.255 Length:338 TOS:0x00 Protocol:UDP Service:DHCP
Time:Jul 4 09:39:47 Direction: Unknown In:eth0 Out: Port:443 Source:80.165.170.19 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 09:39:47 Direction: Unknown In:eth0 Out: Port:443 Source:80.165.170.19 Destination:my.ip.range Length:48 TOS:0x08 Protocol:UDP Service:HTTPS
Time:Jul 4 09:39:50 Direction: Unknown In:eth0 Out: Port:443 Source:80.165.170.19 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 09:39:56 Direction: Unknown In:eth0 Out: Port:443 Source:82.28.75.226 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 09:39:56 Direction: Unknown In:eth0 Out: Port:443 Source:82.28.75.226 Destination:my.ip.range Length:47 TOS:0x08 Protocol:UDP Service:HTTPS
Time:Jul 4 09:39:59 Direction: Unknown In:eth0 Out: Port:443 Source:82.28.75.226 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 09:52:15 Direction: Unknown In:eth0 Out: Port:4899 Source:113.161.87.129 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Radmin-port
Time:Jul 4 09:58:15 Direction: Unknown In:eth0 Out: Port:5900 Source:196.200.132.18 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:VNC
Time:Jul 4 10:22:42 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 4 10:26:24 Direction: Unknown In:eth0 Out: Port:5060 Source:82.192.79.155 Destination:my.ip.range Length:440 TOS:0x00 Protocol:UDP Service:SIP
Time:Jul 4 10:39:12 Direction: Unknown In:eth0 Out: Port:23 Source:222.155.209.221 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Telnet
Time:Jul 4 10:40:38 Direction: Unknown In:eth0 Out: Port:26721 Source:62.221.147.156 Destination:my.ip.range Length:140 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 10:46:55 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:154 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 10:57:53 Direction: Unknown In:eth0 Out: Port:26721 Source:87.121.77.11 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 11:18:42 Direction: Unknown In:eth0 Out: Port:26721 Source:77.168.152.125 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 11:21:57 Direction: Unknown In:eth0 Out: Port:26721 Source:77.76.184.80 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 11:22:36 Direction: Unknown In:eth0 Out: Port:33437 Source:66.35.46.194 Destination:my.ip.range Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Jul 4 11:23:18 Direction: Unknown In:eth0 Out: Port:26721 Source:77.76.184.80 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 11:31:58 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 4 11:35:28 Direction: Unknown In:eth0 Out: Port:26721 Source:77.168.152.125 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 11:37:03 Direction: Unknown In:eth0 Out: Port:23 Source:190.42.217.2 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Telnet
Time:Jul 4 11:45:48 Direction: Unknown In:eth0 Out: Port:26721 Source:77.168.152.125 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 11:53:11 Direction: Unknown In:eth0 Out: Port:26721 Source:212.233.197.31 Destination:my.ip.range Length:141 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 11:54:02 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:141 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 11:56:22 Direction: Unknown In:eth0 Out: Port:26721 Source:77.168.152.125 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 12:01:32 Direction: Unknown In:eth0 Out: Port:25 Source:112.104.10.205 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:SMTP
Time:Jul 4 12:06:23 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:140 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 12:07:55 Direction: Unknown In:eth0 Out: Port:26721 Source:77.168.152.125 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 12:07:57 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.146.166 Destination:my.ip.range Length:142 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 12:07:57 Direction: Unknown In:eth0 Out: Port:26721 Source:77.168.152.125 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 12:38:54 Direction: Unknown In:eth0 Out: Port:5060 Source:184.154.54.194 Destination:my.ip.range Length:446 TOS:0x00 Protocol:UDP Service:SIP
Time:Jul 4 12:39:48 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 4 12:40:06 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:141 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 12:42:21 Direction: Unknown In:eth0 Out: Port:26721 Source:41.191.236.228 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 12:42:29 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:143 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 12:42:42 Direction: Unknown In:eth0 Out: Port:26721 Source:175.136.236.137 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 12:42:46 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:247 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 12:44:15 Direction: Unknown In:eth0 Out: Port:26721 Source:121.166.88.14 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 12:45:13 Direction: Unknown In:eth0 Out: Port:26721 Source:202.150.137.216 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 12:47:46 Direction: Unknown In:eth0 Out: Port:443 Source:67.137.238.164 Destination:my.ip.range Length:60 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 12:47:49 Direction: Unknown In:eth0 Out: Port:22 Source:67.137.238.164 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:SSH
Time:Jul 4 12:50:25 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:245 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 13:47:16 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 4 13:57:24 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:143 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 15:10:57 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 15:11:59 Direction: Unknown In:eth0 Out: Port:22 Source:60.172.27.20 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:SSH
Time:Jul 4 15:12:22 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 15:14:44 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:143 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 15:17:29 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 4 15:25:19 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:143 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 15:27:55 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:138 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 15:36:14 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:143 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 15:38:07 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 15:46:46 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:247 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 15:48:28 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 15:57:38 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:247 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 15:58:52 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 16:07:54 Direction: Unknown In:eth0 Out: Port:26721 Source:78.130.131.212 Destination:my.ip.range Length:143 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 16:09:09 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 16:13:51 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:138 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 16:24:44 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:138 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 16:28:53 Direction: Unknown In:eth0 Out: Port:1433 Source:46.26.11.7 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 4 16:31:33 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 16:32:32 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:339 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 16:34:04 Direction: Unknown In:eth0 Out: Port:23 Source:118.101.6.203 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Telnet
Time:Jul 4 16:40:14 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 16:46:26 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:237 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 16:47:58 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 16:57:54 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:00:48 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:09:15 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:09:54 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:11:58 Direction: Unknown In:eth0 Out: Port:443 Source:194.72.238.62 Destination:my.ip.range Length:60 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 17:12:31 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:19:28 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:20:18 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:213 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:29:40 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:30:23 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:30:56 Direction: Unknown In:eth0 Out: Port:26721 Source:193.110.216.138 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:34:50 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:36:49 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 4 17:37:10 Direction: Unknown In:eth0 Out: Port:67 Source:0.0.0.0 Destination:255.255.255.255 Length:576 TOS:0x00 Protocol:UDP Service:DHCP
Time:Jul 4 17:39:52 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:43:16 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:47:58 Direction: Unknown In:eth0 Out: Port:26721 Source:193.110.216.138 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:48:00 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:48:00 Direction: Unknown In:eth0 Out: Port:26721 Source:193.110.216.138 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:48:02 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:48:04 Direction: Unknown In:eth0 Out: Port:26721 Source:193.110.216.138 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:48:06 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:50:04 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:52:22 Direction: Unknown In:eth0 Out: Port:22 Source:62.121.127.111 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:SSH
Time:Jul 4 17:58:12 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:241 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 17:59:38 Direction: Unknown In:eth0 Out: Port:22 Source:219.133.46.153 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:SSH
Time:Jul 4 17:59:47 Direction: Unknown In:eth0 Out: Port:26721 Source:193.110.216.138 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 18:00:29 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 18:06:16 Direction: Unknown In:eth0 Out: Port:22 Source:66.249.2.210 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:SSH
Time:Jul 4 18:09:50 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 18:10:15 Direction: Unknown In:eth0 Out: Port:26721 Source:193.110.216.138 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 18:10:41 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 18:14:10 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:211 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 18:19:29 Direction: Unknown In:eth0 Out: Port:67 Source:0.0.0.0 Destination:255.255.255.255 Length:338 TOS:0x00 Protocol:UDP Service:DHCP
Time:Jul 4 18:20:53 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 18:21:10 Direction: Unknown In:eth0 Out: Port:26721 Source:193.110.216.138 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 18:30:12 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 18:31:05 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 18:31:21 Direction: Unknown In:eth0 Out: Port:26721 Source:193.110.216.138 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 18:34:19 Direction: Unknown In:eth0 Out: Port:45634 Source:60.50.69.21 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 18:41:31 Direction: Unknown In:eth0 Out: Port:26721 Source:193.110.216.138 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 18:41:42 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 18:44:09 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:213 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 18:52:01 Direction: Unknown In:eth0 Out: Port:26721 Source:193.110.216.138 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 18:52:10 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 18:55:55 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 18:56:01 Direction: Unknown In:eth0 Out: Port:26721 Source:86.91.199.83 Destination:my.ip.range Length:52 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 18:56:01 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 18:58:07 Direction: Unknown In:eth0 Out: Port:26721 Source:193.110.216.138 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 19:01:35 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 19:02:42 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 19:06:13 Direction: Unknown In:eth0 Out: Port:26721 Source:193.110.216.138 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 19:10:20 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:213 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 19:11:38 Direction: Unknown In:eth0 Out: Port:22 Source:219.133.46.153 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:SSH
Time:Jul 4 19:11:47 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 19:12:55 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 19:18:16 Direction: Unknown In:eth0 Out: Port:26721 Source:193.110.216.138 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 19:21:21 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:213 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 19:21:51 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 19:26:49 Direction: Unknown In:eth0 Out: Port:26721 Source:88.203.244.59 Destination:my.ip.range Length:141 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 19:27:11 Direction: Unknown In:eth0 Out: Port:26721 Source:213.93.163.165 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 19:27:13 Direction: Unknown In:eth0 Out: Port:443 Source:213.93.163.165 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 19:27:14 Direction: Unknown In:eth0 Out: Port:26721 Source:213.93.163.165 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 19:27:16 Direction: Unknown In:eth0 Out: Port:443 Source:213.93.163.165 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 19:27:20 Direction: Unknown In:eth0 Out: Port:26721 Source:213.93.163.165 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 4 19:27:22 Direction: Unknown In:eth0 Out: Port:443 Source:213.93.163.165 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 19:28:02 Direction: Unknown In:eth0 Out: Port:26721 Source:94.72.147.18 Destination:my.ip.range Length:142 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 19:28:35 Direction: Unknown In:eth0 Out: Port:26721 Source:193.110.216.138 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 19:30:16 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 4 19:32:40 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:342 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 19:32:55 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 19:37:08 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 19:45:15 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 19:50:46 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 19:50:50 Direction: Unknown In:eth0 Out: Port:67 Source:0.0.0.0 Destination:255.255.255.255 Length:338 TOS:0x00 Protocol:UDP Service:DHCP
Time:Jul 4 19:50:52 Direction: Unknown In:eth0 Out: Port:26721 Source:87.120.81.161 Destination:my.ip.range Length:126 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 19:51:03 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.223 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 19:51:03 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.240 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 19:51:03 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.231 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 19:51:05 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.233 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 19:51:07 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.238 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 19:51:09 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.240 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 19:51:15 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.234 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 19:51:17 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.229 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 19:51:29 Direction: Unknown In:eth0 Out: Port:22 Source:79.172.14.99 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:SSH
Time:Jul 4 19:55:27 Direction: Unknown In:eth0 Out: Port:26721 Source:109.160.119.130 Destination:my.ip.range Length:239 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 19:59:05 Direction: Unknown In:eth0 Out: Port:443 Source:79.118.142.139 Destination:my.ip.range Length:64 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 19:59:05 Direction: Unknown In:eth0 Out: Port:443 Source:79.118.142.139 Destination:my.ip.range Length:47 TOS:0x08 Protocol:UDP Service:HTTPS
Time:Jul 4 19:59:08 Direction: Unknown In:eth0 Out: Port:443 Source:79.118.142.139 Destination:my.ip.range Length:64 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 19:59:14 Direction: Unknown In:eth0 Out: Port:443 Source:82.168.11.162 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 19:59:14 Direction: Unknown In:eth0 Out: Port:443 Source:82.168.11.162 Destination:my.ip.range Length:47 TOS:0x08 Protocol:UDP Service:HTTPS
Time:Jul 4 19:59:17 Direction: Unknown In:eth0 Out: Port:443 Source:82.168.11.162 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 19:59:26 Direction: Unknown In:eth0 Out: Port:443 Source:79.118.142.139 Destination:my.ip.range Length:64 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 20:00:01 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.240 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 20:00:02 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.236 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 20:00:04 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.230 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 20:00:08 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.231 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 20:00:11 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.239 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 20:07:00 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.229 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 20:22:00 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.234 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 20:22:01 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.238 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 20:22:03 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.222 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 20:36:39 Direction: Unknown In:eth0 Out: Port:41181 Source:94.72.148.57 Destination:my.ip.range Length:56 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 4 20:37:03 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.236 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 20:37:05 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.234 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 20:37:07 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.230 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 20:49:52 Direction: Unknown In:eth0 Out: Port:443 Source:62.98.39.251 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 20:52:07 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.230 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 20:52:09 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.223 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 20:52:11 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.240 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 21:07:12 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.229 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 21:07:12 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.240 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 21:07:14 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.234 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 21:07:16 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.233 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 21:07:20 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.238 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 21:14:13 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 4 21:14:38 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.238 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 21:14:40 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.230 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 21:14:42 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.223 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 21:17:37 Direction: Unknown In:eth0 Out: Port:22 Source:121.88.249.94 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:SSH
Time:Jul 4 21:23:14 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.236 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 21:23:18 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.230 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 21:26:02 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.234 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 21:26:04 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.232 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 21:26:06 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.229 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 21:36:28 Direction: Unknown In:eth0 Out: Port:443 Source:200.252.135.73 Destination:my.ip.range Length:60 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 21:38:47 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.240 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 21:38:49 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.222 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 21:38:51 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.239 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 21:48:26 Direction: Unknown In:eth0 Out: Port:443 Source:213.34.94.72 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 21:51:15 Direction: Unknown In:eth0 Out: Port:22 Source:218.64.215.239 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:SSH
Time:Jul 4 21:54:35 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.223 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 21:54:39 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.240 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 21:59:35 Direction: Unknown In:eth0 Out: Port:443 Source:83.83.255.244 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 21:59:35 Direction: Unknown In:eth0 Out: Port:443 Source:83.83.255.244 Destination:my.ip.range Length:47 TOS:0x00 Protocol:UDP Service:HTTPS
Time:Jul 4 21:59:38 Direction: Unknown In:eth0 Out: Port:443 Source:83.83.255.244 Destination:my.ip.range Length:52 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 4 22:02:43 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.234 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 22:02:45 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.230 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 22:02:47 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.222 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 22:03:20 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.232 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 22:03:22 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.229 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 22:03:24 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.235 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 22:08:24 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.231 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 22:08:28 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.236 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 22:12:59 Direction: Unknown In:eth0 Out: Port:22 Source:218.64.215.239 Destination:my.ip.range Length:48 TOS:0x00 Protocol:TCP Service:SSH
Time:Jul 4 22:23:34 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.240 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 22:23:34 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.229 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 22:23:36 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.238 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 22:24:28 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.240 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 22:24:30 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.238 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 22:24:32 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.223 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 22:39:32 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.222 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 22:39:33 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.236 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 22:49:57 Direction: Unknown In:eth0 Out: Port:1433 Source:124.232.165.24 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 4 22:54:35 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.232 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 22:54:37 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.223 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 23:03:49 Direction: Unknown In:eth0 Out: Port:23 Source:80.227.180.100 Destination:my.ip.range Length:60 TOS:0x00 Protocol:TCP Service:Telnet
Time:Jul 4 23:09:41 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.222 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 23:09:43 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.240 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 23:18:13 Direction: Unknown In:eth0 Out: Port:1433 Source:116.255.178.42 Destination:my.ip.range Length:40 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Jul 4 23:24:42 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.234 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 23:36:45 Direction: Unknown In:eth0 Out: Port: Source:192.168.1.8 Destination:my.ip.range Length:36 TOS:0x00 Protocol:ICMP Service:Unknown
Time:Jul 4 23:39:48 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.222 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 23:39:52 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.229 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 23:39:53 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.231 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 23:39:55 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.239 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 23:42:37 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.231 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 23:42:39 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.234 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 4 23:42:41 Direction: Unknown In:eth0 Out: Port: Source:94.245.121.229 Destination:my.ip.range Length:72 TOS:0x00 Protocol:IPV6 Service:Unknown
Time:Jul 5 00:05:40 Direction: Unknown In:eth0 Out: Port:443 Source:81.207.90.75 Destination:my.ip.range Length:48 TOS:0x08 Protocol:TCP Service:HTTPS
Time:Jul 5 00:37:23 Direction: Unknown In:eth0 Out: Port:26721 Source:193.110.216.138 Destination:my.ip.range Length:137 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jul 5 00:38:53 Direction: Unknown In:eth0 Out: Port:26721 Source:24.132.164.15 Destination:my.ip.range Length:138 TOS:0x00 Protocol:UDP Service:Unknown

```

---

### Post by jramshu on 2011-07-04
EDIT: I was thinking about ssh, sorry.

Looks like port scanning to me. Set your machine to drop ping requests.

---

### Post by Dangertux on 2011-07-04
It is automated scanning as stated above, telnet, VNC , SQL etc

Off the top of my head 26721 is unassigned, so probably looking for a remote administration port for something. 

As far as blocking icmp-echo (ping) that really won't help in this case, most scanners haven't used icmp-echo requests as their primary means of port scanning in a VERY long time.  However, if you're not running any services on these ports, stopping the scan at a firewall is irrelevant and a waste of system resources. 

I wouldn't sweat it, looks like mostly Chinese traffic which is par for course. Welcome to the world of maintaining a server I guess :-/ *shrug*

EDIT : If the traffic is too much for the router , DMZ the machine it should take a little bit of load off the router.

---

### Post by dFlyer on 2011-07-04
If your worried about your firewall go to shields up and test it. See below link.

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by jramshu on 2011-07-04
> As far as blocking icmp-echo (ping) that really won't help in this case, most scanners haven't used icmp-echo requests as their primary means of port scanning in a VERY long time. However, if you're not running any services on these ports, stopping the scan at a firewall is irrelevant and a waste of system resources.
Come to think of it I am set up to drop ping requests, but still get scanned every once in a while. 

Can't this be stopped with iptables?

---

### Post by Dangertux on 2011-07-04
> **jramshu said:**
> Come to think of it I am set up to drop ping requests, but still get scanned every once in a while. 

Can't this be stopped with iptables?

Yes -- but it's a lot of rules, and generally not worth the resources it takes up in conntrack to do it. Worrying about port scans is futile. If you really want to block port scans, I would suggest something like psad, which interactively uses iptables to block IP's that it detects performing a portscan.

The obvious issue with doing that however, if someone sends you traffic that simulates a port scan from a spoofed IP address, it can cause a reverse denial of service.

EDIT : Let's be realistic, if someone is checking for vulnerabilities on your system they're going to have a decent amount of information up front if you're running any type of server. For instance, if you have a website, they'll know you're probably running a service on port 80 and possibly 443. Which means you probably also have SSH etc, and then you start getting into banner scanning which is a whole different can of worms.

Honestly, keep your services up to date, and hope for the best. No matter how well you set up your firewall a 0 day is still going to own you. Truth of the matter, the days of port scanning and brute forcing FTP passwords are by and large gone. Either a service is going to be exploited directly for instance via a buffer overflow , or web content will be exploited. XSS , CSRF, SQL Injection etc. None of these can really be "firewalled" so to speak. So, best practices, audit your code, harden your services and hunker down. Then of course you get the random angry teenager or competing business who acquired a botnet for the soul purpose of blowing your poor site off the net for a few days while your ISP figures out how to route the traffic lol.

---

### Post by emiller12345 on 2011-07-06
if the port scan is not a syn scan, but one of the others, this kinda a rule might really mess with their efforts.  I don't think it will effect your system much, except it might seem like a lousy connection (2% lousyness)
```
**iptables -I INPUT 1 -m statistic --mode random --probability 0.02 -j DROP**
```your log is indicating only the syn attempts (I believe). But if they try the others it might make it harder on them with their scanning. 
(Dropped packets show up as filtered with nmap)

---

