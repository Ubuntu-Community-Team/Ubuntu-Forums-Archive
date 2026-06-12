---
title: "TDB Error When Adding New SMB User using Smbpasswd"
date: 2008-03-28
forum: Server Platforms
---

### Post by hevfuture on 2008-03-28
Hello,

I am running Ubuntu Server 7.10. 

When I add a new samba user using the smbpasswd command (smbpasswd -a sample_username), I get the following error:
_____________

Unable to modify TDB passwd ! Error: Record exists
 occurred while storing the RID index (RID_                 )
Failed to add entry for user sample_username.
Failed to modify password entry for user sample_username.
_____________

Does anyone know of any solutions to this error?  

I have rebooted several times and also searched on Google, but the only proposed solution has been to reinstall the server. Is there any way to repair just the tdb file, or just samba?


Any feedback is appreciated. Thanks!

---

### Post by cdenley on 2008-03-28
Are you sure the user doesn't already exist?
```

sudo pdbedit -L sample_username

```

---

