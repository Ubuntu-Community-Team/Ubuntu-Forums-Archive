---
title: "Physically moved server, network acting strange, can't SSH [12.04LTS]"
date: 2015-11-28
forum: Server Platforms
---

### Post by robin21 on 2015-11-28
Hi all,

I've recently moved house and just unpacked my server. I'm a a different router now (TP-Link TL-WR841) and although I have internet, I can't SSH into my server and networking takes a long while to come up at boot (waiting.. waiting another 60 seconds).

I've tried;
-Flushing IP tables
-double-checking /etc/networking/interfaces (DHCP client, no static IP)
-checking the interface SSH listens on

But apparently, it still doesn't like my new home network. What should I check next? :(

---

### Post by darkod on 2015-11-28
If you have it plugged to a monitor, try to check from the server side... For example, check the IP with ifconfig, just in case. Then try to ping 8.8.8.8, domains like yahoo.com or google.com, and to ping the private IP of your desktop that you are trying to connect from...

You can also disable iptables temporarily if the server is in your home network and there is no danger from the outside. See if that makes a difference...

Basically, that's all. Use ping to test connectivity to your router, desktop, outside domains and public IPs... That's the start.

---

### Post by robin21 on 2015-11-28
Hi Darko, thanks for your reply.

I can ping to google, etc; it also pulls updates in just fine. I can access web pages on the server from my home network and even Windows shared directories work.

Because of this, first I suspected my SSH config; but this doesn't explain the "waiting for network configuration" boot time hanging I'm experiencing?

---

### Post by darkod on 2015-11-28
Have you tried static IP, just to cover that option too? A server should really have a static IP anyway, even a basic home server... I have no other ideas right now... You didn't make any changes except plugging it into a different router, that should not matter at all.

---

### Post by Habitual on 2015-11-28
contact your ISP?

---

