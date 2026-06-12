---
title: "Creating an init.d script"
date: 2008-03-31
forum: Server Platforms
---

### Post by BillGod on 2008-03-31
I am not sure the best way to do this.  So I will just say what I am trying to do and you guys can give input as to the best way to do it.

I have a command line program I need to run.  Specifically balance (load balancing software.)  I need to run the command "balance mysql IPaddress1 IPaddress2"  I need this to run as an init.d script.  I know I can just add it to rc.local and run it on startup.  That is not how I want to run it.  I am trying to get heartbeat to run it as a service.  This way I can have 2 servers acting as a load balancer and if 1 dies the other will take over.  I have tried ultra monkey for 2 weeks now and have never gotten it to work.  So this is the best way I can come up with.  So if anyone has input as to:

A. create an init script to run my command line
B. better way to do this

It would be GREATLY appreciated.

Thanks
Bill

---

