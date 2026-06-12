---
title: "Backuppc. Corrupt XferLOG.z file"
date: 2022-10-24
forum: Server Platforms
---

### Post by RichardA on 2022-10-24
I have an Ubuntu server running backuppc in an LXC container, backing up two Ubuntu clients. This has worked reliably for years,  but now backups don't complete for either client.
If I use BackupPC_zcat to read XferLOG.z the file starts with file paths, but then changes to either binary or corrupt data (it's hard to tell which). The backup never completes, and  the log file grows to multiple GB.
Has anyone else seen this?

---

