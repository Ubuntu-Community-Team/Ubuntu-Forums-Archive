---
title: "Ubuntu 18.04 Disable systemd-resolved on server"
date: 2018-07-09
forum: Server Platforms
---

### Post by courtney2 on 2018-07-09
So I know there are ways to disable systemd-resolved and then set dns=default with network-manager, but using this brings in some dependencies I don't want (such as wpasupplicant and some bluetooth software). To my understanding, network-manager is desktop software, and I would rather not have that on my server. Could I simply just let systemd-resolved sit on my server, and then set up my resolve.conf file and set the immutable attr on it so systemd can't change it? Or will that cause other headaches?

---

### Post by courtney2 on 2018-07-12
Unfortunate how this forum has gone kaput over the years for semi-advanced questions. If I find a way myself or elsewhere, I'll share my findings

---

