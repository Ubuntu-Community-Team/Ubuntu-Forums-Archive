---
title: "Files not syncing..."
date: 2010-01-02
forum: Ubuntu One (CLOSED)
---

### Post by Cuco3 on 2010-01-02
Is there a way to manually force sync files? My files have not synced over a day and there's an "unsynchronized" emblem appearing over the Ubuntu One folder. The web interface for Ubuntu doesn't display the proper total size of Ubuntu One nor the current files/folders.

---

### Post by James Henstridge on 2010-01-04
Hi Cuco3,

You should be able to trigger a full synchronisation by disconnecting and reconnecting to U1.  This should be possible via the button in the file manager shown when browsing the Ubuntu One folder, or through the icon on the panel.

If that doesn't help, there might be some pointer to the problem in the log files (found in ~/.cache/ubuntuone/log).  In particular, the last few lines of syncdaemon.log.

---

