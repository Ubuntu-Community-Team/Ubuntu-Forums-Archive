---
title: "LXD and lan static ip addresses with no NAT"
date: 2018-11-13
forum: Server Platforms
---

### Post by jason.jackal on 2018-11-13
I am new to LXD and I am reading the LXD Ubuntu Tutorial; however, I want my LXD containers to be visible to my local LAN and not have NAT. I will manually provide a static IP to my containers, but I have not been able to find a deployment guide for what I need. I need to have inbound access to my containers.

Do I still create the bridge during the LXD install? I manually created a bridge in the 'etc/network/interace' file.

Is it better to still create the bridge via LXD install and use that bridge and modify and somehow provide the OS interface for external interface?

---

### Post by jason.jackal on 2018-11-19
I was able to get through this issue. I created a normal bridge interface at the OS level; however, when installing LXD I selected 'no network', but when selecting 'bridge' I selected and defined the bridge interface I created on the OS.

Afterwards - I had to statically assign IP address on my LXD container, which was what I wanted.

---

