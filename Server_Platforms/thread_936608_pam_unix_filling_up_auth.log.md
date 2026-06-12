---
title: "pam_unix filling up auth.log"
date: 2008-10-03
forum: Server Platforms
---

### Post by Shwick2 on 2008-10-03
Running ubuntu 8.04 desktop.

I have sshd server running and there's a cron job that seems to be running every 10 seconds.  It keeps opening and closing a session and it logs this every time to /var/log/auth.log.

Oct  2 14:45:01 desktop CRON[7760]: pam_unix(cron:session): session closed for user root
Oct  2 14:55:01 desktop CRON[7762]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct  2 14:55:01 desktop CRON[7762]: pam_unix(cron:session): session closed for user root
Oct  2 15:05:01 desktop CRON[7764]: pam_unix(cron:session): session opened for user root by (uid=0)

Is there an elegant way to stop this, I don't think this is supposed to happen.

---

### Post by cariboo on 2008-10-03
Actually that is normal, on my server it happens every 5 minutes instead of 10 minutes like yours. :)

Jim

---

### Post by iansane on 2008-10-03
Mine too. Only I've got 

auth.log
auth.log.0
auth.log.1.gz
auth.log.2.gz

So do they get auto gziped when they get so big? Is it safe to delete or back up all but auth.log and clear that file on a regular basis so it can start over?

I just started reading about PAM here, [http://www.linux.com/feature/113567](http://www.linux.com/feature/113567)
and this appears to be from a login session module for PAM. Others in the file are sudo sessions and webmin sessions in mine.

---

### Post by Shwick2 on 2008-10-04
I've read how pam can block brute force ssh attacks but I already have an iptables configuration doing that.  

 I don't really know what it's doing logging into ssh as root every 10 minutes, and I don't think I need it doing that either.

 I tried Try sudo crontab -l and it comes up blank.

---

### Post by Shwick2 on 2008-10-07
Anyone know how to disable this yet?

---

### Post by lykwydchykyn on 2008-10-08
If you check /var/log/syslog, there should be some record of a corresponding action at the times listed which is accessing cron.  From what I can tell, even simply listing the root crontab (sudo crontab -l) generates one of these entries.

Have you checked syslog?

---

### Post by Shwick2 on 2008-10-08
Finally.  Stupid sysstat, some package that supplies mpstat, iostat and sar commands.

It had a script in /etc/cron.d/sysstat which sent machine statistics every 10 minutes to an ubuntu central server where they analyzed the information to gear the next release to the most common machine hardware against your will!!!!

No wait... just the first part about it logging stats to a file every 10 minutes.

---

### Post by iansane on 2008-10-08
Glad you found it but is that the same as that option to participate thing I think it was during install or something and I left the box unchecked?

It was something about sending info about hardware? 

Not that I don't want to help but I'm paranoid about things like that.

---

### Post by Shwick2 on 2008-10-08
no i was completely joking about that part- it only logged the info to a file.  I don't know what option it was.

---

### Post by tobler on 2009-09-24
> **Shwick2 said:**
> Running ubuntu 8.04 desktop.
Oct  2 14:45:01 desktop CRON[7760]: pam_unix(cron:session): session closed for user root
Oct  2 14:55:01 desktop CRON[7762]: pam_unix(cron:session): session opened for user root by (uid=0)
. . .
Is there an elegant way to stop this, I don't think this is supposed to happen.

I have same problem on my Hardy LTS server. I am running many cron jobs and every time I get two rows of text into log file.

When trying to find solution, there are some ideas in RedHat bug-report forum: [https://bugzilla.redhat.com/show_bug.cgi?id=165571](https://bugzilla.redhat.com/show_bug.cgi?id=165571)
I am testing to disable pam_unix.so to generate these log entries by disabling @include common-session -row in file /etc/pam.d/cron. It may cause some other troubles so beware! But now I don't get these rows into my logfile!

Another idea is that use syslog-ng and create filters to get rid of rows where are CRON and pam_unix mentioned.

---

