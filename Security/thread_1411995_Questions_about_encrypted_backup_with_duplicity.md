---
title: "Questions about encrypted backup with duplicity"
date: 2010-02-20
forum: Security
---

### Post by Zilioum on 2010-02-20
I managed to make an encrypted backup of my ubuntu box onto my server and was also able to restore it. I mainly followed this tutorial [here.]("http://www.go2linux.org/scp-duplicity-secure-backup")
Altough everything worked fine I have two questions:
[LIST=1]
[*]What is that part for ? > export PASSPHRASE=your_passphrase
[*]Just for the fun of it, and to see how it would handle incremental backups I ran the backup command a second time and was, to my surprise, asked to provide my GpG password. Whys that? And how can I "auto-login", since I would like to run this command in a cron job.
[/LIST]

Cheers

---

### Post by jfparis on 2010-02-20
The export passphrase if a way to give your passphrase to duplicity. He gonna need if you decrypt the previous checksum files

Use the export line correctly and then you won't be asked for your passphrase again

---

### Post by Zilioum on 2010-02-20
Ok, thanks. So ill just put > export PASSPHRASE=your_passphrase  in the cronjob as well. But isnt there a better way? Not really secure in my opinion to put my passphrase in plaintext into a cronjob.

---

### Post by jfparis on 2010-02-20
Put in into a shell script into ~/bin for example
Be sure the file is chmod 0700 so only you can read it.

---

### Post by Zilioum on 2010-02-21
Ok, I'll do that. Thanks.

---

### Post by Zilioum on 2010-02-21
5 minutes ago my backup should haven been started by cron, using my backup script. Looking at the log, I saw that it didnt work because of ```
Invalid SSH password
```
I get the same error when I run the script as root, but when I run it as a normal user it works. Whys that?
I could just run the cronjob as normal user, but on the other hand I would like to have only one crontab.

---

