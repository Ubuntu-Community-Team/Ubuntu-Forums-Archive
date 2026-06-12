---
title: "where are the log files?"
date: 2007-09-19
forum: Server Platforms
---

### Post by bone2006 on 2007-09-19
With ubuntu lamps I have apache on port 80 and openssh server on port 33333, and a friend told me that there's logs with each attempt of somebody trying to get into your machine.  

I was told to look into /var/log/messages

I only see weird things like this:


Sep 16 10:52:22 server -- MARK --
Sep 16 11:12:22 server -- MARK --
Sep 16 11:32:22 server -- MARK --

I'm not sure how I'm supposed to look at logs to make sure nobody has attempted to get into my system or to even show when I've been in the system?

---

### Post by HermanAB on 2007-09-19
Log files are in - wait for it - drum roll - /var/log... ;)

You can see what is going on by running tail on the messages file:
$ sudo -i
password
# tail -f /var/log/messages

That will provide a running commentary on most everything.

Do explore the other log files too.

Cheers,

H.

---

### Post by ruibernardo on 2007-09-19
Hi bone2006,

for the apache access log, take a look at /var/log/apache2/access.log. 

For SSH, look at /var/log/auth.log.

---

### Post by bone2006 on 2007-09-19
HermanAB
I'm not sure if you read what I wrote, but I already wrote that I was in the log directory and what was produced from the messages file.  I followed your steps using tail instead of vi/vim just incase something magical would appear and it's producing the same thing I already posted above.

It has no real information

---

### Post by bone2006 on 2007-09-19
Thanks epimeteo 
I looked around at the ssh log and it has root all over the place even though I never enabled a password, is it something I should be concerned with?

---

### Post by ruibernardo on 2007-09-19
Don't be concerned if the look like this:

```
Sep 20 02:39:01 example CRON[7548]: (pam_unix) session closed for user root
Sep 20 03:09:01 example CRON[7573]: (pam_unix) session opened for user root by (uid=0)
```It is [CRON]("https://help.ubuntu.com/community/CronHowto") doing its job. SSH sessions look like this:

```
Sep 18 05:52:41 example sshd[4537]: Accepted password for user from 192.168.235.129 port 33902 ssh2
```

---

### Post by HermanAB on 2007-09-19
OK pardon, you have to look at /var/log/auth.log:
# tail -f /var/log/auth.log

You can also scan it for unauthorised logins by pumping it through grep:
# cat /var/log/auth.log | grep "session opened"

---

### Post by Sporkman on 2007-09-20
You can do:

grep -v CRON auth.log

That will print out auth.log, minus lines with "CRON" in it.

---

### Post by bone2006 on 2007-09-20
thank you all for the reponses.

---

