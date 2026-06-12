---
title: "/var/log/samba/log.computername"
date: 2009-01-03
forum: Server Platforms
---

### Post by Zip247 on 2009-01-03
was checking my samba logs on my file server and do not understand the following.
```
[2009/01/03 02:15:05, 0] smbd/service.c:make_connection(1191)
  familyroom (192.168.1.4) couldn't find service serverdocs.com
[2009/01/03 02:15:05, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/serverdocs.com failed. No such file or directory
[2009/01/03 02:15:05, 0] smbd/service.c:make_connection(1191)
  familyroom (192.168.1.4) couldn't find service serverdocs.com
[2009/01/03 02:15:05, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/serverdocs.pif failed. Permission denied
[2009/01/03 02:15:05, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/serverdocs.pif failed. No such file or directory
[2009/01/03 02:15:05, 0] smbd/service.c:make_connection(1191)
  familyroom (192.168.1.4) couldn't find service serverdocs.pif
[2009/01/03 02:15:05, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/serverdocs.pif failed. No such file or directory
[2009/01/03 02:15:05, 0] smbd/service.c:make_connection(1191)
  familyroom (192.168.1.4) couldn't find service serverdocs.pif
[2009/01/03 02:15:05, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/serverdocs.lnk failed. Permission denied
[2009/01/03 02:15:05, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/serverdocs.lnk failed. No such file or directory
[2009/01/03 02:15:05, 0] smbd/service.c:make_connection(1191)
  familyroom (192.168.1.4) couldn't find service serverdocs.lnk
[2009/01/03 02:15:05, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/serverdocs.lnk failed. No such file or directory
[2009/01/03 02:15:05, 0] smbd/service.c:make_connection(1191)
  familyroom (192.168.1.4) couldn't find service serverdocs.lnk
[2009/01/03 02:15:16, 1] smbd/service.c:close_cnum(1230)

```

familyroom is the name of my kids vista puter.  No one was logged in at the time this was going on.  

Could someone tell me what this means.

Thx
wdecker

---

