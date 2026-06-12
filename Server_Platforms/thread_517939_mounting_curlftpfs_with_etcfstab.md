---
title: "mounting curlftpfs with /etc/fstab"
date: 2007-08-05
forum: Server Platforms
---

### Post by etechship on 2007-08-05
Here is my /etc/fstab file. I try differant things, then do mount -l to see if i was able to mount it. 

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
curlftpfs#*user:pass*@ucstreaming.officewebsiteonline.com  /usr/lib/red5/webapps/oflaDemo/streams fuse rw,uid=500,user,noauto 0 0





```

---

### Post by murmel on 2008-01-23
I can't get it to work..
```
curlftpfs#user:***@my.domain.com /mnt/mydomaincom fuse rw,uid=500,user,noauto 0 0
```

---

### Post by etechship on 2008-01-23
Make sure that your uid is correct (that is the user id)

Try to connect to the ftp server regualrly and see if you have any problems. 

dave

---

### Post by jrib on 2008-02-03
you'll also need the "allow_other" option or else only root will be able to view it when it is mounted

---

