---
title: "Ubuntu Server 10.04 shutdowns after idle for a couple of minutes"
date: 2010-10-12
forum: Server Platforms
---

### Post by Melot on 2010-10-12
Hi!
I'm new to Ubuntu (installed it for the first time just a day ago on my server). I've Ubuntu Server 10.04 and am just using the terminal, no GUI like Gnome. So far it's working pretty great except for one big thing.

Whenever I go to sleep and there's no activity on my servers (it's not a big site so active users drop to 0 during the night), the server kind of disconnects. The only thing that can bring the site back online is to restart the whole server. I've tried disabling powersaving by using setterm but that changes nothing. Even if I wake up the server by pressing any key or so the site wont go back online!

I've tried just restarting both Apache and MySQL (I'm using LAMP-server btw) but not even that works. But as soon as I turn the power off and on at the server, everythings work like normal for a couple of minutes of inactivity (~5-15 minutes I'd guess) and then it's down again unless someone logs in to the site and is active.

This is driving me crazy! My site is down all the time I'm in school as I have no possibility to restart the server if it becomes offline. Does anyone have a clue to what could be wrong?

---

### Post by Melot on 2010-10-14
I've tested a couple of new things now:
- Disabling SSH
- Uninstalling Samba
- Added "quiet nomodeset" to grub

Nothing worked. As soon as the number of active users drops to 0 for a couple of minutes the network is shut down but the server is alive. Is there anyway to see a log of what happens so I can track the problem?

---

### Post by sdeshpande on 2011-12-19
I have the same exact problem. Have you found any solution ?

---

