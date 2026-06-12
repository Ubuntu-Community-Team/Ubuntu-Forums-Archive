---
title: "Missing firestarter icon at panel"
date: 2007-01-31
forum: Server Platforms
---

### Post by zairulazwan on 2007-01-31
Hi... I'm so new here. I have install firestarted and run it. previously if I close firestarter window it will dock an it's icon to my panel but that is not so now... I'm not sure if it is running or not.. these goes to my GAIM program.. after closing it it won't dock to panel.

Thank you

---

### Post by raul_ on 2007-01-31
It's not supposed to. It's always running, because Firestarter is just a front-end to the built in firewall (iptables). If want to edit anything, just open it again, and then you can close it without any problems. About GAIM, i don't use it, but maybe there is a preference or an option that you need to check in order to close to the panel? Maybe "close to tray" or "close to panel" or something like that

---

### Post by zairulazwan on 2007-01-31
Thank you..  in firestarter i have already checked the this option i.e. close to tray and everything still after closing it, it did not come out in panel....
What do you mean by 'front-end to the built in firewall (iptables)'

Thank you

---

### Post by raul_ on 2007-01-31
> So, do I need a firewall, anti-virus, anti-spyware tools?
By default, Ubuntu ships with no open ports on public interfaces. In other words, a "port scan" would show all closed ports, nothing open. As a result, putting up a firewall would provide no more security than not putting one up. Remember that open ports provide services that hackers can connect to, and only if they can connect to these services can they be potentially abused and exploited.

A firewall, however, adds the benefit of peace-of-mind from accidentally installing a server program that opens up a port by default. Also, it satisfies curiousity by logging potential "hits." Linux comes with a very strong, secure, and powerful firewall called iptables, but it is relatively difficult to use from a new user's standpoint. As a result, there are many graphical tools that give you a simple user interface for configuring iptables, such as Firestarter for GNOME or Guarddog for KDE. There are many more in the repository, too. Remember--these all use iptables in the background, so find your favorite interface--they all offer the same great protection. [These last two paragraphs contributed by jdong from the Ubuntu Forums. Thanks, jdong!] 

from [http://www.psychocats.net/ubuntu/security#firewallantivirus]("http://www.psychocats.net/ubuntu/security#firewallantivirus")

---

