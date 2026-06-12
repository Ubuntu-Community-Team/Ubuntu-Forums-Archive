---
title: "HowTo: 2 HD on RAID 0"
date: 2010-05-26
forum: Server Platforms
---

### Post by manolomanolo on 2010-05-26
Hi to all. I would like to configure my computer with two hard drives set to RAID 0 but I just don't know where to start. Any suggestion, please? Thanks

---

### Post by i.r.id10t on 2010-05-26
I'd recommend NOT doing it. The 0 in the name "RAID-0" indicates how much data you'll be able to recover if you have a drive failure.

[http://techgurulive.com/2009/08/10/how-to-configure-linux-software-raid-using-mdadm-on-ubuntu/](http://techgurulive.com/2009/08/10/how-to-configure-linux-software-raid-using-mdadm-on-ubuntu/)

---

### Post by dragos2 on 2010-05-26
With 2 drives you can try RAID 1. You will have the same read speed as in raid 0 but only
the write speed of one drive. With this setup you can lose one drive and keep working.

---

### Post by manolomanolo on 2010-05-26
Thank you all for your replies.

I am not interested into the "redundance" property of the RAID configuration since I have just to make some benchmark tests.

I modified the PostgreSQL source code and now I have to benchmark it. I supposed that RAID 0 is the nearest configurations to a typical business configuration, taking in account my hardware.

SUN ULTRA 24 - WORKSTATION
8 GB ram
250 GB hard disk + 1,4 TB hard disk
Intel Core 2

RAID 0 will surely permitt to make test on db up to 1 Tera, right?
Does RAID 0 make sense in this context?

Thank you.

---

