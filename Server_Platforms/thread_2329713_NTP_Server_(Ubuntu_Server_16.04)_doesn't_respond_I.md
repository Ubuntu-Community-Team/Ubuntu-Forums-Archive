---
title: "NTP Server (Ubuntu Server 16.04) doesn't respond IPv6 queries"
date: 2016-07-04
forum: Server Platforms
---

### Post by rudolf.vesely on 2016-07-04
Hi everyone,
I hope you are all well.

I configured Ubuntu Server 16.04 LTS as a local NTP server (installed ntp) and I wanted to query it from another server on LAN using it&#8217;s Unique Local IPv6 address (fd00::/8). ntp doesn&#8217;t respond. I checked that from another Ubuntu box using ntpdate -d server and from Windows using w32tm /stripchart /computer:server.

It&#8217;s very strange since configuration in /etc/ntp.conf is fine, server listens on udp6 (port 123 - checked using ss) and everything works great with IPv4 (I can see responds when I use ntpdate -d server).

I have feeling that it's bug but I'm not sure. Could you please help me with this?

Thank you,

Rudolf

---

### Post by Graham_Willis on 2016-07-07
Have you checked if it is not a firewall issue?

---

