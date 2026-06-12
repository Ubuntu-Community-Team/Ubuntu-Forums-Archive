---
title: "Kernel Panic ... &lt;sigh&gt;"
date: 2012-08-21
forum: Server Platforms
---

### Post by Geoff3142 on 2012-08-21
Following a package update (started manually but left unattended) my server won't boot. All I get is
kernel panic not syncing vfs unable to mount root fs on unknown block (0,0)

[FONT=Arial]The results of a Boot Repair are available at paste.ubuntu.com/1158893

I almost upgraded to 10.04 (over what I thought was 8.04 LTS) but having clicked INSTALL, I aborted at the next prompt. Things are no better or worse because of this.
[/FONT]

---

### Post by Geoff3142 on 2012-08-21
Continued research produced the following:
1. Press ESC (and NOT SPACE) to access the list of other kernel images
2. A brief power cut (shutting down the server) happened DURING the update process.

By selecting an earlier kernel, the system rebooted and offered to continue the update. It did most successfully.

Two things:
1. Not all the help in various Ubuntu sites is accurate (I could thump the person who said SPACE would call up the menu).
2. Ubuntu's recovery is awesome..

All the best.

---

