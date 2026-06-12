---
title: "iSCSI"
date: 2010-08-25
forum: Server Platforms
---

### Post by S.R on 2010-08-25
I am figuring this is the best place for a server hardware question. How is the support for iSCSI?

---

### Post by BkkBonanza on 2010-08-26
I use iSCSI on my Ubuntu based home router and it works well. Whether it does everything you need I couldn't say unless you have more info.

I have it setup with external eSata drives so that when powered on they auto-mount and become visible on the LAN. This works but needed some special udev rules added.

I don't think it currently supports multiple concurrent mounts though. I may be wrong on that but I think I read that was still a limitation. So if you need full multi-user access your'e better off with Samba probably. 

iSCSI has been faster than Samba in my brief tests. Samba is more flexible.

---

### Post by S.R on 2010-08-26
Thanks. I am learning severs the hard way by building one.

---

### Post by BkkBonanza on 2010-08-26
Actually I think that is the only way. Someone can teach you but doing it and gaining experience is necessary.

---

