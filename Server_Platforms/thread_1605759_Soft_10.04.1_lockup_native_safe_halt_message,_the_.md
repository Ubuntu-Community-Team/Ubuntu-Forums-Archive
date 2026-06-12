---
title: "Soft 10.04.1 lockup: native_safe_halt message, the bug involves TCP/IP stack"
date: 2010-10-25
forum: Server Platforms
---

### Post by alecm3 on 2010-10-25
I have a server with 2.6.32-23-server (10.04.1 LTS) that locked up after 94 days of uptime. It locks up every 100 days or so, and the bug is TCP related, with messages like:
ip_local_deliver_finish
ip_rcv
net_rx_action

I have attached a picture of the console after the machine locked up.
The server only runs apache, with about 1500 requests/sec , serving small static files, and nothing else.
Has anyone seen anything similar?

---

