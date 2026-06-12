---
title: "is the adduser manpage correct"
date: 2010-11-01
forum: Server Platforms
---

### Post by david3d on 2010-11-01
Before I file a bug against this can someone else please verify this on 10.04.

The [manpage]("http://manpages.ubuntu.com/manpages/lucid/man8/adduser.8.html") seems to be missing all single letter flags that adduser -h lists.  It also seems to list a bunch of options that aren't supported by adduser, unless I'm doing something wrong.  For instance --conf FILE doesn't seem to work.  I get an error back saying "unrecognized option '--conf'"

---

### Post by david3d on 2010-11-01
Doh...the problem is adduser != useradd.  Must need more coffee today.

---

