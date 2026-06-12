---
title: "fstab - super karamba - kde resource display"
date: 2007-02-24
forum: Server Platforms
---

### Post by huggy77 on 2007-02-24
i cannot get any of the superkarumba widgets to pick up my second drive...  i am not sure what to do...  not even what info to post..

everything else works great!

the widget is:
[http://www.kde-look.org/content/show.php?content=52038](http://www.kde-look.org/content/show.php?content=52038)

my fstab looks like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=b02c9316-741b-4fae-8e91-13beedfa3884 / ext3 nouser,defaults,errors=remount-ro,usrquota,grpquota,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda5
UUID=29544d34-5032-4804-bbeb-ca7fe2d4a82b none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdb5 /data xfs nouser,defaults,errors=remount-ro,usrquota,grpquota,atime,auto,rw,dev,exec,suid 0 1

```

any help will be appareciated!

---

