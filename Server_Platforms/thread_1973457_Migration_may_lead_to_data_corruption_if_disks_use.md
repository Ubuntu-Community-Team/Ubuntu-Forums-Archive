---
title: "Migration may lead to data corruption if disks use cache != none"
date: 2012-05-04
forum: Server Platforms
---

### Post by azzamite on 2012-05-04
While trying to do live migration with libvirt from one host to another I'm getting this error message:
> error: Unsafe migration: Migration may lead to data corruption if disks use cache != none
Trying to follow the error I got to [this page]("http://www.redhat.com/archives/libvir-list/2012-February/msg00927.html").

There it says something about VIR_MIGRATE_UNSAFE, but I don't find where to enable that option.

Also, the images are stored in a **replicated glusterfs** directory, I haven't been able to find if there is a way to disable such "cache" to 0, I tried setting this options to 0:
performance.cache-[ max | min ]-file-size

Tried seting performance.cache-size to 0 but it fails with:
```
gluster volume set hogar performance.cache-size 0
'0' in 'option cache-size 0' is out of range [4194304 - 6442450944]
Set volume unsuccessful
```
And still I'm getting that unsafe migration error.

Any ideas?

---

