---
title: "Disk failure alert"
date: 2009-08-04
forum: Server Platforms
---

### Post by any.linux12 on 2009-08-04
Hi!

Hi have a hp server proliant 365 with raid 5 (3 disks) and I bought now a 4th just in case it crashes but I'm never in the server room and at the moment the only thing that tells me that the disks are ok are the leds. I would like to write a script to send me an e-mail alert (for ex.) in case one disk crashes.

I know how to write the e-mail script but I don't how to check the hard drives condition.

Any help??

---

### Post by fahadsadah on 2009-08-04
You're looking for SMART, the Self Monitoring and Reporting Technology.
A nice article about it [can be found here]("http://www.linuxjournal.com/article/6983").

---

