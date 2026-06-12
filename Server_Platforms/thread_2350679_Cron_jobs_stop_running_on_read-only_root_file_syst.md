---
title: "Cron jobs stop running on read-only root file system"
date: 2017-01-26
forum: Server Platforms
---

### Post by ramah2 on 2017-01-26
We have an Ubuntu 14.04 server that has had its root file system go read-only.  We have a check in place with a cron job to send an email when the file system was detected to be read-only.  However we also found that when the root file system / was read-only cron jobs stopped running.

It is difficult to find out why the jobs are not running because nothing is logged once the root file system is read-only.  Is there a way to keep cron running when the root file system is in read-only?  I am not sure where cron writes its files when jobs start, but could that be forwarded to tmpfs in memory?

We would prefer to keep the check on the servers themselves rather than have an external check from a separate server.

Thank you for your time.

---

### Post by SeijiSensei on 2017-01-26
Cron is going to log its behavior to /var/log/syslog.  I don't know what happens if the rsyslog daemon cannot write those entries.  Other than that, I don't think cron writes anything in particular to the filesystem in the course of running a job.  It certainly doesn't write a lock file.  I wouldn't move the logs to tmpfs; you'd lose the ability to diagnose problems if the machine reboots.  Do you have another server that you could use as a [centralized logger]("https://vexxhost.com/resources/tutorials/how-to-setup-remote-system-logging-with-rsyslog-on-ubuntu-14-04-lts/")?

Have you investigated why the filesystem is going read-only?  Usually that happens when the filesystem has errors that cannot be cured by the simple fsck that happens at boot.  Rather than worry about the symptoms, I'd invest some serious effort in finding out what the problem might be.  Is there a chance the server loses power sporadically?  Is it connected to a UPS?

---

### Post by raja.genupula on 2017-01-26
Hi Sensei, 

If we store the logs in tmpfs (of course it has to write them in the filesystem after threshold size or before shutting down) and redirecting whole file as an attachment to an E-mail ? 

Would it work , is it possible ?

---

### Post by ramah2 on 2017-01-27
Thank you for the replies.  While I do agree that prevention is better, we cannot prevent an underlying SAN issue that causes most, if not all of our linux servers to switch their file systems to read only.  The important thing for us is the detection and notification of this state when it happens.  Also, I am only worried about logging to see why it is failing.

I have replicated the issue by booting / in read-only and NO cron jobs will run.  I have a bash script/cron job touching a file on /run (tmpfs) every minute.  With / in read-only I can run the script manually manually and the file is created.  The cron job that is pointed at the script does not appear to be executing, because no file is being created.  If I remount / in rw the files are then created.

Based on what I have seen, I am working under an assumption that cron needs to create a file on the root file system in order to start a job.

---

### Post by SeijiSensei on 2017-01-27
As I said, I don't believe cron creates any files other than an entry in syslog.  Does the script you are trying to run create files?

---

### Post by ramah2 on 2017-01-27
It does create a file:

```

#!/bin/bash

PATH=/sbin:/bin:/usr/sbin:/usr/local/bin:/usr/bin
export PATH

GET_DATE=$(date +'%Y-%m-%d-%H:%M')

/usr/bin/touch /run/$GET_DATE.txt

```

Perhaps if it cant write to the syslog it wont run?

---

### Post by ramah2 on 2017-01-27
I was able to redirect syslog to /run and confirmed that cron does create tmp files.  See errors when / is read-only then remount in rw and a successful run of the job.

Jan 27 14:55:01  CRON[1674]: (CRON) error (create tmpfile)
Jan 27 14:56:01  CRON[1699]: (CRON) error (create tmpfile)
Jan 27 14:56:10  kernel: [ 1758.404902] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jan 27 14:57:01  CRON[1713]: (root) CMD (/root/scripts/test_cron.sh)

Looking at the source code (crontab.c), this does not appear to be configurable and I will probably have to compile a custom version if I want to redirect this to /run as I do not want to redirect all tmp files to /run/tmp.

```

    (void) sprintf(Filename, "/tmp/crontab.%d", Pid);
    if (-1 == (t = open(Filename, O_CREAT|O_EXCL|O_RDWR, 0600))) {
        perror(Filename);
        goto fatal;
    }

```

Thank you for your replies.

---

