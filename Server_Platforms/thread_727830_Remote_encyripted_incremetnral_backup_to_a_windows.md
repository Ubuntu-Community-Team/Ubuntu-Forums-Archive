---
title: "Remote encyripted incremetnral backup to a windows machine"
date: 2008-03-18
forum: Server Platforms
---

### Post by ulver on 2008-03-18
Hi, I`m using rsnapshot backup on a local server to backup files mostly from windows clients. It works just fine, but I have to figure out how to send every  weekly update (week0) to a windows machine and do incremental backups every week there (sort like a backup for my backup).
Any tip in a right direction would be appriciated

---

### Post by HermanAB on 2008-03-18
Cygwin with OpenSSH and Rsync on Windows is likely the answer.

---

