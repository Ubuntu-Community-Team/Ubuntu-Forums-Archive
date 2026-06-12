---
title: "Webmin Backup does not work"
date: 2011-03-07
forum: Server Platforms
---

### Post by jl2035 on 2011-03-07
Hi all! 

I already posted this on Webmin forums but I got no help...so here it goes:

I want to make a daily backup of my websites from ubuntu server over ftp to another server I own. Backup schedule and process works, the problem is backup restore. Winrar says: The file is corrupt, 7-zip crashes.

Backup archive looks ok (the same size as original folder) and you can also extract it ignoring the error by winrar. But the extracted folder only contains one or two subfolder and one file(usually image) and that's all.  

If I try to restore from Webmin it doesn't report any error, and it looks like restore worked. But restored files are nowhere...

Lp, jl

---

### Post by yotis on 2011-03-07
What format are your backups? Tar, perhaps?

I have no doubts that you know how to use Webmin, but maybe a look here will help you:
[http://doxfer.webmin.com/Webmin/FilesystemBackup](http://doxfer.webmin.com/Webmin/FilesystemBackup)

It's quite an old post but still fit these days.

Good luck and let us know if you have solved this issue.

---

### Post by jl2035 on 2011-03-07
Yes TAR format... I don't know how to do it in other format, it automatically selects tar no matter if it's checked or not... I would rather just backup the folder as it is..

---

### Post by jl2035 on 2011-03-07
The most ridiculous thing is that the tar file size is about 400MB, but the archive contains only one file and when you extract it's 1.60KB...

---

### Post by mbvhq on 2011-06-16
i have the exact same problem
on restore, no error message, the tape device remains busy, nothing happens, no file restored ... 

ubuntu 8.04 server 64 bit
webmin 1.420

---

### Post by collisionystm on 2011-06-16
Just use rsnapshot. You can do several days worth of backups. I have my stuff backing up to 2 weeks.

It does one full backup and then incremental backups after that.

```
sudo apt-get install rsnapshot
```sudo crontab -e

add this entry

```
0 0  * * *     rsnapshot daily
```This will run rsnapshot at midnight everyday. 

edit the conf to set your backup parameters. 

```
nano /etc/rsnapshot.conf
```Here is my rsnapshot.conf to help you out.

> ################################################
# rsnapshot.conf - rsnapshot configuration file #
#################################################
#                                               #
# PLEASE BE AWARE OF THE FOLLOWING RULES:       #
#                                               #
# This file requires tabs between elements      #
#                                               #
# Directories require a trailing slash:         #
#   right: /home/                               #
#   wrong: /home                                #
#                                               #
#################################################

#######################
# CONFIG FILE VERSION #
#######################

config_version    1.2

###########################
# SNAPSHOT ROOT DIRECTORY #
###########################

# All snapshots will be stored under this root directory.
#
[QUOTE][COLOR=Red]snapshot_root    /media/usb0/rsnapshot/[/COLOR]
This is where you want your rsnapshot files stored. Be sure to make this directory in advance!


# If no_create_root is enabled, rsnapshot will not automatically create the
# snapshot_root directory. This is particularly useful if you are backing
# up to removable media, such as a FireWire or USB drive.
#
#no_create_root    1

#################################
# EXTERNAL PROGRAM DEPENDENCIES #
#################################

# LINUX USERS:   Be sure to uncomment "cmd_cp". This gives you extra features.
# EVERYONE ELSE: Leave "cmd_cp" commented out for compatibility.
#
# See the README file or the man page for more details.
#
#cmd_cp        /bin/cp

# uncomment this to use the rm program instead of the built-in perl routine.
#
cmd_rm        /bin/rm

> # rsync must be enabled for anything to work. This is the only command that
# must be enabled.
#
[COLOR=Red]cmd_rsync    /usr/bin/rsync[/COLOR]
Be sure to make sure this is enabled! Just unhash it to enable it.


# Uncomment this to enable remote ssh backups over rsync.
#
cmd_ssh    /usr/bin/ssh

# Comment this out to disable syslog support.
#
cmd_logger    /usr/bin/logger

# Uncomment this to specify the path to "du" for disk usage checks.
# If you have an older version of "du", you may also want to check the
# "du_args" parameter below.
#
#cmd_du        /usr/bin/du

# Uncomment this to specify the path to rsnapshot-diff.
#
#cmd_rsnapshot_diff    /usr/local/bin/rsnapshot-diff

# Specify the path to a script (and any optional arguments) to run right
# before rsnapshot syncs files
#
#cmd_preexec    /path/to/preexec/script

# Specify the path to a script (and any optional arguments) to run right
# after rsnapshot syncs files
#
#cmd_postexec    /path/to/postexec/script

#########################################
#           BACKUP INTERVALS            #
# Must be unique and in ascending order #
# i.e. hourly, daily, weekly, etc.      #
#########################################

#interval    hourly    7
> [COLOR=Red]interval    daily    14
[COLOR=Black]As you  can see, you have several options for backup methods. I chose to do daily only. Therefore, I hashed out everything else. This option is going to backup my stuff for 14 days. So I can go back in time 2 weeks. If you choose to do hourly or monthly...etc. Make sure to edit your crontab accordingly. I.E. rsnapshot monthly, rsnapshot daily, rsnapshot hourly...etc.[/COLOR]
[/COLOR]#interval    weekly    2
#interval    monthly    3

############################################
#              GLOBAL OPTIONS              #
# All are optional, with sensible defaults #
############################################

# Verbose level, 1 through 5.
# 1     Quiet           Print fatal errors only
# 2     Default         Print errors and warnings only
# 3     Verbose         Show equivalent shell commands being executed
# 4     Extra Verbose   Show extra verbose information
# 5     Debug mode      Everything
#
[COLOR=Black]verbose        5[/COLOR]

# Same as "verbose" above, but controls the amount of data sent to the
# logfile, if one is being used. The default is 3.
#
[COLOR=Black]loglevel    5[/COLOR]

# If you enable this, data will be written to the file you specify. The
# amount of data written is controlled by the "loglevel" parameter.
#
logfile    /var/log/rsnapshot.log

# If enabled, rsnapshot will write a lockfile to prevent two instances
# from running simultaneously (and messing up the snapshot_root).
# If you enable this, make sure the lockfile directory is not world
# writable. Otherwise anyone can prevent the program from running.
#
lockfile    /var/run/rsnapshot.pid

# Default rsync args. All rsync commands have at least these options set.
#
#rsync_short_args    -a
#rsync_long_args    --delete --numeric-ids --relative --delete-excluded

# ssh has no args passed by default, but you can specify some here.
#
#ssh_args    -p 22

# Default arguments for the "du" program (for disk space reporting).
# The GNU version of "du" is preferred. See the man page for more details.
# If your version of "du" doesn't support the -h flag, try -k flag instead.
#
#du_args    -csh

# If this is enabled, rsync won't span filesystem partitions within a
# backup point. This essentially passes the -x option to rsync.
# The default is 0 (off).
#
#one_fs        0

# The include and exclude parameters, if enabled, simply get passed directly
# to rsync. If you have multiple include/exclude patterns, put each one on a
# separate line. Please look up the --include and --exclude options in the
# rsync man page for more details on how to specify file name patterns. 
# 
#include    ???
#include    ???
#exclude    ???
> [COLOR=Red]exclude    Shared_Software/[/COLOR]
choose the files you want to exclude. If none, leave as is.
# The include_file and exclude_file parameters, if enabled, simply get
# passed directly to rsync. Please look up the --include-from and
# --exclude-from options in the rsync man page for more details.
#
#include_file    /path/to/include/file
#exclude_file    /path/to/exclude/file

# If your version of rsync supports --link-dest, consider enable this.
# This is the best way to support special files (FIFOs, etc) cross-platform.
# The default is 0 (off).
#
#link_dest    0

# When sync_first is enabled, it changes the default behaviour of rsnapshot.
# Normally, when rsnapshot is called with its lowest interval
# (i.e.: "rsnapshot hourly"), it will sync files AND rotate the lowest
# intervals. With sync_first enabled, "rsnapshot sync" handles the file sync,
# and all interval calls simply rotate files. See the man page for more
# details. The default is 0 (off).
#
#sync_first    0

# If enabled, rsnapshot will move the oldest directory for each interval
# to [interval_name].delete, then it will remove the lockfile and delete
# that directory just before it exits. The default is 0 (off).
#
#use_lazy_deletes    0

# Number of rsync re-tries. If you experience any network problems or
# network card issues that tend to cause ssh to crap-out with
# "Corrupted MAC on input" errors, for example, set this to a non-zero
# value to have the rsync operation re-tried
#
#rsync_numtries 0

###############################
### BACKUP POINTS / SCRIPTS ###
###############################

# LOCALHOST
> [COLOR=Red]backup    root@172.16.64.2:/opt        oscar
backup    /media/usb0/QWServer/C        QWC_drive
backup    /media/usb0/QWServer/D        QWD_drive
backup    /media/usb0/QWServer/N        QWN_drive
backup    root@172.16.64.4:/home        NDS
backup    root@172.16.64.4:/etc        NDS
[COLOR=Black]Chhose the files you want to backup. As you can see I have local entries as well as SSH from other servers. The ssh are the root@ipaddress. The FOLDER name after the entrie is the name of the folder as I want it to appear in the rsnapshot backup folder. NDS will go to NDS folder. oscar to oscar folder, etc.[/COLOR]
[/COLOR]#backup    /etc/        localhost/
#backup    /usr/local/    localhost/
#backup    /var/log/rsnapshot        localhost/
#backup    /etc/passwd    localhost/
#backup    /home/foo/My Documents/        localhost/
#backup    /foo/bar/    localhost/    one_fs=1, rsync_short_args=-urltvpog
#backup_script    /usr/local/bin/backup_pgsql.sh    localhost/postgres/

# EXAMPLE.COM
#backup_script    /bin/date "+ backup of example.com started at %c"    unused1
#backup    [EMAIL="root@example.com"]root@example.com[/EMAIL]:/home/    example.com/    +rsync_long_args=--bwlimit=16,exclude=core
#backup    [EMAIL="root@example.com"]root@example.com[/EMAIL]:/etc/    example.com/    exclude=mtab,exclude=core
#backup_script    ssh [EMAIL="root@example.com"]root@example.com[/EMAIL] "mysqldump -A > /var/db/dump/mysql.sql"    unused2
#backup    [EMAIL="root@example.com"]root@example.com[/EMAIL]:/var/db/dump/    example.com/
#backup_script    /bin/date    "+ backup of example.com ended at %c"    unused9

# CVS.SOURCEFORGE.NET
#backup_script    /usr/local/bin/backup_rsnapshot_cvsroot.sh    rsnapshot.cvs.sourceforge.net/

# RSYNC.SAMBA.ORG
#backup    rsync://rsync.samba.org/rsyncftp/    rsync.samba.org/rsyncftp/[/QUOTE]

---

