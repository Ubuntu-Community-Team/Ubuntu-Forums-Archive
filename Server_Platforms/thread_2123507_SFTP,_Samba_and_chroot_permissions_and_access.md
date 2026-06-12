---
title: "SFTP, Samba and chroot permissions and access"
date: 2013-03-08
forum: Server Platforms
---

### Post by mpasmith on 2013-03-08
Hello,

I have a need for a certain setup using samba and chrooted sftp.

I have a set of directories shared by Samba where a server places output files into a them...it runs
as a batch job against client directories.  That I can get to work.

However, the complication comes that clients need to sftp into their directory to retreive the outputs, 
this is done automatically by the clients own procedures.  For security I obviously need the login to be
chrooted and stop movement up the directory tree.

With the permissions required by sftp, Samba can no longer access the directory.

Is there a way I can get round this?

Everything is going to be automated and more users added over time, so I would like to keep it simple.

Thanks

---

