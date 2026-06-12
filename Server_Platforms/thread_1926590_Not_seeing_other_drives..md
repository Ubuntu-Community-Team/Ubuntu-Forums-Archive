---
title: "Not seeing other drives."
date: 2012-02-16
forum: Server Platforms
---

### Post by mbudden on 2012-02-16
I have decided to move from FreeNAS to Ubuntu Server 10.04 LTS. I have noticed a few differences since moving. The biggest problem I have right now is Ubuntu Server isn't seeing my second set of drives.

I have 2 IDE drives on one controller.
2 IDE drive on another controller.

When installing Ubuntu Server, it sees all 4 drives during install. But when it was done installing. It only sees the 1st controller that has the boot drive and the storage drive. 

When doing a fdisk -l, it doesn't show the second drives. Just the first two. It worked perfectly in FreeNAS, but in Ubuntu Server... It doesn't. This is just junk hardware that was sitting around that was thrown together for me to throw stuff on. 

Any help? Thanks.

---

### Post by mbudden on 2012-02-16
Nevermind. I found my issue. Thanks anyways.

---

