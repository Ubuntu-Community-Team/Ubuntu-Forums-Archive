---
title: "Blocking certain ports"
date: 2007-01-02
forum: Server Platforms
---

### Post by tdlrali on 2007-01-02
Hi community!

I am setting up a server, and i only want it to be accessible from the web through certain ports (80,22), all others blocked. The reason why I am trying to do this is because I have an administration panel (webmin) running on port 10000. I do not want the web to be able to access it, I should only be able to access it when I tunnel that port through SSH and then connect to it (basically connecting to localhost:10000).

So I am trying to block access to all ports except a few from anywhere but localhost.

Which firewall would you guys recommend (no X, just text)?

Thank you,
Felix N.

---

### Post by invalid on 2007-01-02
With just a terminal server, I would suggest using iptables rules. I personally am not familiar with the configuration, so I will leave that to someone else. There are countless tutorials available on the web, though.

---

