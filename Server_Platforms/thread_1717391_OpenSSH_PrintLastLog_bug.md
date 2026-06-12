---
title: "OpenSSH PrintLastLog bug"
date: 2011-03-29
forum: Server Platforms
---

### Post by fela on 2011-03-29
This morning I set PrintLastLog to 'no' from 'yes' on my server's openssh configuration (Debian 5). Immediately problems appeared - friends couldn't connect using SFTP services, I managed to get myself barricaded from connecting until I set it back to yes (luckily I had a session open from earlier or I'd have had to hook up a screen/keyboard to my server :lolflag:).

Anyone heard of this 'bug' before?

---

### Post by fela on 2011-03-30
Never mind, I found the culprit. It wasn't actually anything to do with PrintLastLog (surprise surprise :)), it turned out to be Komodo Edit, and its sftp subsystem, making multiple ssh requests per minute and consequently getting blocked by the server's iptables config.

Well actually, there was an sftp problem previously where my friends couldn't connect, but that was solved in about five minutes (quick google search).

---

