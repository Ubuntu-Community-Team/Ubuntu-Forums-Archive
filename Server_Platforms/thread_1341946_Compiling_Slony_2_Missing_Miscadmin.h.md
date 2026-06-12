---
title: "Compiling Slony 2 Missing Miscadmin.h"
date: 2009-11-30
forum: Server Platforms
---

### Post by user2037 on 2009-11-30
Installing Slony 2 fails with "error: miscadmin.h: No such file or directory" and many similar errors.

Is there a dependency missing?

Apt-get build-dep slony1 appears to depend upon "postgresql-server-dev-8.3".

Any ideas how to compile and install for Postgresql 8.4 on Ubuntu 9.10?

EDIT: Apparently one must install "postgresql-server-dev-8.4". It appears to be a bug in the Slony packaging dependencies since Pg 8.4 is now the 'stable' version in Ubuntu 9.10.

---

