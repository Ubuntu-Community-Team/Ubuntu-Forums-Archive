---
title: "Server showing system restart message after restart"
date: 2011-06-02
forum: Server Platforms
---

### Post by EmilyCT on 2011-06-02
I'm running Ubuntu server 10.04.2 and am having trouble with upgrades.

When I log in, I see: 


65 packages can be updated.
41 updates are security updates.

*** System restart required ***

So I ran sudo apt-get update and sudo-apt get upgrade, then rebooted and shut down the server a few times. Still getting the same message.

Explanation?

---

### Post by brettg on 2011-06-02
Sigh, this is a bug introduced during a recent update that has caused a torrent of forum questions since it occurred. 

sudo rm /etc/motd.tail

Will fix it

---

### Post by EmilyCT on 2011-06-02
Thanks! Didn't mean to re-post; just didn't look around well enough, I guess.

---

