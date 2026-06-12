---
title: "&quot;multiraid doesn't exist&quot; using partman-auto-raid"
date: 2008-08-13
forum: Server Platforms
---

### Post by dioktos on 2008-08-13
Attempting to preseed an automated hardy installation with a RAID partman recipe fails. The recipe is:
```
d-i partman-auto/expert_recipe string \
        multiraid :: \
                2048 2048 2048 raid $primary{ } method{ raid } . \
                10240 1000000000 1000000000 raid method{ raid } .
d-i partman-auto-raid/recipe string \
        1 2 0 swap - /dev/sda1#/dev/sdb1 . \
        1 2 0 ext3 / /dev/sda2#/dev/sdb2 .
```
And the error in the installer syslog looks like this:
```
Aug 13 17:14:13 debconf: --> GET partman-auto/method
Aug 13 17:14:13 debconf: <-- 0 raid
Aug 13 17:14:13 debconf: --> GET partman-auto/disk
Aug 13 17:14:13 debconf: <-- 0 /dev/sda /dev/sdb
Aug 13 17:14:14 debconf: --> METAGET partman/text/scsi_disk description
Aug 13 17:14:14 debconf: <-- 0 SCSI%s (%s,%s,%s) (%s)
Aug 13 17:14:14 debconf: --> GET partman-auto/expert_recipe
Aug 13 17:14:14 debconf: <-- 0 multiraid :: 2048 2048 2048 raid $primary{ } method{ raid } . 10240 1000000000 1000000000 raid method{ raid } .
Aug 13 17:14:14 debconf: --> SET partman-auto/expert_recipe_file /tmp/expert_recipe
Aug 13 17:14:14 debconf: <-- 0 value set
Aug 13 17:14:14 debconf: --> GET partman-auto/expert_recipe_file
Aug 13 17:14:14 debconf: <-- 0 /tmp/expert_recipe
Aug 13 17:14:14 debconf: --> METAGET multiraid description
Aug 13 17:14:14 debconf: <-- 10 multiraid doesn't exist
Aug 13 17:14:14 partman-auto: Expert recipe too large (12288 > 5368); skipping

```
partman-auto-raid exists as a package: is there something special I need to do to pull it into the ubuntu-installer?

Edited: I missed [this earlier thread]("http://ubuntuforums.org/showthread.php?t=403168"), but since I can't add to it, consider this a continuation of it.

---

