---
title: "[Samba] NT_STATUS_UNSUCCESSFUL when add Root"
date: 2009-06-18
forum: Server Platforms
---

### Post by Francesco89 on 2009-06-18
Hi, I'm making a domain with samba on my Ubuntu Desktop 8.04 server.
Everything seems ok in the config file, I've followed this how to [http://openskill.info/infobox.php?ID=552](http://openskill.info/infobox.php?ID=552), but when I try to add root at samba's users I have this error:

root@server:~# smbpasswd -a root
New SMB password:
Retype new SMB password:
Unable to modify TDB passwd: NT_STATUS_UNSUCCESSFUL!
Failed to add entry for user root.
Failed to modify password entry for user root

I've tried both with samba running and stopped..but the error is the same.

Thanks, Francesco

---

