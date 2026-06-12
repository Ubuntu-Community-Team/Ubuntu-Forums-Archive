---
title: "automatic email sending of changed log files"
date: 2011-10-03
forum: Server Platforms
---

### Post by d347hm4573r on 2011-10-03
Hi there,

I have used google and the search function of this forum, but I didn't get any results. And I google alot..!

Now to my actual question:
What I want is to send myself an Email containing the new lines of the /var/log/auth.log. Every day. So what I thought of was a daily cron job sending me the content of that file:
```
mail my@emailaddress.com < /var/log/auth.log
```
But then I figured that it would send me the whole file, everytime, which is not what I want. And I don't know if the auth.log files gets cleared every now and then.

Is there a way to only send myself the new lines, that were added to the auth.log file??


Thank you for your help

---

### Post by [S|G] on 2011-10-03
You can, but you'd have to have to have a copy of the file from the previous day to compare to the current one.

A VERY rough and simple way to do this would be something like the following script (you'd need to create an empty "yesterday" file to begin with):

---------------------------------------------------
#!/bin/bash
# Your previous day log file name
OLDLOG=/var/log/auth.log.yesterday

# Your current log
CURLOG=/var/log/auth.log

# File where to keep the differences
DIFFLOG=/tmp/auth.diff.log

# Check the differences between today and yesterday
diff $OLDLOG $CURLOG|grep ^\> > $DIFFLOG 

# Copy today's log over yesterday's
cp $CURLOG $OLDLOG

# Send the differences by mail
mail bla@bla < $DIFFLOG

# Remove the temp file
rm $DIFFLOG

---

### Post by SeijiSensei on 2011-10-04
An easier solution is to modify the file /etc/logrotate.d/rsyslog and set up a custom rotation schedule for /var/log/auth.log.  You'll see that file in the list in the bottom half of the rsyslog file.  Remove /var/log/auth.log from that list, then set up the following definition at the end of the file:

```

[...]

/var/log/auth.log
{
        rotate 30
        daily
        missingok
        notifempty
        sharedscripts
        postrotate
                reload rsyslog >/dev/null 2>&1 || true
        endscript
}

```

That will rotate the log daily and keep thirty prior versions numbered from auth.log.1 to auth.log.30.  

Logrotate runs at around 6:25 am as defined by /etc/crontab.  It's one of the tasks invoked from the /etc/cron.daily directory.  If you run your job after that time, say at 6:45 am, and mail yourself /var/log/auth.log.1, you'll have just the previous day's entries.

---

### Post by Jonathan L on 2011-10-04
Hi .. 

you might also look at the mailfirst option of logrotate, which emails the newly created log file, and dateext, which will call it auth-20111231

Kind regards
Jonathan

---

### Post by d347hm4573r on 2011-10-04
> **SeijiSensei said:**
> An easier solution is to modify the file /etc/logrotate.d/rsyslog and set up a custom rotation schedule for /var/log/auth.log.  You'll see that file in the list in the bottom half of the rsyslog file.  Remove /var/log/auth.log from that list, then set up the following definition at the end of the file:

```

[...]

/var/log/auth.log
{
        rotate 30
        daily
        missingok
        notifempty
        sharedscripts
        postrotate
                reload rsyslog >/dev/null 2>&1 || true
        endscript
}

```

That will rotate the log daily and keep thirty prior versions numbered from auth.log.1 to auth.log.30.  

Logrotate runs at around 6:25 am as defined by /etc/crontab.  It's one of the tasks invoked from the /etc/cron.daily directory.  If you run your job after that time, say at 6:45 am, and mail yourself /var/log/auth.log.1, you'll have just the previous day's entries.

So how would I state the command the send the corresoponding file, acording to the day?
It does sound like a good idea to me, because if I want to check a different day that would be awesome..

---

### Post by [S|G] on 2011-10-04
> **d347hm4573r said:**
> So how would I state the command the send the corresoponding file, acording to the day?

You should just send your auth.log.1 file. That'll always be "yesterday's" file.

---

### Post by d347hm4573r on 2011-10-04
> **'[S|G] said:**
> You should just send your auth.log.1 file. That'll always be "yesterday's" file.

ah ok.. that's convinient.. :D
Thank you very much

---

