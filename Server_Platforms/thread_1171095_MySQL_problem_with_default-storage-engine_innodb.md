---
title: "MySQL problem with default-storage-engine innodb"
date: 2009-05-27
forum: Server Platforms
---

### Post by ashleym1972 on 2009-05-27
I've set two Ubuntu servers with MySQL and am trying to run them as a simple master slave with InnoDB as the default storage engine. I over came the problem with the ib* files hosing InnoDB so it is no longer disabled, but now MySQL will not change the default storage engine. I can set default-storage-engine=memory or innodb but show engines; always shows myisam as default.

What gives? Do I need to just dump the apt package and compile MySQL for myself? I don't understand why something that should be so simple is so complicated. I also don't understand why this doesn't just work. Is replication getting in the way?

---

