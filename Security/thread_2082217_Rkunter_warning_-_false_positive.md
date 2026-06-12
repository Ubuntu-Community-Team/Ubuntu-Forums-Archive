---
title: "Rkunter warning - false positive?"
date: 2012-11-08
forum: Security
---

### Post by zozza on 2012-11-08
I just ran a rkhunter session and noticed several entries like this:

Warning: The file properties have changed:
[21:13:28]          File: /bin/kill
[21:13:28]          Current hash: cfb465a12b8631d37bcedaf1666190981b313c1d
[21:13:28]          Stored hash : 2526f22ed8a7cd7a967ca4dda75938083ab31557
[21:13:28]          Current inode: 4237170    Stored inode: 4235324
[21:13:28]          Current file modification time: 1342492315 (17-Jul-2012 03:31:55)
[21:13:28]          Stored file modification time : 1260992081 (16-Dec-2009 19:34:41)

Does this actually mean anything?

Thanks.

---

### Post by OpSecShellshock on 2012-11-08
It means that the file changed between the last time rkhunter was run and the time that you ran it again. That could happen because of a software update or a version upgrade, particularly if there was a three year gap.

Every time you do a software update or version upgrade you should run rkhunter right after in order to calibrate it to the current state of the system.

---

