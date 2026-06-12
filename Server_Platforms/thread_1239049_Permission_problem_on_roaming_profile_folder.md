---
title: "Permission problem on roaming profile folder"
date: 2009-08-13
forum: Server Platforms
---

### Post by jbcola on 2009-08-13
Hello,

I have been running an Ubuntu Server PDC 8:04 , with 10 XP workstations using it, now I wanted to upgrade the server and to the 64 bit version  and to put it an a new hardware platform.
However, on the new installation, the server-side profiles could not be loaded, i receive an error message "Profile could not be loaded because of invalid user rights on the profile folder", on the old server this worked without any problem.
I have also taken over the domain SID, so that the clients do not need to register again.

After the logon (only with the local profile) I have access to the "profile" folder (and all other shares), and it is writable.

On the XP clients I get the following message explaing that the server-side version of the profile folder has not the correct permissions, it should be owned by the user, and the Admin should have access to it.

The permissions of the "profile" folder are appended.
I thing there's something wrong with the samba group mappings, i've tried some changes , but without success (net groupmapp ....)

Somebody has an idea why the server-side profile does not work?

Thank you for your help, i tryed everything, and it simply does not work ....

Best regards,
Jean-Luc

---

### Post by jbcola on 2009-09-09
Solved !!!
The "logon path" was missing in the smb.conf, the default value did not work anymore...
(Only for the home share ....)

---

### Post by whoop on 2009-11-07
Did you follow any tutorial setting this up?

---

### Post by jbcola on 2009-11-07
Yes, but do not remember which one (8.04 was setup some time ago ...)

But the same settings on the 32bit instance of Samba worked fine.
Maybe a default value has changed between thoses 2 versions ...

JL

---

