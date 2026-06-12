---
title: "Moving external drives into the main case with LVM"
date: 2007-07-28
forum: Server Platforms
---

### Post by RaZoR1394 on 2007-07-28
Hi.

I'm currently using a logical volume for root spanning over 7 drives: 5 internal sata, 1 esata and one usb. What I would like to do is to move the external drives from their enclosures to the 2 free spaces in the main case and use the 2 free sata ports.

Some weeks ago I tried switching the external usb drive to esata but the computer wouldn't boot up probably because it was missing that drive for the logical volume. I thought LVM worked with UUID:s but it seems something is not right here.

Please help. The only option I know of is restarting from scratch and creating a new logical volume.

---

### Post by RaZoR1394 on 2007-07-28
Nevermind. It just worked after switching from usb/esata to sata. I guess I was lucky.

---

