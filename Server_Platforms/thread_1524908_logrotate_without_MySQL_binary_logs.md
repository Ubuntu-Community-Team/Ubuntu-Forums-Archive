---
title: "logrotate without MySQL binary logs"
date: 2010-07-05
forum: Server Platforms
---

### Post by Jyunhao on 2010-07-05
I set up a 10.04 server and found that logrotate close MySQL's current binary log and open new one at 6:25 every day.

But I use mysql-zrm to backup my DB in MySQL remotely and incrementally, which also close and open binary logs.

It's more reasonable to have only one binary log a day, closed and opened during backup.

Is there a way to configure logrotate to leave MySQL's binary log alone?

---

