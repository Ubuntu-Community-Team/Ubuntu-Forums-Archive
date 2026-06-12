---
title: "recommend a RAID5 controller card"
date: 2008-07-02
forum: Server Platforms
---

### Post by fosheezy on 2008-07-02
I'm looking for a RAID5 SATA II controller card for my Ubuntu server.  I've seen some on newegg, but have not gotten a definite answer on if any of them work under Ubuntu 8.04 server. Does anyone have a recommendation on one that will work here?

 Is setting up an ubuntu server on a hardware RAID array any different than on one drive?

---

### Post by Titan8990 on 2008-07-02
I did my homework on this recently. 3ware offers the best Linux and Ubuntu support for their cards.

> Is setting up an ubuntu server on a hardware RAID array any different than on one drive?

No, because the RAID set is created in the card's BIOS and not in the OS Ubuntu will display it as a single drive (but Ubuntu will know that it is a RAID set).

---

### Post by windependence on 2008-07-02
One word. 3Ware. They are the best for this. Period.

-Tim

---

### Post by fosheezy on 2008-07-02
any cheaper ones?  a 3ware 4 port sata II is over $250-300.

---

### Post by ixus_123 on 2008-07-02
i like lsi megaraid.  Not cheap though but the raid bios is nice and simple, their cards are pretty rock solid and the megaraid software is a good way to get at the settings without needing to reboot

---

### Post by gtdaqua on 2008-07-03
> **fosheezy said:**
> any cheaper ones?  a 3ware 4 port sata II is over $250-300.

SATA is not very good for production servers which need to up all the time. Most SATAs start to degrade after a year of continuous access. If access is intensive, they begin to degrade after 6 months! Go for SCSI or SAS. They are enterprise-grade and can sustain longer and harder punishments.

SATA is cheap and can store more data. Ideal for archiving data which is not going to be frequently accessed. In fact, the best for this sort of job.

---

