---
title: "Administer Firestarter via Command Line?"
date: 2007-05-07
forum: Server Platforms
---

### Post by stealth17 on 2007-05-07
Is there anyway I can admin firestarter settings through command line so that when I connect with SSH I can make adjustments when needed? As of now all I can figure out is how to start or stop the firewall from command line, but since I'm using it as a router to another computer I would like to be able to forward ports and stuff remotely as well.

Either that or a web-based configuration interference would work too.

Thanks.

---

### Post by mlind on 2007-05-07
what firestarter does is that it creates iptables ruleset and loads it when firestarter daemon is started. You can add new iptables rules via command line.

---

