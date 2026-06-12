---
title: "Handling file checksums for backup/restore"
date: 2023-03-30
forum: Windows
---

### Post by Rooster2000 on 2023-03-30
As a part of taking backup on my spouses Windows 11 computer with EaseUS Todo Backup Free, I wish to do something similar I am doing on my LM 21 for checking file hashes before backing them up.

```
~$ find -P /home/dir -type f -exec sha256sum {} \; > sha256sums.txt
```

And then would like to check the file integrity somewhat similarly also.

```
~$ sha256sum -c sha256sums.txt
```

I only found a way to do it for single file, and Windows command prompt examples and tutorials are a bit scarce. Or are they called Windows Powershell scripts?

```
certutil -hashfile c:\temp\myfile.txt SHA256
```

Or would there be some better or easier way to ensure file integrity after restoring them?

---

### Post by SeijiSensei on 2023-03-30
Use [rsync]("https://linux.die.net/man/1/rsync"). 

> rsync always uses checksums to verify that a file was transferred correctly. If the destination file already exists, rsync may skip updating the file if the modification time and size match the source file, but if rsync decides that data need to be transferred, checksums are always used on the data transferred between the sending and receiving rsync processes. This verifies that the data received are the same as the data sent with high probability, without the heavy overhead of a byte-level comparison over the network.

[https://unix.stackexchange.com/questions/30970/does-rsync-verify-files-copied-between-two-local-drives](https://unix.stackexchange.com/questions/30970/does-rsync-verify-files-copied-between-two-local-drives)

---

### Post by Rooster2000 on 2023-03-30
> **SeijiSensei said:**
> Use [rsync]("https://linux.die.net/man/1/rsync").

Thanks for suggestion. Forgot to mention that backup is stored in cloud, so encrypted and incremental would be preferred.

Edit: naturally the EaseUS offer for free 250 GB cloud storage is tempting too, although their client is not open source, and I don't know where their servers are located.

> EaseUS Todo Backup offers each user 250GB of free cloud storage so they  can access their backups without the time and space limit.

[[SIZE=2]https://www.easeus.com/backup-software/tb-free.html[/SIZE]]("https://www.easeus.com/backup-software/tb-free.html")

---

