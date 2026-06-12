---
title: "vsftpd: refusing to run with writable anonymous root"
date: 2009-12-12
forum: Server Platforms
---

### Post by aajax on 2009-12-12
According to the manpage for vsftpd.conf there are settings that can be used to allow anonymous users to upload files.  These for example -

anonymous_enable=YES
write_enable=YES
anon_upload_enable=YES

However, setting the above parameters results in the subject error message when the anonymous user tries to logon to the server.

By removing the write permissions to the ftp root directory the user can logon successfully.  However, they receive access permission errors when attempting to upload as would be expected.  If I change the permissions on the ftp root directory after the anonymous user is logged on (i.e., bypass the logon error) it works fine.  However, this is not very handy and one would think is not what is intended when you specify anon_upload_enable=YES.

I'd be grateful to anyone who can explain how to get anon_upload_enable=YES to work.

---

