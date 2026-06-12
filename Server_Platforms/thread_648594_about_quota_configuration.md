---
title: "? about quota configuration"
date: 2007-12-23
forum: Server Platforms
---

### Post by Freesprt30 on 2007-12-23
Ok I am building a server using this guide [http://www.howtoforge.com/perfect_server_ubuntu7.10_p4](http://www.howtoforge.com/perfect_server_ubuntu7.10_p4)

  This is what my quota Config looks like I am not sure how I am suppose to configure it.  Does anyone know if this looks right.

# /etc/fstab: static file system information.
## /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=efe03e30-1d4d-4528-9a01-429539d7834a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=a452eb47-d992-4722-836d-bb4c582087db /usr            ext3    defaults        0       2
# /dev/hda5
UUID=1f9f1603-ca80-4a7b-ab82-e31aaaca210b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


  I am using this serve for a webpage/forum, and file hosting.

 Thanks in  advance

---

### Post by Freesprt30 on 2007-12-23
I did some research and I think this is right can anyone confirm.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=efe03e30-1d4d-4528-9a01-429539d7834a /               ext3    defaults,errors=remount-ro,usrquota, grpquota 0       1
# /dev/hdb1
UUID=a452eb47-d992-4722-836d-bb4c582087db /usr            ext3    defaults,usrquota, grpquota  0       2
# /dev/hda5
UUID=1f9f1603-ca80-4a7b-ab82-e31aaaca210b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by Freesprt30 on 2007-12-24
OK I think I almost got it this is my last rsults
root@rose:/home/bill# quotaon -avug
/dev/hda1 [/]: group quotas turned on
/dev/hda1 [/]: user quotas turned on


  But I didn't and can't get hdb1turned on?

---

