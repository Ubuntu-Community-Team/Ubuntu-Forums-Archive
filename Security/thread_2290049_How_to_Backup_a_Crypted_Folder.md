---
title: "How to Backup a Crypted Folder ?"
date: 2015-08-08
forum: Security
---

### Post by raffaele8 on 2015-08-08
I use "backup in time" and gnome encfs manager.

When the folder is decrypted the backup save the folder, but all the file are visible in backup destination directory?

When the folder was locked, Backup in time save the folder?

I see it save an empty folder.



thank you

---

### Post by TheFu on 2015-08-09
encfs only descrypts when logged in. That is the only way you will backup "files."

You can backup the blob of encrypted bits, but that is less useful.

I think you mean "back in time" - the way that system works, you should only backup files, not blobs. If you want to secure the backup area, you'll need to encrypt that and lock down the permissions.  There are as many different ways to backup systems as there are people and systems. I think you'd be happier with whole drive encryption - at least for the backup storage.  Setting this up after install is non-trivial. There is no GUI for it.

---

