---
title: "NXSERVER sort of works"
date: 2006-01-15
forum: Server Platforms
---

### Post by duffydack on 2006-01-15
I got this to work locally but after opening the port in my router that i set in /etc/nxserver/node.conf and etc/sshd/sshd_config (not 22) i can not get it to login. It gets past auth ok and then says negotiating link params, then hangs for while, then gives me some crap about couldnt establish link with proxy or some babble.. i dont have a proxy, ... Whats wrong?
i even added a range of ports that the nxclient uses (1000 + )
nadda
ps: no firewall in linux and my routers fine,

edit:  fixed.
found out i needed to open port 5000 (opened 5000-5002 just in case since i wanna use 2-3 logins)

doesnt tell you that in any FAQ/setting guides .

---

