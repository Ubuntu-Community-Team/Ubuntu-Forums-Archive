---
title: "I edited and saved mail.log, now it won't update"
date: 2011-12-10
forum: Server Platforms
---

### Post by Linksku on 2011-12-10
I added a bunch of newlines in /var/log/mail.log to distinguish which lines are the new errors and I saved it. Now, new errors aren't being written to mail.log.
I tried removing the newlines, and deleting the file. There are still no new logs.

---

### Post by kamaji792 on 2011-12-11
Just a thought, have you tried renaming the file to see if the system will create a new log file?

Might be worth looking at the log file permissions.

Atb k

---

### Post by Lars Noodén on 2011-12-11
> **kamaji792 said:**
> Might be worth looking at the log file permissions.


The permissions should be these:
```

$ ls -l /var/log/mail.log 
-rw-r----- 1 syslog adm 0 Dec  7 16:26 /var/log/mail.log

```

You can set them like this:

```

sudo chown syslog.adm /var/log/mail.log
sudo chmod 640 /var/log/mail.log

```

---

### Post by SeijiSensei on 2011-12-13
Did you stop the rsyslog service before editing the log file?  If not, you probably need to run "service rsyslog restart" to have it start logging again.

Rather than adding blank lines to the file, why not just stop rsyslog, rename the file and start a new one like this:

```

sudo service rsyslog stop
cd /var/log
sudo mv mail.log mail.log.bak
sudo touch mail.log
sudo chown syslog.adm mail.log
sudo chmod 640 mail.log
sudo service rsyslog start

```

---

