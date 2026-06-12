---
title: "Syslogd writing single entry every 5 seconds"
date: 2009-06-01
forum: Server Platforms
---

### Post by stevenickels on 2009-06-01
I am using a 6.06 Ubuntu Server system as a syslog receiver. However, the syslogd daemon (sysklogd version 1.4.1) on the system is doing something I've never seen in a syslog server before. It only writes an entry to its log files every five seconds, and only one message from each source at a time. As a result, syslog's apparent internal queue gets quickly filled up, at which point most entries get dropped and never make it into the log file.

I thought perhaps this was a networking issue, since a netstat -su showed a large number of UDP packet receive errors. However, after rebooting the server, I end up seeing single lines from the linux bootup sequence get written to the syslog log file every 5 seconds. Additionally, running a tcpdump on udp port 514 shows the expected number of incoming packets, so at some level all the syslog data I am expecting is making it to the server. This leads me to believe that the syslog daemon's internal queues are being populated, but syslog itself is only pulling a single entry off each queue every 5 seconds to write to the appropriate log files. Once the syslog queues are full, it starts rejecting incoming UDP packets, leading to the netstat packet receive errors.

Anyone know what the problem could be here? I didn't see any configuration options or command-line arguments that could cause a problem like this, but did I miss something? Does this definitely sound like a syslog problem, or is it perhaps a UDP issue like I originally thought?

Any help would be greatly appreciated.

--Steve

---

### Post by stevenickels on 2009-06-03
For anyone who was interested, the problem was a bad DNS server. Apparently every syslog message coming in was causing the server to do a reverse lookup on the incoming IP address. Since the DNS server was bad, it would take 5 seconds on each message for the DNS request to time out.

Changing resolv.conf to the correct DNS server fixed the problem.

--Steve

---

