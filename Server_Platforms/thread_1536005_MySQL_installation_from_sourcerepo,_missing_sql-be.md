---
title: "MySQL installation from source/repo, missing sql-bench"
date: 2010-07-21
forum: Server Platforms
---

### Post by isri on 2010-07-21
Hello,

I need to make some tests of MySQL. Till now I was using sql-bench. It was available in earlier in MySQL 5.0. Now only MySQL 5.1 is available (on 10.04) and sql-bench seems to be missing.

I was trying to build it from source (with apt-get source mysql-server and dpkg-buildpackage -b). Inside source directory I can find sql-bench folder with sources). Compilation and installation was done sucessful but sql-bench folder with benchmark scripts is still missing...

./configure --help doesn't contain information about sql-bench so as I understand this is default option.

Thanks,
Regards

---

