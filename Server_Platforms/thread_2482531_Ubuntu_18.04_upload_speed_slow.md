---
title: "Ubuntu 18.04 upload speed slow"
date: 2023-01-03
forum: Server Platforms
---

### Post by zin-ko142 on 2023-01-03
Hello I am newbie at this forum. I am sorry that my post is not relate to this forum.
Currently I have Ubuntu 18.04 VPS which is provided by hosting provider. 
When I tested with Speedtest in the server, the download speed is normal. Around 120 Mbps which is max bandwidth provided by provider.
But the upload speed is only around 4 Mbps which is unacceptable speed and the data upload to the server is very slow. 
Does anyone suggest me what to do? What will be the cause? Is it relate with Ubuntu version? Thank you.

here is my speed test result.

root@vm202301031529:~# speedtest
Retrieving speedtest.net configuration...
Testing from xxx (xx.xx.xx.xx)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by 3BB (Nakhon Pathom) [1444.61 km]: 3.613 ms
Testing download speed................................................................................
Download: 1538.26 Mbit/s
Testing upload speed......................................................................................................
Upload: 4.17 Mbit/s

---

### Post by howefield on 2023-01-03
Not a development release so thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by MAFoElffen on 2023-01-03
Depends on your ISP and connection type. Upload speeds are a fraction of the download speeds, and if you need more, or think there is something wrong, discuss it with your ISP. Higher speeds are possible, but you pay for it. Yours seems a bit slow. I think a Commercial 1G connection is around 20-30Mb/s upload on fiber.. But upload speed is usually only 1.5-5% of the download speed on non-commercial connections.

I know someone who offers cloud backups as a service for small businesses, but he pays dearly for that. They have business enterprise fiber that is available from his ISP from 2Gbps to 1Tbps. He has 2 bonded fiber runs to his router, and fiber to his fiber switches, etc. I think his is 25Gbps download and 3Gbps upload speeds at his servers. I never asked him what he pays...

---

### Post by LHammonds on 2023-01-03
Versions of Ubuntu do not artificially limit bandwidth on its own so there should not be a major speed difference if you were using any of the various versions (12, 14, 16, 18, 20 or 22).  However, version 18 is a bit long in the tooth and would be a good idea to see if you can run your services on version 20.04 or 22.04.

When you signed up for VPS, you should have been informed as to the expected bandwidth for up/down....and probably selected a plan based on how much is available.  You need to check your service level agreement (SLA).

Keep in mind that when you do a speedtest, the results are not lab best-case scenarios.  You are probably running the test while services are active which may be detracting from the overall number(s).   You will need to do speed tests multiple times throughout a 24-hour period to get a good picture of the overall rather than just a single data point.

My bandwidth connection is currently 332 Mbit/s down, 769 Mbit/s up but that is a dedicated onsite fiber that is currently hosting a lot of servers...so that speed is "leftover" bandwidth that is available to the test.  The connection also allows for temporary burst speeds so I can get some fairly random numbers doing various tests.

LHammonds

---

