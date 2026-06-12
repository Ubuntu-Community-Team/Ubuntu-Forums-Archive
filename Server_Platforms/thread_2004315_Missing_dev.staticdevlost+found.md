---
title: "Missing /dev/.static/dev/lost+found"
date: 2012-06-15
forum: Server Platforms
---

### Post by ejain on 2012-06-15
Since doing an upgrade from 10.04 to 12.04, 
I get the following mail every day; not sure what to do about it:

> Subject: Cron <root@test> test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )

/etc/cron.daily/standard:

Some local file systems lack a lost+found directory. This means if the
file system is damaged and needs to be repaired, fsck will not have
anywhere to put stray files for recovery. You should consider creating
a lost+found directory with mklost+found(8).

The following lost+found directories were not available:

/dev/.static/dev/lost+found


---

### Post by rfay on 2012-12-28
Yes, I have this after an upgrade from 10.04 to 12.04 also.

It's odd because /dev/.static shouldn't be its own filesystem, right? And why should it have a lost+found?

It looks to me like /dev/.static was removed per [https://lists.ubuntu.com/archives/ubuntu-devel/2009-January/027184.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-January/027184.html), so perhaps this is just legacy stuff hanging around.

---

