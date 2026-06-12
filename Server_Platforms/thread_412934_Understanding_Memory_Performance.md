---
title: "Understanding Memory Performance"
date: 2007-04-18
forum: Server Platforms
---

### Post by SuperMike on 2007-04-18
What commands do you type, and how do you interpret the results, to understand Linux memory performance to know if you have an Ubuntu server that needs help or is about to crash? I mean, I take it that I'll need to look at virtual memory utilization vs. RAM, or paging in/out, paging utilization, etc.

The reason I ask is because I have a way to hook these commands and results with Bash and funnel through net-snmp using the 'exec' parameter in /etc/snmpd.conf, and then pick up and chart using HP Mercury SiteScope.

My background has been web development but got outsourced, so I took an operations job to hang on with an IT job. I know Linux fairly well, especially programming, but this is one area I haven't delved into very much.

---

### Post by b3nw on 2007-04-20
while I can't speak to the issue in great detail, top and free -m will give you some numbers to start.

---

### Post by gaten on 2007-04-22
Memory use in Linux is much different than that of Windows (except for Vista, which uses a similar system as *nix). There's a bunch of articles out there, but the basics as I understand it are this: Linux predicts memory usage. 

Unlike Windows pre-vista (which I am assuming you are familiar with), Linux does not wait for you to open a program to fill memory up. If it's there, Linux will find a way to use it. This article explains it better than I can: [http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by amohanty on 2007-04-22
For system monitoring:
[http://ganglia.sourceforge.net/](http://ganglia.sourceforge.net/) with [http://nagios.org/](http://nagios.org/)

To actually look at memory utillization, top and free will give you a nice overall view. After that it depends on what application you are trying to profile and/or look at.

AM

---

