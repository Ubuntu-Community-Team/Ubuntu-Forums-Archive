---
title: "I can't see alias ip."
date: 2011-11-27
forum: Server Platforms
---

### Post by yavuz.maslak on 2011-11-27
I use ubuntu11.10 server.

I have 2 ips on the same interface on it.
also both work 
But I can't see alias ip when i run ifconfig.

How can I see alias ip?

---

### Post by Wayne_V on 2011-11-27
ifconfig -a

---

### Post by matt_symes on 2011-11-27
Hi

Maybe this may be affecting you. Have a read even if it does not as there have been some changes in 11.10 server for aliases.

[https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/876829](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/876829)

Kind regards

---

### Post by yavuz.maslak on 2011-11-27
actually second alias ip works I can ping at it.
But I can't see it with ifconfig or ifconfig -a

what is the solution ?

---

