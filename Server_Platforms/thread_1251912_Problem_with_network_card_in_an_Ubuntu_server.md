---
title: "Problem with network card in an Ubuntu server"
date: 2009-08-28
forum: Server Platforms
---

### Post by Milambar on 2009-08-28
I am a volunteer sysadmin for a small, but growing mmorpg. Our setup consists of 3 machines and a cisco firewall unit. The three machines are all running Ubuntu. Here is the uname -a output from one of them:
```

Linux gameserver 2.6.28-15-server #49-Ubuntu SMP Tue Aug 18 20:09:37 UTC 2009 x86_64 GNU/Linux

```
The three machines are identical but each serves a different purpose. One machine is the login server, one is the world server, and the third is the database server.

The world-server links directly via a LAN to the database server and the login server. The link between the world server and the login server is "busy", with people logging in all the time. However, the link between the world-server and the database-server is insane. I don't have any hard figures, although I could probably monitor it if needed, but the database server not only serves the login server with authentication tokens, it also supplys the world server with the realm data.

This is the problem. Since the last kernel update, the internel link (eth1) that connects the db server to the world server, keeps going dead during our peak periods. Im guessing its just getting saturated with traffic. A quick "ifdown eth1; ifup eth1" works to bring it back.

The point is, it didn't do that under the last kernel, only the newest kernel, and I don't have any idea where to start debugging the problem.

I welcome any suggestions and/or advice. 

The boxes run "headless" at a datacenter, so suggesting things that need a GUI are of no use.

---

