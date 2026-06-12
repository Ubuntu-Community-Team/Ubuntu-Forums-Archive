---
title: "Synchronize Utility?"
date: 2008-03-14
forum: Windows
---

### Post by hyper_ch on 2008-03-14
Any recommendation for a good synchronize utility for windows (free of charge and if possible also free as in free speech ^^)

---

### Post by michaelzap on 2008-03-14
I used to use [SyncToy]("http://www.microsoft.com/downloads/details.aspx?FamilyId=E0FC1154-C975-4814-9649-CCE41AF06EB7&displaylang=en") (works a lot like Grsync).

---

### Post by dca on 2008-03-14
Depends.  I've consulted for some organizations that would have Samba shares on a Linux box.  In each share is a symlink to Rsync...  On each Windows user workstation is a PHP script that includes the command to run rsync and all you see on the client terminal is a DOS window popping up indicating building file list and you see it matching up the data.  You throw a batch file calling the PHP or Perl or whatever script into the Windows automatic task scheduler and you're done.
 
You can even throw in a Windows shutdown command if you wanted to run the tool later at night...

---

### Post by rickyjones on 2008-03-14
I've been using Alway Sync ([http://allwaysync.com/](http://allwaysync.com/)) for a while now and I recommend it. I believe you can script it pretty easily. Great for synchronization. You can also have it run in the system tray and monitor for file changes. When detected it will automatically synchronize the files.

-Richard

---

### Post by digital_exhaust on 2008-03-14
> **michaelzap said:**
> I used to use [SyncToy]("http://www.microsoft.com/downloads/details.aspx?FamilyId=E0FC1154-C975-4814-9649-CCE41AF06EB7&displaylang=en") (works a lot like Grsync).

Yep... works really well..

---

### Post by hyper_ch on 2008-03-14
downloaded synctoy now, but haven't had a chance yet to look at it :) thx for the suggestions

---

