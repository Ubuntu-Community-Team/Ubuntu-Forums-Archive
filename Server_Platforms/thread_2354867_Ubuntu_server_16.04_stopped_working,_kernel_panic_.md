---
title: "Ubuntu server 16.04 stopped working, kernel panic on boot"
date: 2017-03-07
forum: Server Platforms
---

### Post by space-possum on 2017-03-07
Hi all,
[ATTACH=CONFIG]274024[/ATTACH]
One of our servers stopped working. Since power cycling didn't help I connected a screen to see why it didn't boot anymore.
I've added a photo with the kernel panic dump showing on boot.

Booting using a USB stick with Ubuntu desktop live on it works, hardware seems fine.

No changes made to the hardware or Ubuntu in the days before the crash.

Any pointers on this are much welcome since we've servers with similar configuration deployed on remote locations.

Setup Ubuntu 16.04 server on Dell PowerEdge R220

---

### Post by ajgreeny on 2017-03-07
From your live USB desktop version run a filesystem check ```
sudo e2fsck /dev/sdx#
``` where sdx# is the root partition of your server.

That may be all that is needed ; it certainly worked for me a long time ago for my desktop installtion.

---

