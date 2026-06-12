---
title: "Backup user"
date: 2007-02-23
forum: Server Platforms
---

### Post by Koybe on 2007-02-23
Hello,

I installed ubuntu as a mail server (pop/maildir) and I need a email [email]backup@mydomain.com[/email]. Anyway there is already a backup user that got /var/backups as his home directory.

What's the need for that user? Can I change is homedir to a normal homedir? When is this used?


Thank you.

---

### Post by Koybe on 2007-02-25
It seems that /var/backups contains :
- logs for aptitude, dpkg...
- backupfiles for users, group and shadow.

There is a cron.daily job that puts these files in that particular directory but i can't get what this user is used for?

No one knows what's the deal with this particular user? Can I rename it backups without any damage?

Thank you.

---

### Post by jtc on 2007-02-25
Well, I doubt anyone is going to try to email your backup-user, so I'm fairly sure you can "steal" its mail address with good consious :-) The easiest would probably be just to add an alias. Do that by  edit /etc/aliases

```

backup:        otherusername

``` 

Then, having savid your new /etc/aliases you have to finish of by running the command "newaliases".

---

### Post by Koybe on 2007-02-25
Ok but then I need to create a Maildir dir in /var/backups... doesn't it look strange?

---

### Post by jtc on 2007-02-25
No, if you have an alias then simply all mail addressed to backup would end up in the mailbox of otherusername. As long as that user has a maildir it will be fine.

---

### Post by Koybe on 2007-02-25
OK thank you! :D

---

