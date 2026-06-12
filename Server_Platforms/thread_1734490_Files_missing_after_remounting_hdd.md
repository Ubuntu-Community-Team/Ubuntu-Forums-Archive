---
title: "Files missing after remounting hdd"
date: 2011-04-20
forum: Server Platforms
---

### Post by nbrochu on 2011-04-20
Hello i am running 10.10 server. i shut down the server to install a new hard drive for backups. When i remounted the drives and restarted the shares, About 10 very important files were missing. The rest of the data on the share is fine. Any ideas on what could cause this issue?

---

### Post by nbrochu on 2011-04-20
After some digging, i found teo of the files but they have .~lock. before the file name. What is a .~lock. file?

---

### Post by dtfinch on 2011-04-20
OpenOffice creates ".~lock." files to indicate that somebody has the file open, so that one person doesn't mistakenly overwrite another's changes, and unless there is a crash or something, typically deletes them when the file is closed.

If these were relatively new files, and if there's a chance that one of the drives wasn't mounted when they were saved, you could try unmounting the drive (or look into mount --bind if unmounting isn't a good option) to see if they were saved directly in the mount point folder, which would have been hidden once the drive was mounted. It seems like a long shot though, since it'd be hard not to notice an empty share when saving to it.

If these are all OpenOffice documents, you could try looking at local backups it might have made. On mine at work (LibreOffice on XP) for example, there's backups of the last 20 documents I've saved in "C:\Documents and Settings\davidf\Application Data\LibreOffice\3\user\backup".

---

