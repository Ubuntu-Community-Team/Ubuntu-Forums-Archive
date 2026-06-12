---
title: "Logcheck running multiple times over the course of an hour"
date: 2008-02-07
forum: Server Platforms
---

### Post by Rich99 on 2008-02-07
I use logcheck on 6.06LTS.  It used to work perfectly, however recently it has been running multiple times.  I use the default cron job to run it - /etc/cron.d/logcheck looks like this:

# /etc/cron.d/logcheck: crontab entries for the logcheck package

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root

@reboot         logcheck    if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck -R; fi
* 2 * * *       logcheck    if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi

# EOF

At 2am it runs correctly, however it then continues to run every couple of minutes for the next hour, so that I get about 26 logcheck emails sent between 2 & 3 am.  The first email always says it can't get a lock on the lockfile, the next includes all the info from the previous day then the remainder all contain info from the couple of minutes between them & the previous email.  Any ideas why it's doing this - there's no entry in the root crontab, nor in /etc/cron.daily, so I can't see why it's running continuously.  At reboot it runs fine - just once.

---

### Post by MJN on 2008-02-07
I don't know anything about logcheck however check your syslog to see if it really is cron executing it over and over. I suspect that, given the first e-mail is mentioning an error, then it is actually the first instance of logcheck (run by cron) that is re-running (outputting) every couple of minutes.

If nothing else this will narrow down the cause to between cron and logcheck itself.

Mathew

---

### Post by Rich99 on 2008-02-09
The problem appears to be cron - syslog shows this:

Feb  9 02:00:05 rich /USR/SBIN/CRON[16242]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:01:01 rich /USR/SBIN/CRON[18092]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:02:01 rich /USR/SBIN/CRON[18359]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:03:01 rich /USR/SBIN/CRON[19012]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:04:01 rich /USR/SBIN/CRON[19665]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:05:01 rich /USR/SBIN/CRON[20321]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:06:01 rich /USR/SBIN/CRON[21000]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:07:01 rich /USR/SBIN/CRON[21653]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:08:01 rich /USR/SBIN/CRON[22314]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:09:02 rich /USR/SBIN/CRON[22982]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:10:01 rich /USR/SBIN/CRON[23668]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:11:01 rich /USR/SBIN/CRON[24356]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:12:01 rich /USR/SBIN/CRON[25009]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:13:01 rich /USR/SBIN/CRON[25662]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:14:01 rich /USR/SBIN/CRON[26315]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:15:02 rich /USR/SBIN/CRON[26972]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:16:01 rich /USR/SBIN/CRON[27654]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:17:01 rich /USR/SBIN/CRON[28317]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:18:02 rich /USR/SBIN/CRON[28970]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:19:01 rich /USR/SBIN/CRON[29623]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:20:01 rich /USR/SBIN/CRON[30281]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:21:01 rich /USR/SBIN/CRON[30938]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:22:01 rich /USR/SBIN/CRON[31595]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:23:02 rich /USR/SBIN/CRON[32251]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:24:01 rich /USR/SBIN/CRON[462]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:25:01 rich /USR/SBIN/CRON[1116]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:26:01 rich /USR/SBIN/CRON[1770]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:27:01 rich /USR/SBIN/CRON[2428]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:28:01 rich /USR/SBIN/CRON[3085]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:29:01 rich /USR/SBIN/CRON[3767]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:30:01 rich /USR/SBIN/CRON[4441]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:31:01 rich /USR/SBIN/CRON[5147]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:32:01 rich /USR/SBIN/CRON[5806]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:33:01 rich /USR/SBIN/CRON[6462]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:34:01 rich /USR/SBIN/CRON[7116]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:35:02 rich /USR/SBIN/CRON[7769]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:36:01 rich /USR/SBIN/CRON[8425]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:37:01 rich /USR/SBIN/CRON[9104]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:38:01 rich /USR/SBIN/CRON[9757]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:39:01 rich /USR/SBIN/CRON[10420]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:40:02 rich /USR/SBIN/CRON[11090]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:41:01 rich /USR/SBIN/CRON[11781]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:42:01 rich /USR/SBIN/CRON[12434]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:43:01 rich /USR/SBIN/CRON[13087]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:44:02 rich /USR/SBIN/CRON[13740]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:45:01 rich /USR/SBIN/CRON[14422]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:46:01 rich /USR/SBIN/CRON[15075]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:47:01 rich /USR/SBIN/CRON[15730]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:48:01 rich /USR/SBIN/CRON[16386]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:49:01 rich /USR/SBIN/CRON[17052]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:50:01 rich /USR/SBIN/CRON[17705]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:51:01 rich /USR/SBIN/CRON[18370]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:52:01 rich /USR/SBIN/CRON[19049]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:53:01 rich /USR/SBIN/CRON[19702]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:54:01 rich /USR/SBIN/CRON[20356]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:55:01 rich /USR/SBIN/CRON[21009]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:56:01 rich /USR/SBIN/CRON[21662]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:57:01 rich /USR/SBIN/CRON[22323]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:58:01 rich /USR/SBIN/CRON[22989]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb  9 02:59:01 rich /USR/SBIN/CRON[23668]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)

Why on earth is it doing this - as far as I'm aware nothing else in cron.d is being run incorrectly.

---

### Post by faulkes on 2008-02-09
Have you checked whether a manual crontab entry exist which is running the logcheck?

crontab -u root -l

Faulkes

---

### Post by Rich99 on 2008-02-09
That just gives 'no crontab for root'.

There's no file called logcheck listed in /etrc/cron.daily, and just the one file called logcheck in /etc/cron.d which cotains:

# /etc/cron.d/logcheck: crontab entries for the logcheck package

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root

@reboot         logcheck    if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck -R; fi
* 2 * * *       logcheck    if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi

# EOF


I've just chaned that file to read 3 am instead of 2am, I'll see what that does to the runs.

---

### Post by Rich99 on 2008-02-10
Well, I changed the cron.d entry to 3am & it then ran 26 times between 3 & 4am, so it's all coming from that single cron entry.  Any ideas?

---

### Post by MJN on 2008-02-10
The answer was staring us in the face:

> **Rich99 said:**
> * 2 * * *       logcheck    if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi

Change that first * to 00

The * wildcard is matching *every* minute... 2:00, 2:01, 2:02 etc

Edit: Actually, presumably Logcheck is intended to constantly monitor the logs? In which case one would expect it to run constantly, or at least very regularly so perhaps it is meant to run every minute (or whatever), but why just between 2am-3am? I would find the cause of the error you say it gives - what is it? As it mentions a lockfile this suggests it is self-aware and wont' overlap consecutive runs, but if yours can't set the lock then it'll run out of control. Post the full error so we can take a look.

Mathew

---

### Post by Rich99 on 2008-02-10
LOL - now I feel stupid!  Thanks for pointing out the obvious.  I seem to remember changing the default runtimes to make it 2am, obviously I screwed up when doing that.  I could have sworn that it originally did only run once at 2am after I changed that, but maybe I'm remembering incorrectly.

Thanks!

---

### Post by MJN on 2008-02-11
At the risk of bursting your bubble I don't think you're out of the woods just yet... ;)

I've checked the source and it would appear that logcheck is intended to be run every 2 minutes by default:

```
# /etc/cron.d/logcheck: crontab entries for the logcheck package

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root

@reboot         logcheck    if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck -R; fi
2 * * * *       logcheck    if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi

# EOF
```Hence, it is designed to keep a constant tab on the logfiles and, presumably, report only if something is amiss.

Of course, such a regular operation needs some self-control to ensure operations don't overlap (you might have a lot of logfiles to check) and so a lockfile is used.

You should set the timings back to the above (default) and see how you go.

Mathew

P.S. If you're not after realtime logfile analysis, but rather just daily reports, then you might wish to consider something like 'logwatch' instead.

---

