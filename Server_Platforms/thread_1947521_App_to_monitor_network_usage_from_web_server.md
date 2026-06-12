---
title: "App to monitor network usage from web server"
date: 2012-03-26
forum: Server Platforms
---

### Post by OliverHaslam on 2012-03-26
Hey,

I've got a web server running at home on an Ubuntu box, and it works well.

What I want to do though is monitor how much data is being used by web traffic. Is there a good app, command line that will write to a log file, that will monitor data on port 80?

Cheers guys.

---

### Post by iclebyte on 2012-03-27
Hello,

There are a few ways to do this.

1) Since you most likley have Apache running on Port 80 and no other process can bind to it, you could use AWSTATS or some other such log analysis tool to scan your log files in /var/log/apache/* and calculate your data usage each day.

2) You could use some deep packet inspection tool to listen in on the interface via libpcap like Wireshark would and count the data transfered. The best tool for this I've come accross is called 'ntop' it gives you a web interface running on port 3000 and will let you see this data in real time: [www.ntop.org](www.ntop.org)
You can get ntop with 'apt-get install ntop'

Hope this is of some help!

Kind Regards,
Jamie

---

