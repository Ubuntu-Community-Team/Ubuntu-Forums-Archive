---
title: "Ubuntu Server 10.10 &amp; 11.04 outgoing connection issues"
date: 2011-04-26
forum: Server Platforms
---

### Post by hypetech on 2011-04-26
I'm having a frustrating issue with outgoing connections on an Ubuntu server.  I have had a server in place running 10.10 for quite a while now with no issues.  The last time I logged into the server was about a month or two ago and I did some system updates and outgoing connections were working fine.  Before this, the server had been in place for almost a year, working perfectly fine.  

I logged in a couple of days ago, and noticed that I could no longer initiate an outgoing connection of any kind.  While I could still access the SSH, FTP, Murmur, HTTP, and other services running on the box, I could not ping out to an IP, complete a dig, or create any other outgoing connection.

In an effort to troubleshoot, I uninstalled iptables, switched network cables, switched ports on the switch, tested a windows machine using the same IP configuration on the cable (it worked), and made sure that none of the outgoing rules on the hardware firewall applied to the server in any way.

None of this was successful, so I decided to try to re-install Ubuntu Server 10.10.  During the install, I noticed that apt was able to download packages successfully using the same IP configuration the server had previously, so I thought the issue was resolved.  However, when the server rebooted into the fresh Ubuntu installation, it was again unable to initiate any outbound connections.  I also tried today to install 11.04 server on it just as a test and had the same results.  apt would successfully connect and download files during installation, but once booted into the finalized operating system, the issue reappeared.

Was there some package change in the core packages in the last couple months that would affect outgoing connections?  I'm quite familiar with ubuntu and networking in general, so I'm really just stumped here.


Edit: It figures that as soon as I break down and post for help, I resolve the issue.  It turns out that for some reason I am unable to communicate with google's dns servers from this server.  Does anybody know if Google blocks DNS traffic for any reason on individual IPs?

---

