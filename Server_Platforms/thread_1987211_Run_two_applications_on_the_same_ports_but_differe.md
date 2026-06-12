---
title: "Run two applications on the same ports but different IP?"
date: 2012-05-26
forum: Server Platforms
---

### Post by vapid2323 on 2012-05-26
Hey guys,

I have a basic question for you, and it deals a bit with running a minecraft server (yah I know lol)

Anyhow I run a dedicated 2U server with 4 IPs, I have the interfaces setup as:

iface eth0 inet static
iface eth0:0 inet static

Etc.

My question is, is it possible to run two minecraft instances on the _same port_ but utilizing different ip's?

The idea is that someone would be able to join my server via:

mc.domain.com for server #1
pvp.domain.com for server #2

Minecraft will force you to place a port after the server name if its not on the default port. I am trying to avoid that.

I hope this was clear, let me know if you need more info.

---

### Post by sanderj on 2012-05-26
[http://www.minecraftwiki.net/wiki/Server.properties#Server.properties](http://www.minecraftwiki.net/wiki/Server.properties#Server.properties) says you can specify the IP address at "server-ip=", so ... have you tried that?

---

### Post by vapid2323 on 2012-05-26
> **sanderj said:**
> [http://www.minecraftwiki.net/wiki/Server.properties#Server.properties](http://www.minecraftwiki.net/wiki/Server.properties#Server.properties) says you can specify the IP address at "server-ip=", so ... have you tried that?

I will continue to test with that, but at the moment it can ping the IP but the game will not connect with my IP.

Thank you for the tip though! I totally missed that basic option!

---

