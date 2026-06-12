---
title: "slow mysql, help!"
date: 2007-05-02
forum: Server Platforms
---

### Post by 5hundy on 2007-05-02
I have 3 boxes, each running Feisty. All of them are AMD64, one
of them is in 32b mode, other two are 64b mode. All have the same
filesystem type, and roughly the same hardware config. Each has the ruby
mysql gem installed.

I have a script that fills a database with random data for testing. Its
mainly a lot of inserts and takes about 30 to run on 2 of the boxes. On
one of them (a 64b mode machine) it uses *very little CPU* and takes
FOREVER to run. I benchmarked the disk and its faster than the other HDs
(this was done with repeated writes to a sqlite db), however this
machine is the only one with a raid configuration.

Can anyone think of anything I should check out to fix this problem?

Thanks!!

---

