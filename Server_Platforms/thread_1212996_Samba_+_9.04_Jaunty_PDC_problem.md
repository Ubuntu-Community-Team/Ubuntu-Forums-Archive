---
title: "Samba + 9.04 Jaunty PDC problem"
date: 2009-07-14
forum: Server Platforms
---

### Post by ingcabral on 2009-07-14
Hi guys,

I wonder if you ever had this problem. I'm using 9.04 as a PDC and fileserver.
All of the windows clients have mainly one issue: If they create a file or folder (or rename it), they have to refresh the screen in order to see the changes. We migrated from a windows server and, of course, this didn't happen, so I'm getting the complains because of that.
And also I have one more thing: Sometimes, folders or files created inside this shares are not created at all. I've seen the logs and don't see anything strange but this, which happened yesterday at the same time the user told me that happened again:

root@arfilesvr01:/var/log/samba# tail log.guillermo01.old
[2009/06/24 18:17:13,  0] smbd/service.c:make_connection(1284)
  guillermo01 (192.168.1.86) couldn't find service archivo
[2009/06/24 18:17:13,  0] param/loadparm.c:process_usershare_file(8322)
  process_usershare_file: stat of /var/lib/samba/usershares/archivo failed. Permission denied
[2009/06/24 18:17:13,  0] param/loadparm.c:process_usershare_file(8322)
  process_usershare_file: stat of /var/lib/samba/usershares/archivo failed. No such file or directory
[2009/06/24 18:17:13,  0] smbd/service.c:make_connection(1284)
  guillermo01 (192.168.1.86) couldn't find service archivo
[2009/06/24 18:17:13,  0] param/loadparm.c:process_usershare_file(8322)
  process_usershare_file: stat of /var/lib/samba/usershares/archivo failed. Permission denied

Of course file /archivo doesn't exist, but how come samba is searching for a service when the client is asking for creating a file?

I'll post my smb.conf if you need it

Thanks in advance,

Ariel

---

