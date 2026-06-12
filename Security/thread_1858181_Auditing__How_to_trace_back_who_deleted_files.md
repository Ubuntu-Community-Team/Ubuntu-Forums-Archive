---
title: "Auditing : How to trace back who deleted files?"
date: 2011-10-11
forum: Security
---

### Post by phil4000n on 2011-10-11
Config:
C: Windows 7 x64bits with multi-users account, only one account with admin priviledges
D: Data partition (NTFS)

Problem
All the data(files and up to root directory) have been erased from D, except those with admin access (me.)
The guilty user claims that it's virus.

How can I verify that the delete command was launch or it's a virus (I do not believe it, but in the meantime I check with a 2nd anti-virus)

Of course, I don't want to boot now under Win7 ([https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery))

Thanks

---

### Post by Dangertux on 2011-10-11
> **phil4000n said:**
> Config:
C: Windows 7 x64bits with multi-users account, only one account with admin priviledges
D: Data partition (NTFS)

Problem
All the data(files and up to root directory) have been erased from D, except those with admin access (me.)
The guilty user claims that it's virus.
[http://www.microsoft.com/technet/security/prodtech/windows2000/w2kccadm/localpol/w2kadm11.mspx](http://www.microsoft.com/technet/security/prodtech/windows2000/w2kccadm/localpol/w2kadm11.mspx)
How can I verify that the delete command was launch or it's a virus (I do not believe it, but in the meantime I check with a 2nd anti-virus)

Of course, I don't want to boot now under Win7 ([https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery))

Thanks

Unfortunately , unless you took a few steps before this happened. You may be out of luck. Windows logging is not as robust as Linux/Unix logging.

If you did not set up File Access auditing under User Manager > policies. Then there will not likely be a log of the command.


If you did have File Access auditing set up previously you can view the events under Administrative Tools > Event Viewer > Log > Security

Hope this helps :-/

Also if it was a virus : it will likely show the deletion performed by the UID the virus was running as.

---

### Post by phil4000n on 2011-10-11
> If you did have File Access auditing set up previously you can view the events under Administrative Tools > Event Viewer > Log > Security
Haven't check yet.
But if it was on, how can access it through Linux?

---

### Post by Dangertux on 2011-10-11
> **phil4000n said:**
> Haven't check yet.
But if it was on, how can access it through Linux?

By default it will either be stored in C:\Windows\System32\Config or C:\Windows\System32\winevt\logs

If you were not using full drive encryption you should be able to mount the partition under Ubuntu and snag those files, they are simply XML files, so you should be able to read them with little effort without them being in event viewer.

Hope that helps.

---

