---
title: "Copying a file from a PC running Ubuntu to a website"
date: 2020-12-01
forum: Ubuntu Application Development
---

### Post by schmitta on 2020-12-01
I need to copy a data file to a website that I own. How do I do that automatically once a day with ubuntu? Thank you.

---

### Post by TheFu on 2020-12-01
Use rsync over ssh.  The webhost must allow ssh.  If not, fire them and get a better host.  Setup ssh-keys for authentication.
Step 1:  Run on the client as the normal user:
```
   $ ssh-keygen -t ed25519
```

Step 2:  Run from the client to the server:
```
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote
```

Google "rsync examples" for lots of examples.
```
   $ rsync -avz /opt/my/project/files/ username@remote:path/to/my/project/files/
```
This will recursively copy everything under /opt/my/project/files/.  Note that the trailing '/' on the source is critical. 
Also, on the remote machine, note that my example path is relative, not absolute.

As for scheduling this to happen, use cron for that. Here's a helpful template:
```
$ crontab -l
# .---------------- minute (0 - 59) 
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ... 
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
# *  *  *  *  *  command --arg1 --arg2 file1 file2 2>&1
```
Those are all comments, so add that to the top of your personal crontab file, then add the actual command(s) and settings below. For example, 
```
1 0 * * * /home/tf/bin/push_keepass_db.sh
```
At 1 minute after midnight, daily, I run a script to push my password manager DB file to about 6 different systems. I want an email, so I don't redirect stdout or stderr to files or nowhere.  By default, cron will email all output, using a configured MTA on the system, to the userid running the process.  That userid would be based on who's crontab it is.

There are other ways to automatically do things using root.  For using rsync to other systems, using root would be a bad idea, from a security standpoint, so I won't say anything about those other crontab files or locations.

---

### Post by schmitta on 2020-12-02
Thank you for your help

---

