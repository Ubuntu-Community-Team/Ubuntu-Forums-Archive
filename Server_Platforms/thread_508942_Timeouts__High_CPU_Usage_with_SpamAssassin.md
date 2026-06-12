---
title: "Timeouts / High CPU Usage with SpamAssassin"
date: 2007-07-24
forum: Server Platforms
---

### Post by oxygen on 2007-07-24
Hi all,

I have a Ubuntu box run for a mail server. Via a cron job the machine uses getmail to check a users email and download any messages. I then have courier serving these via IMAP locally.

I recently started using spamd to filter the incoming emails - however what I find is that it seems to be chewing up the CPU whenever it checks an email.

End users IMAP connections are constantly timing out - however only when there is spamd process running.

I've tried setting the priority level to 19 using nice - however it doesn't seem to make any difference. Does anyone have any experience with this happening before?

---

### Post by Mr. C. on 2007-07-24
You're going to have to give more specifics.

[LIST]
[*]How long does it take spamd to check each message?
[*]Do you limit the size of a message that you send to spamd?
[*]What CPU speed/type?
[*]How much RAM?
[*]Have you added any extra rulesets?
[*]How often does your cron job run
[*]What is the average amount of email that you send to spamd at one time?
[*]Are you logs showing any problems?
[/LIST]

Lots of variables.
MrC

---

### Post by oxygen on 2007-07-24
[LIST]
[*]How long does it take spamd to check each message? **Between 5 to 10 seconds**
[*]Do you limit the size of a message that you send to spamd?**Yes, 100k**
[*]What CPU speed/type?**Celeron 2.8Ghz**
[*]How much RAM?**512MB DDR**
[*]Have you added any extra rulesets?**No**
[*]How often does your cron job run**Every 5 minutes**
[*]What is the average amount of email that you send to spamd at one time?**One email at a time**
[*]Are you logs showing any problems?**Logs don't show any issues**
[/LIST]

---

### Post by Mr. C. on 2007-07-24
Ok, great.

Between 5 and 10 seconds is normal.  Search for the "SA check" line in the timing report here from amavis, as it calls SpamAssassin:

[http://www.mikecappella.com/logwatch/example-amavis-detail10](http://www.mikecappella.com/logwatch/example-amavis-detail10)

You'll notice that that 90% of the time, it takes less than 9.587 seconds, 75% is less than 6.039, etc.

Since you are using courier, and hence the Maildir format, and are only dropping one email at a time, it doesn't make sense that courier is timing out due to your getmail calls to spamd.  SpamAssassin is more network latency intensive than local CPU intensive.  The only way I can see this happening is if getmail is being called in parallel for multiple messages or profiles.  Are you serializing each users's downloads?

And do have have an max_messages_per_session setting?

I wouldn't recommend changing the priority of the process - this isn't the correct way to solve this.

What you are going to have to do, is look at the basic system diagnostics during the times when you experience courier timeouts.  You can just use **top** if you want, updating each second, and you can also look at the output of **sar**, checking the times when there is trouble.

Let's see what you find.

MrC

---

### Post by Mr. C. on 2007-07-24
Ah, I found something which confirms a suspicion:

> How do I stop multiple instances of getmail from running at the same time?

getmail has no problems running multiple instances in parallel, though you shouldn't attempt to use the same getmail rc file from two different instances at the same time. If you need to prevent two instances of getmail from running simultaneously, use any standard Unix method of providing a mutex for this purpose. One example would be to run getmail under a program like setlock (part of the daemontools package). Change your script or crontab file to invoke getmail like this:

/path/to/setlock -n /path/to/lockfile /path/to/getmail [getmail options]

There are other programs that provide functionality similar to setlock. 

Are you ensuring only one getmail instance runs at a time ?

MrC

---

### Post by oxygen on 2007-07-24
This is the contents of my script - which cron runs every 5 minutes:

```

USERS="`ls -1 /home`"
for i in $USERS; do
  command su $i -c "nice -19 getmail"
done

```

From observing **top** only one instance is ever running at a time. It does each user sequentially.

---

### Post by Mr. C. on 2007-07-24
Oh, you definitely do not want nice -19 !  That will starve every other process.  Perhaps you meant nice 19 !

MrC

---

### Post by oxygen on 2007-08-07
Turns out it had nothing to do with getmail or spamassassin - I had the MAXDAEMONS settings for Courier IMAP set to low!

---

