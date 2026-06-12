---
title: "fstab errors"
date: 2007-04-18
forum: Server Platforms
---

### Post by sickdude on 2007-04-18
Ok guys i had a lot of trouble with my server lately, and i thought that it was the fault of old hard disks. But when i fresh installed today i found out something, something wierd.

I got some errors that had to do something with the uuid in my fstab, that ubuntu generates itself.

```


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
#UUID=d0542f19-9b2b-41c9-a0dc-dcfb5f261018 /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd1
/dev/hdd1 /back-up        ext3    defaults        0       2
#UUID=85ce492c-7b6d-3b26-df63-c1fff9827291 /back-up        ext3    defaults        0       2
# /dev/hda4
/dev/hda4 /home           ext3    defaults        0       2
#UUID=19953a19-c53e-4627-9ec0-f9c72b61f80e /home           ext3    defaults        0       2
# /dev/hda3
/dev/hda3 /var            ext3    defaults        0       2
# /dev/hda3
#UUID=f55c03b9-ed3e-48b7-b9be-68be2b566da6 /var            ext3    defaults        0       2
# /dev/hda1
/dev/hda1 none            swap    sw              0       0
#UUID=91b6c74b-6981-436a-b083-83d31cfd6d4a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


```

As you can see i hased out the entrys with the uuid and replaced them with the standard thingies. This seems to do the trick but i was wondering if this is a bug or just a known error? And ofcourse im wondering if this is the right way to fix this?

---

### Post by gaten on 2007-04-21
I also had a problem with UUIDs. In my case, for some reason Ubuntu didn't generate the complete UUID for one of my drives and therefor couldn't mount it. I used the command```
 sudo vol_id -u device
``` to find out the correct UUID of my device, now everything works great. Donno if that helped, but there ya go :P

---

### Post by sickdude on 2007-05-01
Thnx for the info dude :)

---

