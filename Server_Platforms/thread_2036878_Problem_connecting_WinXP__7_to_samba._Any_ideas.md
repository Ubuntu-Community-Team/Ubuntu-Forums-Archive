---
title: "Problem connecting WinXP / 7 to samba. Any ideas?"
date: 2012-08-03
forum: Server Platforms
---

### Post by radiognome on 2012-08-03
I have a couple of Ubuntu 10.04 servers running Samba to share a directory or two.

My ubuntu desktop connects happily to all of them, and so do all OS-X Feline entities.
So far so good.

On Windows XP and 7 most of those servers are found nicely in WinExplorer. Only one Samba-Server provokes errors on Windows, complaining the server is not accessible, account is not allowed to connect / system error 1240 and such.

All smb.conf files are practically the same, only the paths to the shares differ. All user-rights and groups are the same on the shared directories. Only on the 'error-provoking one' the shared directories are mountpoints for partitions.

I use the following authentication settings in smb.conf, which for years have enabled me to connect to a samba-share with any username/password whatsoever.

```

# Some security lines from my smb.conf
   security = SHARE
   auth methods = guest

   encrypt passwords = true

   passdb backend = tdbsam

   obey pam restrictions = yes

   guest account = shareusers
   invalid users = root

```

I am running out of ideas to google... Any suggestions?

Kind regards,

Martin

---

### Post by kevinthecomputerguy on 2012-08-03
does it work via IP address?

are the client computers in the same workgroup?

do the client computers have a password? most sharing is disabled when the windows accounts dont have passwords.

---

