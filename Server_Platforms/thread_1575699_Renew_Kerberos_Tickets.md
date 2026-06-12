---
title: "Renew Kerberos Tickets?"
date: 2010-09-16
forum: Server Platforms
---

### Post by Lucky. on 2010-09-16
I've been running Kerberos successfully for over 6 months now (Ubuntu Server & Client).  However if I stay logged in too long (Over 10 hours), I automatically lose access to certain resources because my tickets expire.  I know I could increase the life of the tickets, but would prefer my computer to automatically renew the ticket.

I've seen some solutions around on the net that seem to involve cron jobs that check the status & renew.  This seems awful hack-ish.  Is there an elegant and simple setting somewhere to auto-renew?  Or is there a good reason that tickets shouldn't be renewed?

---

### Post by Lucky. on 2010-09-27
As a follow up, here's what I did from start to finish (with the help of forumite anirudhtomer in [this thread](http://ubuntuforums.org/showthread.php?t=1580802)).

**After getting Kerberos working on server and client, do the following on the client:**

1.  Install the "kstart" package.

```
apt-get kstart
```

2.  Edit /etc/profile and add this at the end:

```

krenew -K 10 -b -p ~/.krenewprocess.txt

```

This runs krenew as a daemon to check every 10 minutes if the kerberos ticket is near expiration, and renew if necessary.  It also records the process ID of the daemon in the user's home directory as ".krenewprocess.txt" (file name is irrelevant, but I put it there and put a period in front of it so it's invisible and doesn't get in each user's way.)

3.  The reason I recorded the PID was so I could destroy it on logout.  If I didn't, then each logout/login would result in another daemon being created (even if it's the same user logging in and out).  I needed to kill this process on logout.

4.  In order to kill the process on the way out, I edited the following file:

```

/etc/gdm/PostSession/Default

```

...and put the following near the end of the file, but before the "exit 0" line:

```

while read line
do
kill $line
done < ~/.krenewprocess.txt
rm ~/.krenewprocess.txt

```

5.  In the end, the following happens for each user that logs in/out:

a.  User logs in, and /etc/profile is run.  krenew daemon is created, and pid is recorded in user's home directory under ".krenewprocess.txt".

b.  krenew does its thing, renewing Kerberos tickets as necessary.

c.  When user logs out, /etc/gdm/PostSession/Default is run, which reads form .krenewprocess.txt and kills the pid of krenew that was launched upon login.  Note that I couldn't use "killall krenew" or that would kill each possible daemon created by other users (if multiple users were logged on at the same time).

d.  Finally, the file containing the pid is deleted/cleaned up (last part of /etc/gdm/PostSession/Default).

Seems to be working so far...

---

