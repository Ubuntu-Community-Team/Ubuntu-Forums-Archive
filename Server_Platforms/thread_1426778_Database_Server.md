---
title: "Database Server"
date: 2010-03-10
forum: Server Platforms
---

### Post by Vegan on 2010-03-10
Anybody using MySQL as the only application on a server. I was thinking that a dedicated server might have some advantages once my shop becomes a bit larger.

I use MySQL with my web server now, but I was thinking for future reference etc.

---

### Post by Iowan on 2010-03-10
My LAMP server is still a development toy... uh, tool. Even if it were used only for MySQL, I'd probably also leave it as SSH server for headless, remote access.

---

### Post by Vegan on 2010-03-13
I was thinking about that too, but I was also pondering webmin for the servers if I can get them all working the way I want.

I am planning a wall of servers and wanted to make sure my ideas are valid before i start wasting cash

---

### Post by Xipher on 2010-03-13
SSH is a requirement on any server regardless of any other administrative interfaces available. It's simply too reliable to overlook and it's what you will fall back on when every thing else is dead except networking.

---

### Post by Sporkman on 2010-03-13
Here's a dedicated MySQL ubuntu-based "appliance" package:

[http://www.turnkeylinux.org/mysql](http://www.turnkeylinux.org/mysql)

---

