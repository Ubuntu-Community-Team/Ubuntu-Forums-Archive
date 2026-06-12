---
title: "Deploy desktop images from Ubuntu server?"
date: 2008-03-27
forum: Server Platforms
---

### Post by ThaddyBoy on 2008-03-27
I'm trying to figure out how to deploy window images from an ubuntu server.
Possible?
I'm trying to get it running similar to Novel Zenworks.
__________________

---

### Post by craigp84 on 2008-03-27
Yes- [http://oss.netfarm.it/guides/ris-linux.php](http://oss.netfarm.it/guides/ris-linux.php)

---

### Post by ThaddyBoy on 2008-03-27
That's kind of what I'm looking for. But more like a way to take an already created production image and slap it to a desktop.

---

### Post by netlogic on 2008-03-27
1. Setup a samba server
2. Create an image using a live cd that contains partimage such as systemrescuecd or RIP.
3. go to the new machine and lauch your livecd. If you want to automate parted and partimage, you can dump your scripts to rc.local

This the same way how people deployed XP using Ghost, but this is a 100% free solution.

---

