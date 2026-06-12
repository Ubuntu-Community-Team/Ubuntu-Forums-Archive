---
title: "Samba Password Changes"
date: 2009-03-30
forum: Server Platforms
---

### Post by damo12 on 2009-03-30
I run a server for a small business (Ubuntu Server 8.04, accessed through Webmin and Putty).

The server is used as a file server with various shares accessed from Windows machines through Samba.  Every now and then, the Samba password changes for no apparent reason.  Resetting the password using the command "sudo smbpasswd -a username" resets the password and everything works fine again.

The user account has the same password as the samba password (not the most secure I know but it works in this environment) although in Webmin the password automatically encrypts itself.

In smb.conf the "unix password sync" is set to yes.  Resetting the samba password resolves the problem and there is no need to reset the unix password.

Thanks in advance.

---

