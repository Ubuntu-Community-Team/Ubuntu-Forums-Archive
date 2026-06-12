---
title: "jaunty versus hardy (server)"
date: 2009-04-19
forum: Server Platforms
---

### Post by ae+ on 2009-04-19
Hello,

we are about to create a number of server instances on ec2 (in the next month) and are very tempted to use jaunty server as the base. The servers will predominantly be web servers using php5/mysql/memcached.

On a comparison of those packages between jaunty and hardy there are slight differences but not major ones.

Does anyone have any comments that would be useful/helpful for us in making the decision? ie. Is there anything in jaunty server that could cause instability? Would there be any gains (speed?) by using jaunty? Or are the differences so small that we should stick with LTS (hardy)?

Cheers

Andrew

---

### Post by BkkBonanza on 2009-04-19
If these servers are for anything but testing then you should use the LTS version 8.04. It provides the longest support path for security updates. 

Unless you enjoy the instability risk caused by always changing things on the server.

---

### Post by nandemonai on 2009-04-20
+1 for LTS.

Numerous reasons for doing so. Longer lifespan, more stable etc.

---

### Post by ugm6hr on 2009-04-20
Consider having to upgrade your server every 6 months; it is better to stick with LTS releases, and just upgrade every 2 years.

While Jaunty will be supported for 18 months, the upgrade path is designed to go through every release.  LTS releases have a direct LTS to LTS upgrade path (and are supported for 5 years).

---

### Post by Thirtysixway on 2009-04-20
Go with hardy, 8.04 since it's LTS.

---

