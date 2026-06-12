---
title: "ufw before.rules without restarting"
date: 2011-05-10
forum: Server Platforms
---

### Post by ene_dene on 2011-05-10
I use UFW firewall on my server. In order to route traffic to some other computers in my LAN I need to edit /etc/ufw/before.rules and put some commands there.
The problem is when I put a new rule I need to restart the computer in order for the rule to work, sudo ufw restart doesn't do anything.
I really don't like restarting my server, is there a way to start before.rules without restart?

---

