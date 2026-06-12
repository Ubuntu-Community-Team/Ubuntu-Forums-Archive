---
title: "Best way to manage bandwidth on a LAN"
date: 2010-10-28
forum: Server Platforms
---

### Post by martinofmoscow on 2010-10-28
I'm looking for an effective way to manage use of internet bandwidth by users on a local area network. Currently there is a simple broadband router and unmanaged switch, and a standalone Ubuntu Server (8.04) that provides DHCP, DNS and mail for the LAN, and a web server. Ports are forwarded from a static external IP address to HTTP, HTTPS, SMTP, SSH and IMAPS, and some security is provided by IP Tables (managed by using UFW).

There are 5 users on the network, and currently one or two of those 5 are using beyond our monthly download allowance of 30Gb. There are chiefly 2 things I'd like to achieve, and would appreciate any comments:-

1) To be aware of how many users are currently using the internet connection, and to divide the bandwidth between that number (so that if there are, say, 3 active connections, the total bandwidth available is divided 3 ways, rather than one of those users being able to hog all of it).

2) To allow each user to download up to 1/5 of 30Gb each month without any additional throttling (apart from the above), but once they go over that allowance to throttle them individually to, say, 10Kbps until the start of the new month.

I've heard other threads talking about both IP Tables and a proxy server such as Squid. I have no idea which of these would be most suited to the task. Currently, as I said, the Ubuntu server is standalone and only using 1 NIC, but it has 2 NICs and I could be configured to act as a gateway for the LAN, instead of the router, which is set to be the current default gateway.

Any comments would be much appreciated. I have a moderate amount of Linux experience and use a combination of shell and Webmin to manage the server.

Many thanks,

Martin.

---

### Post by aeiah on 2010-10-28
have you looked into putting routing software on the server? a lot of them will have QoS, and bandwidth management options. i havent used any so cant recommend any, but i imagine there are several you could try, and administer from a web interface etc.

i know you have a router, but you've already moved dhcp onto the server so you might as well go with NAT too and just use the router to provide the required physical ethernet sockets.

---

### Post by martinofmoscow on 2010-10-29
Thanks aeiah, can you or anyone suggest a (preferably easy to set up/administer) particular server app for this?

---

### Post by David006 on 2011-11-17
I'm researching a similar issue (with TC as a possible solution) for: **Ubuntu 11.10 (Oneiric)** and **Ubuntu 10.04.3 LTS ..**


( Will report back .. )

---

