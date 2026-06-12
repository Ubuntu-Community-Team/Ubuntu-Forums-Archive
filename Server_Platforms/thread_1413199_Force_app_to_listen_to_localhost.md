---
title: "Force app to listen to localhost?"
date: 2010-02-22
forum: Server Platforms
---

### Post by 5millp0x on 2010-02-22
Hello, i have a file server application that only is accessible from  my external ip on port 2112 , but i really want to access it local from localhost,  But it dossent worke, 

Some one told me that i might be possible to fix using iptables? but i cant figure out how, Can some one help me?

Thanks!!

---

### Post by cdenley on 2010-02-22
The only way you can force an application to listen on a different interface is to configure or change the application. I don't think traffic for 127.0.0.1 would reach the PREROUTING chain in the nat table, so a DNAT rule probably wouldn't work. What you can do (if you don't know how to configure the listening process) is install rinetd and configure it to listen on 127.0.0.1 and forward that traffic to your external interface.

---

