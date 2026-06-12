---
title: "virtual network interface not coming up on boot"
date: 2010-09-22
forum: Server Platforms
---

### Post by gollum53 on 2010-09-22
Hello,
I have a problem on several of our servers: After upgrading to ubuntu server Lucid 64bit, sometimes some of existing virtual interfaces (eth0:0 etc.) don't come up after reboot even if it is configured to start up automatically in /etc/network/interfaces. This issue does not happen after every reboot though. There is no relevant information in the log files or at least I cannot find anything. When I run "ifup eth0:0" manually, then the interface starts up without any problem. Has anyone seen this behavior too? 
Thank you
Roman Smid

---

