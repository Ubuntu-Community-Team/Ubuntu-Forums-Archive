---
title: "problems connecting with ssh"
date: 2011-01-18
forum: Server Platforms
---

### Post by guest_user on 2011-01-18
I have a server running on my network, this server currently gets its IP via dhcp. When it starts up using a particular IP, the say 192.168.1.76, I get to connect to it fine but sometimes it starts up on a different IP like 192.168.1.64 and when I try to ssh to that IP address, it gives me a connection refused error, why is this happening and how do I solve this?

---

### Post by kg4cna on 2011-01-18
You need to give the machine a static IP address, then you should be able to ssh to it.

A~

---

