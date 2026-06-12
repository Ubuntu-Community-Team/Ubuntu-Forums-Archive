---
title: "Qemu, Windows, and File Sharing"
date: 2008-02-06
forum: Virtualisation
---

### Post by mithrilrider on 2008-02-06
I've been using Ubuntu for about a week and love it. I want to be able to use windows on the occasions that I need to (mainly for Photoshop CS3) without rebooting my computer. I went ahead and started running XP with Qemu, but since it only has access to its own little partition, its not of too much use to me. Is there a way I can access my larger windows partition (about 70% of my total HD) through Qemu or even a way where I could use that partition to run windows from without rebooting?

Also, is there a way to make Qemu fullscreen and have it as one of my viewports?

---

### Post by bodhi.zazen on 2008-02-06
You can share files with any networking protocol.

ssh (scp), nfs, samba, ftp, http ... take your pick

---

