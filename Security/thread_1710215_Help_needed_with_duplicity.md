---
title: "Help needed with duplicity"
date: 2011-03-19
forum: Security
---

### Post by GonzoCubFan on 2011-03-19
Hi,

First of all, I'm not sure if this is the correct forum for this, but I've seen other duplicity posts here, so here goes...

I've been trying for a few months now to get my duplicity nightly, cron-driven backup working properly.  I backup to an external USB drive, and for the most part it seems to be working correctly.  I have two problems.  First I get a lot of log messages after each backup session, and I'm not sure what to make about most of the messages.  Secondly, the one set of messages that makes sense to me indicates that it apparently does not like my "time constant" string in the "remove-older-than" commands.  For the life of me, I cannot figure out what it wants there.

I'm hoping that someone here with duplicity expertise can help me out and tell me where I'm going wrong.  I've copied my duplicity backup script below as well as the log file that gets emailed to me when the script is run nightly. What I'd really love to see is a clean log message each night that shows that things worked as they are supposed to.  Any help would be greatly appreciated.

Thanks in advance,

 = Ed = 

Here is my duplicity script:
```


# This script was created to make Duplicity backups.
# Full backups are made on the 1st day of each month.
# Then incremental backups are made on the other days.
#

# Loading the day of the month in a variable.
date=`date +%d`

# doing a monthly full backup (1M)
        duplicity --full-if-older-than 1M --no-encryption /home file:///media/ServerBackup/duplicity/home >>/var/log/duplicity/home.log
        duplicity --full-if-older-than 1M --no-encryption /etc file:///media/ServerBackup/duplicity/etc >>/var/log/duplicity/etc.log
        duplicity --full-if-older-than 1M --no-encryption --exclude /var/cache --exclude /var/tmp /var file:///media/ServerBackup/duplicity/var >>/var/log/duplicity/var.log
        duplicity --full-if-older-than 1M --no-encryption /usr/local file:///media/ServerBackup/duplicity/usr/local >>/var/log/duplicity/usr.log
# Check http://www.nongnu.org/duplicity/duplicity.1.html
# for all the options available for Duplicity.

duplicity remove-older-than 6M --force file:///media/ServerBackup/duplicity/home >>/var/log/duplicity/home.log
duplicity remove-older-than 6M --force file:///media/ServerBackup/duplicity/etc >>/var/log/duplicity/etc.log
duplicity remove-older-than 6M --force file:///media/ServerBackup/duplicity/var >>/var/log/duplicity/var.log
duplicity remove-older-than 6M --force file:///media/ServerBackup/duplicity/usr/local >>/var/log/duplicity/usr.log
exit 0

```

And here is the log file that gets emailed to me:
```

Traceback (most recent call last):
 File "/usr/bin/duplicity", line 463, in <module>
   with_tempdir(main)
 File "/usr/bin/duplicity", line 458, in with_tempdir
   fn()
 File "/usr/bin/duplicity", line 388, in main
   action = commandline.ProcessCommandLine(sys.argv[1:])
 File "/usr/lib/python2.5/site-packages/duplicity/commandline.py", line 448, in ProcessCommandLine
   args = parse_cmdline_options(cmdline_list)
 File "/usr/lib/python2.5/site-packages/duplicity/commandline.py", line 186, in parse_cmdline_options
   globals.full_force_time = dup_time.genstrtotime(arg)
 File "/usr/lib/python2.5/site-packages/duplicity/dup_time.py", line 254, in genstrtotime
   error()
 File "/usr/lib/python2.5/site-packages/duplicity/dup_time.py", line 228, in error
   the day).""" % timestr)
duplicity.dup_time.TimeException: Bad time string "--remove-older-than"

The acceptible time strings are intervals (like "3D64s"), w3-datetime
strings, like "2002-04-26T04:22:01-07:00" (strings like
"2002-04-26T04:22:01" are also acceptable - rdiff-backup will use the
current time zone), or ordinary dates like 2/4/1997 or 2001-04-23
(various combinations are acceptable, but the month always precedes
the day).
Traceback (most recent call last):
 File "/usr/bin/duplicity", line 463, in <module>
   with_tempdir(main)
 File "/usr/bin/duplicity", line 458, in with_tempdir
   fn()
 File "/usr/bin/duplicity", line 388, in main
   action = commandline.ProcessCommandLine(sys.argv[1:])
 File "/usr/lib/python2.5/site-packages/duplicity/commandline.py", line 448, in ProcessCommandLine
   args = parse_cmdline_options(cmdline_list)
 File "/usr/lib/python2.5/site-packages/duplicity/commandline.py", line 186, in parse_cmdline_options
   globals.full_force_time = dup_time.genstrtotime(arg)
 File "/usr/lib/python2.5/site-packages/duplicity/dup_time.py", line 254, in genstrtotime
   error()
 File "/usr/lib/python2.5/site-packages/duplicity/dup_time.py", line 228, in error
   the day).""" % timestr)
duplicity.dup_time.TimeException: Bad time string "--remove-older-than"

The acceptible time strings are intervals (like "3D64s"), w3-datetime
strings, like "2002-04-26T04:22:01-07:00" (strings like
"2002-04-26T04:22:01" are also acceptable - rdiff-backup will use the
current time zone), or ordinary dates like 2/4/1997 or 2001-04-23
(various combinations are acceptable, but the month always precedes
the day).
Traceback (most recent call last):
 File "/usr/bin/duplicity", line 463, in <module>
   with_tempdir(main)
 File "/usr/bin/duplicity", line 458, in with_tempdir
   fn()
 File "/usr/bin/duplicity", line 388, in main
   action = commandline.ProcessCommandLine(sys.argv[1:])
 File "/usr/lib/python2.5/site-packages/duplicity/commandline.py", line 448, in ProcessCommandLine
   args = parse_cmdline_options(cmdline_list)
 File "/usr/lib/python2.5/site-packages/duplicity/commandline.py", line 186, in parse_cmdline_options
   globals.full_force_time = dup_time.genstrtotime(arg)
 File "/usr/lib/python2.5/site-packages/duplicity/dup_time.py", line 254, in genstrtotime
   error()
 File "/usr/lib/python2.5/site-packages/duplicity/dup_time.py", line 228, in error
   the day).""" % timestr)
duplicity.dup_time.TimeException: Bad time string "--remove-older-than"

The acceptible time strings are intervals (like "3D64s"), w3-datetime
strings, like "2002-04-26T04:22:01-07:00" (strings like
"2002-04-26T04:22:01" are also acceptable - rdiff-backup will use the
current time zone), or ordinary dates like 2/4/1997 or 2001-04-23
(various combinations are acceptable, but the month always precedes
the day).
Traceback (most recent call last):
 File "/usr/bin/duplicity", line 463, in <module>
   with_tempdir(main)
 File "/usr/bin/duplicity", line 458, in with_tempdir
   fn()
 File "/usr/bin/duplicity", line 388, in main
   action = commandline.ProcessCommandLine(sys.argv[1:])
 File "/usr/lib/python2.5/site-packages/duplicity/commandline.py", line 448, in ProcessCommandLine
   args = parse_cmdline_options(cmdline_list)
 File "/usr/lib/python2.5/site-packages/duplicity/commandline.py", line 186, in parse_cmdline_options
   globals.full_force_time = dup_time.genstrtotime(arg)
 File "/usr/lib/python2.5/site-packages/duplicity/dup_time.py", line 254, in genstrtotime
   error()
 File "/usr/lib/python2.5/site-packages/duplicity/dup_time.py", line 228, in error
   the day).""" % timestr)
duplicity.dup_time.TimeException: Bad time string "--remove-older-than"

The acceptible time strings are intervals (like "3D64s"), w3-datetime
strings, like "2002-04-26T04:22:01-07:00" (strings like
"2002-04-26T04:22:01" are also acceptable - rdiff-backup will use the
current time zone), or ordinary dates like 2/4/1997 or 2001-04-23
(various combinations are acceptable, but the month always precedes
the day).

```

---

