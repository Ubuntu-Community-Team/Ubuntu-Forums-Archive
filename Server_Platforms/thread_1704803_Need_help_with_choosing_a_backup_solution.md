---
title: "Need help with choosing a backup solution"
date: 2011-03-11
forum: Server Platforms
---

### Post by youdontneedtoknow on 2011-03-11
[COLOR=#000000][FONT=Times New Roman][LEFT][FONT=Arial]Hi all,
I need help choosing a backup solution for a server amongst all the tools that I read about recently (rsnapshot,amanda,clonezilla,rsync,dd,duplicity,bacula...).

The setup:
[1] one disk (a RAID actually) with the live system (ubuntu server 10.0.4) running on it.
[2] another disk mounted to /media/backup on that same system

The requirements:
-be able to create compressed backups of [1] to [2] while [1] is running.
-be able to recover individual files/directories from [2]'s backups to [1] while [1] is running.
-ideally be able to look at the files on [2] before restoring them to [1].
-be able to restore completely [1] from one of [2]'s backups.

Any input is welcome
[/FONT][/LEFT]
[/FONT][/COLOR]

---

### Post by HermanAB on 2011-03-11
Howdy,

Rsync is your friend, but it doesn't do compression.

---

