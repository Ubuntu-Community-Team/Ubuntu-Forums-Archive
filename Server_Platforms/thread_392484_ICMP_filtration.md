---
title: "ICMP filtration"
date: 2007-03-24
forum: Server Platforms
---

### Post by tiger's on 2007-03-24
Hi, team!

I'm a newbie in Linux (my last exp was with home PC / slackware 7 :-) ). 

No I've got a OpenVPN+OpenSSH server (Ubuntu 6.10) with future sight including apache. 

Right now my task is to create apropriate iptables rules. I've done a simple start-up script like 

```
#! /bin/sh
iptables-restore /home/user/iptables.config
```

Maybe later I'll upgrade it to a normal script :-)

So, after a long "abstract" :-) my question:

Can someone advise something better than:
```

-A INPUT -p icmp -j ACCEPT

```

And may be there are filtering modules like Intrusion Detection Systems etc for other kinds of traffic?

Thank you!

---

