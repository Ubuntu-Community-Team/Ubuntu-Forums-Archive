---
title: "MySQL Password in Crontab"
date: 2009-07-23
forum: Security
---

### Post by Mr_Lazy on 2009-07-23
Hi,

I want to execute a series of MySQL procedures using Cron, but I have a concern. To execute the procedures a MySQL password has to be in the Crontab file, but how secure is this file on the server? Can it be hidden or protected so only a (Linux) root account can access it?

I am a bit new to Linux so sorry if this is a no brainer....

Thanks 
L.

---

### Post by andrewc6l on 2009-07-23
It pretty much does this already. You need to be root in order to read /var/spool/cron/crontabs, so if you add to your user's crontab, it should be visible to only root. Use
crontab -e
to edit it.

(Note that anyone who can sudo can read it - but anyone who can sudo can also become root, so that's not really a security issue.)

---

### Post by Mr_Lazy on 2009-07-23
OK, thanks for your answer, that has reassured me.

---

### Post by TurboRush on 2009-07-23
Depending on what commands you need to execute you could also create seperate user that has very limited privledges and run as that user. 

I need to backup a single database every night so I created a user that can't do anything except pull out the data from a that one database. Not fool proof, but limits the exposure if that account was compromised.

---

### Post by Mr_Lazy on 2009-07-24
TurboRush, that is an excellent suggestion. I forgot the mantra about only giving accounts/users only the privileges they need. This Cron job will not DELETE, INSERT or DROP anything, so it should have a separate account with only the privileges it requires, down to table level as well.

Thanks for the idea.

---

### Post by ErDty&amp;h on 2010-11-18
Fairly newbie. Just came across this thread. Still looking for a more generic solution.

@andrew6 -- "It pretty much does this already." -- [INDENT]What you say is true, but it doesn't deal with the underlying security issue -- saving unencrypted passwords on the server. Anyone with privileges can read /etc/passwd, and that was a huge hole that required /etc/shadow to tighten up.
[/INDENT]@ TurboRush[INDENT]Thanks for the excellent advice. As a newbie, I forget that I can create accounts I never intend to log into just to perform specific admin tasks. But again, it's not ideal. I'm looking for something more generic.
[/INDENT]Anybody have ideas on how to set up some kind of personal  shadow password file to use in your own scripts?

---

### Post by rkillcrazy on 2011-01-19
> **ErDty&h said:**
> Fairly newbie. Just came across this thread. Still looking for a more generic solution.

@andrew6 -- "It pretty much does this already." -- [INDENT]What you say is true, but it doesn't deal with the underlying security issue -- saving unencrypted passwords on the server. Anyone with privileges can read /etc/passwd, and that was a huge hole that required /etc/shadow to tighten up.
[/INDENT]@ TurboRush[INDENT]Thanks for the excellent advice. As a newbie, I forget that I can create accounts I never intend to log into just to perform specific admin tasks. But again, it's not ideal. I'm looking for something more generic.
[/INDENT]Anybody have ideas on how to set up some kind of personal  shadow password file to use in your own scripts?

You could create a script that is scheduled to run via a cron job.  The script can be owned by **root** and you can chmod it to 0700 that way no other user can even view the script.

I do wish this could be done with a .credentials file like we tend to use for entries in fstab though....

---

### Post by Dave_L on 2011-01-19
If I recall correctly, you can place a hidden MySQL config file that contains the MySQL password in the user's home directory .  Then the crontab entry would not need to specify the password.

The MySQL manual should have more details on this.

---

### Post by maticer on 2011-11-17
You can use:
```
/usr/bin/mysql --defaults-file=/etc/mysql/debian.cnf
```

---

