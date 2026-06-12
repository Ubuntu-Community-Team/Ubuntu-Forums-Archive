---
title: "Problems with OpenVZ on Ubuntu Hardy"
date: 2008-08-23
forum: Virtualisation
---

### Post by MarkusThielmann on 2008-08-23
I'm trying to get OpenVZ on Ubuntu Hardy to work. I'm using 2.6.24-21-openvz and I'm able to create, start and use containers. 

The problem is: Whenever I try to stop a container via "sudo vzctl stop <ID>", my keyboard stops working and I'm no longer able to start new applications. Applications running will still work, but after a few minutes they start getting unresponsive. 

I'm not even able to shut down, since I'm unable to start the shutdown application. vzctl.log and syslog don't show any information besides "VE 123456 : Stopping VE ...". When shutting down via the power key, I'm able to catch a few error messages from openvz, complaining about problems with the network device driver. Unfortunately, I can't find these messages in any log files. 

I'm unsure about opening a bug report, since this might be a configuration problem. Does someone has experienced similar problems?

---

### Post by ilidio on 2008-08-23
Yep, exactly the same here and also in 2.6.24-20 kernel and not a clue as how to solve it.

Ilídio

---

### Post by MarkusThielmann on 2008-08-27
It seems this problem is fixed with the new kernel in "proposed". See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/258044](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/258044) for details and some problems with the new sync.

---

