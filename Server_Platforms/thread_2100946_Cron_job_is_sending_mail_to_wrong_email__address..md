---
title: "Cron job is sending mail to *wrong* email  address."
date: 2013-01-03
forum: Server Platforms
---

### Post by Andre-D on 2013-01-03
Every day 
I get an error mail from the server, about an email that could not be sent.
The error mail is sent successfully by ssmtp.
The mail that failed to get delivered, is failed because it's sent by the cron service to:
andre@odin2   (no such email address exist)

Technical details of permanent failure:
DNS Error: Domain name not found

I've tried to force all CRON email to go to correct email address to crontab like this

MAILTO="andre****@gmail.com"  (That did not help.)

(in case you suggest a mail server, Procmail is installed, but not configured.)

To me, it seems that the user's default email address needs to be entered somewhere.

---

### Post by cj13579 on 2013-01-03
Have you tried creating an alias for that user in /etc/aliases?

```
andre : andre***@gmail.com
```

You will need to run the following command after making any changes to /etc/aliases:

```
 sudo newaliases 
```

---

### Post by Andre-D on 2013-01-04
thanks, sudo newaliases said that ssmtp is not using aliases
Then I found this info:
[http://raftaman.net/?p=591](http://raftaman.net/?p=591)

Once mail.rc & ssmtp revaliases was configured, it worked great.

---

