---
title: "rysync working in .sh file, but when cron set up it doesn't"
date: 2014-04-01
forum: Server Platforms
---

### Post by agarrett5 on 2014-04-01
I got a script to work in rsyncing backup files from one location to another.  It worked when running from .sh fale (using sudo ./).

I have asked webmin to run it as cron job but on each file its coming up with > rsync: chown "/mnt/backup/Fri" failed: Permission denied (13)

I'm running it as root, which I was on command line.

---

### Post by ally2 on 2014-04-01
ls -l 

what are the permissions on the file you are trying to run?

---

### Post by TheFu on 2014-04-01
root on system A is NOT the same as root on system B, unless you go out of your way to make that connection. If you post the exact command, we might be able to help. Also, turn up the verbosity on the rsync command to see great error/warning data.  rsync uses ssh by default - does ssh between the two systems work using ssh-keys?

Scripting 101:
* always fully specify paths to all programs and files (input/output) inside any script. NEVER trust the PATH.
* always set any environment variables necessary to the script. Don't trust the userid environment to be available during cron. JAVA_HOME is an example, but there are thousands of others - most scripts need fewer than 5 environment variables.
* use the -x to see what a script does.
* use built-in "verbosity" settings for any specific command
* check the log files - client-side AND server-side.

I'm gonna post this on my blog too.

---

### Post by agarrett5 on 2014-04-01
The rsync works in the.sh file.  It gives that error message if run through cron on webmin.  The sh file is run sudo ./<filename.sh>

In cron its set as: execute as root
 cmmand:<filename.sh>

---

### Post by SeijiSensei on 2014-04-01
Let's avoid webmin, shall we, and just create the entry manually.

I prefer to use /etc/crontab for root processes.  Add an entry to that file that looks like this:
```
01 00 * * * root sh /path/to/your/script
```
That will run the script at one minute past midnight every night.

You'll need to edit /etc/crontab as root with sudo.

---

### Post by lukeiamyourfather on 2014-04-01
What is the name of the script? If it has a period like "foo.sh" then cron will ignore it (but "foo" would run just fine).

---

### Post by TheFu on 2014-04-01
> **lukeiamyourfather said:**
> What is the name of the script? If it has a period like "foo.sh" then cron will ignore it (but "foo" would run just fine).

Huh?  ANY filename that cron can access will be run if the read and execute permissions are set correctly. 
The name has ZERO to do with it.  
The extension has ZERO to do with it.

foo.sh is fine.
foo is fine.

Just be certain to completely specify the name.
```
# .---------------- minute (0 - 59) 
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ... 
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
# *  *  *  *  *  command to be executed
3 2  *  *  * /root/bin/backup-to-rom.sh

```
So at 203am, that script will be run. This is in a file location that only root can access, so this is the "root crontab".  The output will be emailed to the "root" account on the machine, unless you setup email aliases and/or forwarding. To suppress email, add ```

 > /dev/null 2>&1
``` after the command.

---

### Post by lukeiamyourfather on 2014-04-02
> **TheFu said:**
> Huh?  ANY filename that cron can access will be run if the read and execute permissions are set correctly. 
The name has ZERO to do with it.  
The extension has ZERO to do with it.

foo.sh is fine.
foo is fine.


I should clarify, that's the case when using the /etc/cron.* directories. See the run-parts manual for more information.

[http://manpages.ubuntu.com/manpages/precise/man8/run-parts.8.html](http://manpages.ubuntu.com/manpages/precise/man8/run-parts.8.html)

---

### Post by TheFu on 2014-04-02
Ah.  I run servers and use crontabs,   edit with **crontab -e**. filenames don't matter at all.

For sometimes-on systems, the /etc/cron* stuff makes sense, but not so much when control over the exact time a task runs is desired. On systems where I do use the cron.daily/ directory, it drives me nuts when jobs run at times that are less-than-optimal. Still, it is a great solution for those needs.

---

