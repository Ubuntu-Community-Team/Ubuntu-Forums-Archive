---
title: "Disconnect Simultaneous Devices - Coovachilli, Freeeadius, Daloradius, Mysql"
date: 2017-06-22
forum: Server Platforms
---

### Post by mancharagopan on 2017-06-22
I have configured Coovachilli, Freeradius, DaloRadius. All working fine but,
I have a problem with the simultaneous device.

Example:
User A has 1 GB limit for 1 month. He login his credentials on a laptop to access the internet and also he login on his mobile at the same time. So there are two sessions. therefor he is getting 1GB on his mobile and 1GB on his laptop, totally 2GB. Mobile will get disconnected after he finish that 1GB and the laptop will get disconnected after he finished his other 1GB.



I need user A to get only 1GB limit per month no matter how many devices he use to login at the same time. after 1GB exceeded or time exceeded all the sessions should disconnected.

---

### Post by howefield on 2017-06-22
Thread moved to the "*Server Platforms*" forum.

---

