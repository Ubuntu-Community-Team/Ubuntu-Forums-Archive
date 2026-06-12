---
title: "retrieve old rsync snapshot"
date: 2009-12-25
forum: Server Platforms
---

### Post by m@ripr on 2009-12-25
Hi,

I've been playing with rsync for a month by now for incremental backup. I have a master folder containing last sync and several folders containing increments (--backup and --backup-dir options used). Each day I rsync my folder. I started the first of december so I have approx. 24 folders in my --backup-dir folder containing increments.

All worked fine.

Now let's say I want to retrieve the exact snapshot of, say, the backup of the 2nd of december. Do I have to manually go through all backup to retrive this particular snapshot ?

Is there any way to play with rsync as we play in subversion (get working copy of revision 27)

Hope i am clear, not sure though.

And yes I am aware of rdiff-backup that I am already using. But for this need I only can (and want to learn how) use rsync.

Thanks to all.

M

---

### Post by mhanson on 2009-12-30
Yes and no. Your use of the term snapshot related to rsync is a bit incorrect since you dont restore like a dedicated backup software functions and no you will not experience any real similarities between it and a vcs like SVN. However, to go back to any given date you just reverse the command. So you swap the destination and the source. You also should decide if you want to work file by file or by an entire directory.

rsync is very simplistic by nature which makes it so nice to use.

So if 4 weeks ago you did:
rsync -rvu /home/user/ /backups/november30/home/user/
 
Today you would (for an individual file):
rsync -rvu /backups/november30/home/user/file_to_restore /home/user/

---

