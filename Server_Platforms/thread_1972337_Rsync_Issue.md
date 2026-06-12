---
title: "Rsync Issue"
date: 2012-05-03
forum: Server Platforms
---

### Post by AvidElite on 2012-05-03
I'm using Rsync to move files from a remote computer (running the rsync daemon), but I need to have everything, files and folders, on the sender be removed if the transfer was successful.  This is the command I'm using:

rsync -rlpEthSWog --progress --stats --update --remove-source-files --password-file=/server/rsync-batchpass rsync://yamada@10.0.0.2/outbox/ /server/raid/inbox/

It seems like other people have had issues with rsync only deleting files in my Google searches, but the solution they found was to run "rm -fr ./" on the source directory.  In my case that's not an option since I don't have access to a shell on the sender.

Anyone have any ideas?

---

### Post by PCloutier on 2012-05-03
You can try --delete-after to do any file level cleanup.

---

### Post by AvidElite on 2012-05-03
Thanks, but --delete-after has the receiver delete files that were not part of the transfer.  I need the sender to delete files after the transfer.

---

