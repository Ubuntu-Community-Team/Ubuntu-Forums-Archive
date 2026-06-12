---
title: "Traffic Shaping / SSH &amp; MySQL Slowness"
date: 2016-04-25
forum: Server Platforms
---

### Post by bsntech on 2016-04-25
Very odd situation here.

Two datacenters with different ISPs.  Each data center has at least a 100 mbps connection or higher.

During hours of say 1 am through 2 pm, everything is fine.

Then randomly between 2pm through midnight, MySQL replication and rsync replication between the servers (keeps them in sync) significantly slows down, disconnects, fails to connect.  But not all the time.

From Server A to Server B, I can ping and do a traceroute with an average of only 23 ms latency.  From Server B to Server A, it is the same story - about 23 ms latency.

During the same time of the major slowness, connection from Server A to Server C (different ISP) and connection from Server B to Server C are fine with no latency.  So each test fine individually through another entity.  Sometimes it is bad enough where it takes an hour to replicate 10 - 15 MB of data.

Connection seems fast and I don't believe that it is due to network saturation.  Both servers A and B also have the mini speedtest running on the web service - and when doing a speed test between the servers, the speed is very fast and normal even during the slow times.  This tells me that the network isn't saturated otherwise these speedtests would suffer too.

Almost seems like some kind of traffic shaping/filtering that is being implemented somewhere... but obviously it isn't all hours of the day and only during more peak times.

Any suggestions on how that theory could be tested or other things to look for?  MySQL runs on the standard port and rsync is done via SSH on the standard port.  The significant slowness causes major headaches and failures for the synchronization of the servers.

---

### Post by Graham_Willis on 2016-04-26
Have you checked rsync logs, including error logs? Perhaps it tries to synchronize a directory with a huge numbers of files in it or deeply nested directories or directories/files with very long names? How busy are disks on the both sides during this slowness? Does iotop tell you something interesting? Have you tried to manually rsync some data (first the same which automatic rsync is trying to download, then anything else) from the source server during this weird behaviour? If it is slow, then stop the automatic rsync and try again to manually download the data. If it is still slow, try scp (shouldn't be much of difference I guess, but it doesn't harm trying). With what priority is your rsync running? Try making it higher when the replication is slow. Is the same instance of rsync running all the time? Do you use rsync with bwlimit option? Does it write to the same disk all the time?

Also, you can try setting up a completely fresh machine and make various rsync/scp download tests (especially when the transfer of data is slow) from there.

Set up SSH on a port of a different standard service (if it is affordable) and run rsync associated with this port, check if it will make any difference.

As far as I understand the issue concerns a lot of servers, so it really seems like a kind of network problem, but perhaps the things that I listed will tell you something valuable anyway.

---

