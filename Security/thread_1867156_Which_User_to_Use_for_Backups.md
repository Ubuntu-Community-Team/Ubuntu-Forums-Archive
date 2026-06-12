---
title: "Which User to Use for Backups"
date: 2011-10-22
forum: Security
---

### Post by hwttdz on 2011-10-22
I'd like to backup the data for my other family members on a machine I administer for them, and I'm wondering which user to use.  I don't really want to use my own, because I'd want to back up their hidden files as well (I don't have read permissions on things like .bash_history, and maybe some other config files).  I'm also shy about using root, because, well, I'm not that clever, I could screw up.  Best case, there would be a user who had universal read access (i.e. read permissions of root), but write permissions to only /backup or /home/backup.  Can I do this?  I guess I could have root su to each of the other users, which would be nice because then they would own their own archives, so I could just make the backup dir sticky.  But I'd still worry about writing something to their directories.

I currently have an archive script which I run on my home (a glorified tar+compression) and if the archive changes in size by more than some threshold it sends me an email.  I guess I should just put it in a loop over home directories, and have a lookup table for their email addresses and actually call the mail command inside the cronjob instead of relying on cron to send messages?

---

### Post by CharlesA on 2011-10-22
I run my backups in a root crontab so that it preserves the permissions and I don't have to worry about messing with the sudoers file in order to mount a drive without getting prompted for the sudo password.

I have been using just the mail command instead of letting cron email me so that I know exactly what I want to know.

---

