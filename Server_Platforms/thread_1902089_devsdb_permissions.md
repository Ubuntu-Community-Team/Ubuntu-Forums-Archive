---
title: "/dev/sdb permissions"
date: 2011-12-29
forum: Server Platforms
---

### Post by grogling on 2011-12-29
Hi All,

I am having a bit of trouble getting virtualbox to access a raw disk. I have set everything up, but it seems that my raw disk /dev/sdb keeps reverting back to normal permissions rather then the ones I have set every couple of minutes.

I have used the command "chmod 777 /dev/sdb" which works for a short time, but then I get errors, and when checking it goes back to this:
brw-rw----  1 root disk        8,  16 2011-12-30 14:19 sdb

After a bit of searching, it seems I may need to setup a udev rule, but am stumped on how to do this, can anybody advise how to setup a udev rule to keep the permissions of this device public?

Glen

---

