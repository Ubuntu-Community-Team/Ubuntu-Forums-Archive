---
title: "Samba with winbind saving files with incorrect permissions (samba 3.0.24)"
date: 2007-08-10
forum: Server Platforms
---

### Post by nbaldridge on 2007-08-10
Hello forums-goers,
  I have a couple of rogue samba shares that have started acting up since I migrated our ldapsam PDC to another machine running Ubuntu Feisty (samba 3.0.24).

It seems that a specific user, whenever she saves files to a particular share, will cause the samba panic action to be fired off (sending me an email).  This panic action can be caused by viewing one of those files' permissions in the Windows permissions viewer as well.

The issue is that the files written need to be accessible to an entire group (read and write), as well as read and write for the owner of the files.  Samba (or the OS) is saving them with 700 permissions (read ,write, and execute for owner only).
I have tried everything to correct this behavior, even going as far as to force the permissions on the share to 0770, but this has not corrected the problem.

Below please see the share definition in question:

[paperless]
   path = /paperless/file_room/
   public = no
   browsable = yes
   writable = yes
   directory mask = 0770
   create mask = 0770
   security mask = 0770
   directory security mask = 0770
   force create mode = 0770
   valid users = @FOO.BAR\"Domain Users"

Thank you for your time,
-Nick

---

