---
title: "Cannot restore deleted directory using rdiff-backup"
date: 2011-05-17
forum: Security
---

### Post by Paddy Landau on 2011-05-17
I have carefully made daily backups using rdiff-backup, so in the case of needing to restore I can do so.

But.

I deleted a directory yesterday, and made a backup in the evening. Therefore, the directory is not in the latest mirror, but in the incremental backup from yesterday.

Now I need to restore the directory. But I cannot figure out how to!

I can see the directory in yesterday's incremental backup; i.e., the following works:
```
sudo rdiff-backup --list-at-time 1D [backupdir] [nameofdir]
```where [backupdir] is the backup (mirror) directory, and [nameofdir] is the name of the directory I'm trying to restore.

So, I have tried to restore. This is the type of thing I have tried:
```
sudo rdiff-backup --restore-as-of 1D --include-globbing-filelist to-restore.lst [backupdir] [restoredir]
```where to-restore.lst holds the name of the directory to restore (in rdiff-backup's format) and [restoredir] is where I want the restored directory to go to.

But, I get errors like:
```
Fatal Error: Fatal Error: The file specification
    '/home/paddy/[nameofdir]/'
cannot match any files in the base directory
    '/home/paddy/[restoredir]'
Useful file specifications begin with the base directory or some
pattern (such as '**') which matches the base directory.
```Well, obviously the file specification doesn't exist in the [restoredir]. That's because I'm trying to restore it! If I try to create an empty directory first, it complains:
```
Fatal Error: Restore target /home/paddy/[restoredir] already exists, specify --force to overwrite.
```Please help. How do I restore a deleted directory from a previous day's backup to a designated destination?

---

### Post by Paddy Landau on 2011-05-17
Bump...

Maybe there is a tutorial on restoring with rdiff-backup somewhere? I have Googled without success.

---

### Post by Paddy Landau on 2011-05-17
Ah, I've found the answer. Two answers, actually.

**The very slow way: archfs**

[LIST]
[*]Install [archfs]("apt:archfs").
[*]Mount your backup:```
sudo archfs [mountpoint] [repository]
```
[*]Now, you can browse your backup (as root) to find what you want; and you can copy it to where you want.
[*]Having restored, everything will be read-only and belong to root, so you will have to use chown and chmod.
[/LIST]
*Pros:* Visual (you can use Nautilus). Each version is displayed in an appropriately-named directory, so you can simply browse.

*Cons:* Slow. Very slow. (It took several minutes to load my backup. Changing directories within the virtual drive takes a long time. (However, I have many versions; if you have a very fast computer or few versions it should be reasonably fast.)) After restoring you need to chown and chmod; the original permissions and ownership are lost. Remember to start Nautilus with gksu.

**The fast way: CLI**

I had misunderstood the requirements. The format is:
```
sudo rdiff-backup --restore-as-of [time] [repository]/[directorytorestore] [targetdirectory]
```*Pros:* Fast. Restores permissions and ownership.

*Cons:* Not visual; you need the command line interface (CLI).

---

