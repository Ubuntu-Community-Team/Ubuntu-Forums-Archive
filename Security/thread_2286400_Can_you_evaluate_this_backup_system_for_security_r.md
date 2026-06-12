---
title: "Can you evaluate this backup system for security risks?"
date: 2015-07-11
forum: Security
---

### Post by Raner on 2015-07-11
Can you evaluate this backup system for security risks?

I&#8217;m new to linux and trying to form a good backup system.

I have a program that writes backups to a sshfs mounted drive. This drive is automounted by autofs.

The program has its own group and user account. I have set the remote drive to be mounted inside of a folder that only the program access, /mnt/backup:
```
sudo chmod 700 /mnt/backup
sudo chown my_program /mnt/backup 
sudo chgrp my_program_group /mnt/backup
```

I noticed the path to my ssh keys, the user name of the box I was logging into, and the IP of the box I was logging into was in auto.backup, so to be safe (they were only writable by root but readable by everyone), I did

```
sudo chmod /etc/auto.master 700
sudo chmod /etc/auto.backup 700

```
so that only root can read those files. (auto.backup is just a config file I created that specifies what folders to mount and how.)

I think this means that if an attacker gets access to my non-root user, they will not know the IP/username of where to log in, even if they eventually could find my rsa key (it&#8217;s in the usual place currently &#8211; my user&#8217;s home directory/.ssh).

(EDIT: I posted this but didn't restart my server, but I discovered that after doing so, I can't change the auto.master or auto.backup files to chmod 700; drives will not be auto-mounted unless both remain at chmod 644.) 

But if an attacker managed to get root access, while it seems my program&#8217;s data would be exposed no matter what I do, the real problem now is that the attacker would know where my backups are stored and be able to ssh in and delete them by looking at the auto.master / auto.backup files.

I haven&#8217;t found a good way to protect my backups on the remote box except to have yet another box ssh in and copy them to another machine. This is safe because ssh keys are only one way.

Unfortunately the program itself must be able to both write and delete from the mounted drive.

Ideas on what I can do here? It&#8217;s possible I am missing something quite obvious to a seasoned linux user.

---

### Post by TheFu on 2015-07-12
"Pull" the backups using any tool based on librsync - like rdiff-backup. Rsync uses an ssh tunnel by default and has for at least 10 yrs.
sshfs is nice for quick remote access needs, but not really that good for a backup.  The system being backed up would only have the public ssh key on it that way. Not really useful to an attacker - though they would see the ~/.ssh/authorized_hosts file and they'd see the connection from a remote system with netstat and in the process table, it would still be secure and they wouldn't be able to connect from the server to the backup system.

Plus, if you are really concerned about security, the backups need to be encrypted when stored on disk - for that a tool based on duplicity is probably the easiest. If you do use duplicity-like backups, then you need to follow the 40+ yr old backup schedule with full weekly and incremental backups the rest of the time.

All security techniques are about risk mitigation, when possible. Using a "pull" backup method moved the risks to the backup server.
It is unclear what you are backing up and which userid(s) are being used.  I want to maintain all the file ownership, permissions and ACLs with my backups - those are 50% of what is important, not just the data inside. If you don't use a root-equiv account for backups, that data is lost.

BTW - love the idea of going off the reservation and using sshfs and autofs, but backups are a well-known problem and using the existing tools designed for that specific purpose is usually best. [http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) explains with examples.  Do a small directory like /etc/ for your testing to get a feel for any backup tool.

---

### Post by Raner on 2015-07-12
Thanks for the comments. As a newbie, I learned alot from your reply - I was not considering the value of permissions and ownership. Been looking up the explanations you made for the past hour to try to understand how to do this a bit better.

---

