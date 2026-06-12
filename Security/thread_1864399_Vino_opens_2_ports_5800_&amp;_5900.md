---
title: "Vino opens 2 ports: 5800 &amp; 5900"
date: 2011-10-18
forum: Security
---

### Post by mrsuess2 on 2011-10-18
In Ubuntu 10.10, Vino only opened up port 5900 when remote desktop was enabled.  To increase security, I used gconf-editor (dconf-editor in 11.10) to only allow connections from localhost (lo), and would only use VNC over ssh via tunneling.  However, in 11.10, when Vino is enabled it opens up both 5800 and 5900.  I can still bind 5900 to localhost only, but I can't figure out a way to do this with 5800.  Ideally, I would have 5800 closed and only 5900 open, but I'm not sure how to do this.  Do you have any suggestions for hardening this configuration? It's annoying to have 5800 opened up to the world.  I suppose I can a firewall to stop access, but is there any way to stop it from being opened in the first place and still have Vino enabled?

---

