---
title: "backup MySQL to a date named file"
date: 2010-09-23
forum: Server Platforms
---

### Post by Vegan on 2010-09-23
I am manually backing up my server now with mysqldump and that works but I was wondering about mechanizing the process.

Nirvana would be to dump to a file named with the date

This way I have backups going back over time

---

### Post by Ryan Dwyer on 2010-09-23
```

ryan@ryan-pc:~$ date
Fri Sep 24 07:27:03 EST 2010
ryan@ryan-pc:~$ mysqldump -u root -p dbname > "`date`.sql"
Enter password: 
ryan@ryan-pc:~$ ls *.sql
Fri Sep 24 07:27:13 EST 2010.sql

```

Play with the date parameters to format it as you want.

---

### Post by Vegan on 2010-09-23
I was hoping to get a simple format such as

20100923.sql so that I can gzip it up to save on storage

---

### Post by FuturePilot on 2010-09-23
> **Vegan said:**
> I was hoping to get a simple format such as

20100923.sql so that I can gzip it up to save on storage

```
date +%Y%m%d
```

---

### Post by SeijiSensei on 2010-09-23
```

#!/bin/sh

# where to put the backups and log
BACKUPDIR=/backup/mysql
LOG="$BACKUPDIR/mybackup.log"

# how many days should we keep 
ROTATE=15


# leave empty to backup local server,
# else specify remote server's hostname
DBHOST=

# enter custom MySQL port if other than default (3306)
DBPORT=3306


# MySQL database owner and password; use root to back up everything
DBUSER="root"
DBPASS="root.password"


# list of MySQL databases to back up; a separate file will 
# be created for each database in the list
DBLIST="msqldb1 mysqldb2"


######################################################################

# Here be monsters, cap'n!

# if a port is specified on the command line, use it
[ "$1" != "" ] && DBPORT=$1

echo -n `date -R` >> $LOG
echo " MySQL backup procedure starting" >> $LOG

TODAY=`date +%y%m%d`
STALE=`date +%y%m%d --date="$ROTATE days ago"`

for D in `echo $DBLIST`
do
        NEWFILE="$BACKUPDIR/dump-$D.$TODAY"
        OLDFILE="$BACKUPDIR/dump-$D.$STALE"

        echo "Creating backup file $NEWFILE" >> $LOG
        mysqldump --user=$DBUSER --password=$DBPASS $D > $NEWFILE 2>>$LOG 3>>$LOG

        echo "Deleting stale backup file $OLDFILE" >> $LOG
        rm -f $OLDFILE 2>>$LOG 3>>$LOG

done

echo -n `date -R` >> $LOG
echo " MySQL backup procedure completed" >> $LOG


```

This code generates backup files of the form "dump-dbname.YYMMDD" and stores them, and a log, in BACKUPDIR.  It keeps up to ROTATE days of backups.  You're welcome to it!

I usually put administrative scripts like this one in /usr/local/sbin.  If you create a symlink to the file in /etc/cron.daily, it will be run automatically every night.

Be careful if copying that the "backtick" character (`) is handled correctly.  It can be accidentally deleted when moving from one character encoding to another.

---

### Post by terazen on 2010-09-24
I've used this for a few years now.
[http://sourceforge.net/projects/automysqlbackup/](http://sourceforge.net/projects/automysqlbackup/)

A how-to:
[http://www.howtoforge.com/creating-mysql-backups-with-automysqlbackup](http://www.howtoforge.com/creating-mysql-backups-with-automysqlbackup)

Basically you just edit the file and set it to run nightly in your crontab and done.

---

### Post by Vegan on 2010-09-24
I downloaded that script from sourceforge and I edited with my specs and I have chmod'ed it to 777 and symlinked it to /etc/cron.daily

The script lives in my home directory, for want of a place to put it.

now to see how well it works.

I am sure this thread will be of benefit to legions of Linux users.

---

### Post by terazen on 2010-09-24
If it runs as root you only need the permissions to be 700.  I put the script in /bin, but like SeijiSensei said /usr/local/sbin is fine too.  I guess the location doesn't matter as much, but I wouldn't want it world readable with my mysql passwords!

---

### Post by Vegan on 2010-09-26
So far the script is not doing anything. So I am still backing up manually.

I have a symlink to the /etc/cron.daily and the script is marked executable.

---

### Post by terazen on 2010-09-26
Have you tried running the backup script manually as root?

---

### Post by BkkBonanza on 2010-09-26
I've always liked `date +%F` which gives "2009-09-28".
Here's portions of my backup to Amazon S3 script...


```

DBS="admin jazz cars other"
S3BUCKET="bak.mydomain.com"
SQLDIR=/usr/bin/
DBDIR=/var/lib/mysql/
GZDIR=/bin/
TODAY=`date +%F`
SQLPWD=xxxxx
S3SPEC="*${TODAY}*"

cd /var/bak

${SQLDIR}mysqladmin --user=root --password=${SQLPWD} flush-logs
for db in $DBS
  do ${SQLDIR}mysqldump --user=root --password=${SQLPWD} --master-data $db | ${GZDIR}gzip > $db-${TODAY}.sql.gz
done

echo --- S3 Backup ${TODAY} --- >>s3.log
for file in ${S3SPEC};
do echo $file >>s3.log;
  gpg -r MyBackupKey -e $file;
  s3put ${S3BUCKET}/ $file.gpg >>s3.log;
  rm $file.gpg;
done

# remove any old archives
find *.gz -maxdepth 1 -atime +2 -exec rm -f {} \;

```

---

### Post by Vegan on 2010-09-27
> **terazen said:**
> Have you tried running the backup script manually as root?

Turns out the script is no good.

---

### Post by SeijiSensei on 2010-09-27
Which script?  Mine or another one?

---

### Post by Vegan on 2010-09-27
> **SeijiSensei said:**
> Which script?  Mine or another one?

Yours

I tried fixing, but all that did was spawn more errors.

---

### Post by BkkBonanza on 2010-09-28
Can you post the script for suggestions to fix it?

---

### Post by SeijiSensei on 2010-09-28
OK, I've reproduced the section at the top where the configuration information is entered:

```
# where to put the backups and log
BACKUPDIR=/backup/mysql
LOG="$BACKUPDIR/mybackup.log"

# how many days should we keep 
ROTATE=15


# leave empty to backup local server,
# else specify remote server's hostname
DBHOST=

# enter custom MySQL port if other than default (3306)
DBPORT=3306


# MySQL database owner and password; use root to back up everything
DBUSER="root"
DBPASS="root.password"


# list of MySQL databases to back up; a separate file will 
# be created for each database in the list
DBLIST="msqldb1 mysqldb2"

```

Did you change these values to match your configuration?  For instance, did you replace the value for BACKUPDIR to point to the directory in which you want the backups written?  The entry I have there, "/backup/mysql," is just an example.  You *could* store the files there, but first you'd need to create /backup/mysql with the mkdir command like this:

mkdir -p /backup/mysql

The -p switch tells the mkdir command to make any "parent" directories that might be needed.  So if you don't have a /backup directory, it would make that first before creating the mysql subdirectory.

The value of ROTATE depends on how cautious you are and how much disk space you can afford to allocate to backups.  Fifteen days may be too many; if so, eight is good alternative.

DBHOST should be blank if you're backing up a database on the local machine, and DBPORT should be left at the correct default value of 3306 unless your MySQL server is listening on a custom port.  So there's usually no need to change either of these.

Typically you want to leave DBUSER as "root" so the script is authorized to dump any database regardless of ownership.  "root.password" should be replaced with the actual password for the root MySQL user.  If the MySQL root account has no password, then leave this field blank and delete the string "--password=$DBPASS" from the mysqldump command further down in the file.

Finally, this script is designed to create separate dump files for each database you enter in DBLIST.  The entries "mysqldb1" and "mysqldb2" are just examples.  You should enter the names of the databases on your server that you need to back up.

Does this help?  Sorry if the script wasn't explicit enough that the entries were just sample values.

Oh, and if the script is linked to /etc/cron.daily, then it will be run as the Linux "root" user and thus have permission to create files in /backup/mysql, or wherever you'll be writing your backups.  If you run this from a normal account, though, you should either use sudo or make sure that the account you're using can write to the backup directory.

---

### Post by Vegan on 2010-09-28
I have a 777 folder called public that is also shared with SAMBA. This way I can use my Windows machine to copy the files to DVD for archival storage.

I set the values in the script to place I wanted it saved etc. Used NANO to edit the script as shown.

---

### Post by SeijiSensei on 2010-09-28
> **Vegan said:**
> I set the values in the script to place I wanted it saved etc. Used NANO to edit the script as shown.

Please post your version inside [noparse]```

```[/noparse] tags.

What errors do you see when you run the script?  Could you post those as well?

---

### Post by Vegan on 2010-09-28
```

#!/bin/bash
#
# MySQL Backup Script
# VER. 2.5.1 - http://sourceforge.net/projects/automysqlbackup/
# Copyright (c) 2002-2003 wipe_out@lycos.co.uk
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA
#
#=====================================================================
#=====================================================================
# Set the following variables to your system needs
# (Detailed instructions below variables)
#=====================================================================
#set -x
CONFIGFILE="/etc/automysqlbackup/automysqlbackup.conf"

if [ -r ${CONFIGFILE} ]; then
	# Read the configfile if it's existing and readable
	source ${CONFIGFILE}
else
	# do inline-config otherwise
	# To create a configfile just copy the code between "### START CFG ###" and "### END CFG ###"
	# to /etc/automysqlbackup/automysqlbackup.conf. After that you're able to upgrade this script
	# (copy a new version to its location) without the need for editing it.
	### START CFG ###
	# Username to access the MySQL server e.g. dbuser
	USERNAME=root
	
	# Password to access the MySQL server e.g. password
	PASSWORD=********************
	
	# Host name (or IP address) of MySQL server e.g localhost
	DBHOST=localhost
	
	# List of DBNAMES for Daily/Weekly Backup e.g. "DB1 DB2 DB3"
	DBNAMES="all"
	
	# Backup directory location e.g /backups
	BACKUPDIR="/public
	
	# Mail setup
	# What would you like to be mailed to you?
	# - log   : send only log file
	# - files : send log file and sql files as attachments (see docs)
	# - stdout : will simply output the log to the screen if run manually.
	# - quiet : Only send logs if an error occurs to the MAILADDR.
	MAILCONTENT="log"
	
	# Set the maximum allowed email size in k. (4000 = approx 5MB email [see docs])
	MAXATTSIZE="4000"
	
	# Email Address to send mail to? (user@domain.com)
	MAILADDR="maintenance@example.com"
	
	
	# ============================================================
	# === ADVANCED OPTIONS ( Read the doc's below for details )===
	#=============================================================
	
	# List of DBBNAMES for Monthly Backups.
	MDBNAMES="${DBNAMES}"
	
	# List of DBNAMES to EXLUCDE if DBNAMES are set to all
	DBEXCLUDE=""
	
	# Include CREATE DATABASE in backup?
	CREATE_DATABASE=no
	
	# Separate backup directory and file for each DB? (yes or no)
	SEPDIR=no
	
	# Which day do you want weekly backups? (1 to 7 where 1 is Monday)
	DOWEEKLY=6
	
	# Choose Compression type. (gzip or bzip2)
	COMP=gzip
	
	# Compress communications between backup server and MySQL server?
	COMMCOMP=no
	
	# Additionally keep a copy of the most recent backup in a seperate directory.
	LATEST=no
	
	#  The maximum size of the buffer for client/server communication. e.g. 16MB (maximum is 1GB)
	MAX_ALLOWED_PACKET=
	
	#  For connections to localhost. Sometimes the Unix socket file must be specified.
	SOCKET=
	
	# Command to run before backups (uncomment to use)
	#PREBACKUP="/etc/mysql-backup-pre"
	
	# Command run after backups (uncomment to use)
	#POSTBACKUP="/etc/mysql-backup-post"
	### END CFG ###
fi

#=====================================================================
# Options documantation
#=====================================================================
# Set USERNAME and PASSWORD of a user that has the appropriate permissions
# to backup ALL databases. (See mysql documentation for details)
# NEW in 2.5.1:
# - If USERNAME is set to "debian" and PASSWORD is unset or "" obtain
#   them from the file /etc/mysql/debian.cnf
# - First command line option "-c" for configfile
# - Interpretable Exit-States:
#    1: given configfile is not readable or does not exist
#    2: unknown option
#
# Set the DBHOST option to the server you wish to backup, leave the
# default to backup "this server".(to backup multiple servers make
# copies of this file and set the options for that server)
#
# Put in the list of DBNAMES(Databases)to be backed up. If you would like
# to backup ALL DBs on the server set DBNAMES="all".(if set to "all" then
# any new DBs will automatically be backed up without needing to modify
# this backup script when a new DB is created).
#
# If the DB you want to backup has a space in the name replace the space
# with a % e.g. "data base" will become "data%base"
# NOTE: Spaces in DB names may not work correctly when SEPDIR=no.
#
# You can change the backup storage location from /backups to anything
# you like by using the BACKUPDIR setting..
#
# The MAILCONTENT and MAILADDR options and pretty self explanitory, use
# these to have the backup log mailed to you at any email address or multiple
# email addresses in a space seperated list.
# (If you set mail content to "log" you will require access to the "mail" program
# on your server. If you set this to "files" you will have to have mutt installed
# on your server. If you set it to "stdout" it will log to the screen if run from 
# the console or to the cron job owner if run through cron. If you set it to "quiet"
# logs will only be mailed if there are errors reported. )
#
# MAXATTSIZE sets the largest allowed email attachments total (all backup files) you
# want the script to send. This is the size before it is encoded to be sent as an email
# so if your mail server will allow a maximum mail size of 5MB I would suggest setting
# MAXATTSIZE to be 25% smaller than that so a setting of 4000 would probably be fine.
#
# Finally copy automysqlbackup.sh to anywhere on your server and make sure
# to set executable permission. You can also copy the script to
# /etc/cron.daily to have it execute automatically every night or simply
# place a symlink in /etc/cron.daily to the file if you wish to keep it 
# somwhere else.
# NOTE:On Debian copy the file with no extention for it to be run
# by cron e.g just name the file "automysqlbackup"
#
# Thats it..
#
#
# === Advanced options doc's ===
#
# The list of MDBNAMES is the DB's to be backed up only monthly. You should
# always include "mysql" in this list to backup your user/password
# information along with any other DBs that you only feel need to
# be backed up monthly. (if using a hosted server then you should
# probably remove "mysql" as your provider will be backing this up)
# NOTE: If DBNAMES="all" then MDBNAMES has no effect as all DBs will be backed
# up anyway.
#
# If you set DBNAMES="all" you can configure the option DBEXCLUDE. Other
# wise this option will not be used.
# This option can be used if you want to backup all dbs, but you want 
# exclude some of them. (eg. a db is to big).
#
# Set CREATE_DATABASE to "yes" (the default) if you want your SQL-Dump to create
# a database with the same name as the original database when restoring.
# Saying "no" here will allow your to specify the database name you want to
# restore your dump into, making a copy of the database by using the dump
# created with automysqlbackup.
# NOTE: Not used if SEPDIR=no
#
# The SEPDIR option allows you to choose to have all DBs backed up to
# a single file (fast restore of entire server in case of crash) or to
# seperate directories for each DB (each DB can be restored seperately
# in case of single DB corruption or loss).
#
# To set the day of the week that you would like the weekly backup to happen
# set the DOWEEKLY setting, this can be a value from 1 to 7 where 1 is Monday,
# The default is 6 which means that weekly backups are done on a Saturday.
#
# COMP is used to choose the copmression used, options are gzip or bzip2.
# bzip2 will produce slightly smaller files but is more processor intensive so
# may take longer to complete.
#
# COMMCOMP is used to enable or diable mysql client to server compression, so
# it is useful to save bandwidth when backing up a remote MySQL server over
# the network. 
#
# LATEST is to store an additional copy of the latest backup to a standard
# location so it can be downloaded bt thrid party scripts.
#
# If the DB's being backed up make use of large BLOB fields then you may need
# to increase the MAX_ALLOWED_PACKET setting, for example 16MB..
#
# When connecting to localhost as the DB server (DBHOST=localhost) sometimes
# the system can have issues locating the socket file.. This can now be set
# using the SOCKET parameter.. An example may be SOCKET=/private/tmp/mysql.sock
#
# Use PREBACKUP and POSTBACKUP to specify Per and Post backup commands
# or scripts to perform tasks either before or after the backup process.
#
#
#=====================================================================
# Backup Rotation..
#=====================================================================
#
# Daily Backups are rotated weekly..
# Weekly Backups are run by default on Saturday Morning when
# cron.daily scripts are run...Can be changed with DOWEEKLY setting..
# Weekly Backups are rotated on a 5 week cycle..
# Monthly Backups are run on the 1st of the month..
# Monthly Backups are rotated on a 5 month cycle...
# It may be a good idea to copy Monthly backups offline or to another
# server..
#
#=====================================================================
# Please Note!!
#=====================================================================
#
# I take no resposibility for any data loss or corruption when using
# this script..
# This script will not help in the event of a hard drive crash. If a 
# copy of the backup has not be stored offline or on another PC..
# You should copy your backups offline regularly for best protection.
#
# Happy backing up...
#
#=====================================================================
# Restoring
#=====================================================================
# Firstly you will need to uncompress the backup file.
# eg.
# gunzip file.gz (or bunzip2 file.bz2)
#
# Next you will need to use the mysql client to restore the DB from the
# sql file.
# eg.
# mysql --user=username --pass=password --host=dbserver database < /path/file.sql
# or
# mysql --user=username --pass=password --host=dbserver -e "source /path/file.sql" database
#
# NOTE: Make sure you use "<" and not ">" in the above command because
# you are piping the file.sql to mysql and not the other way around.
#
# Lets hope you never have to use this.. :)
#
#=====================================================================
# Change Log
#=====================================================================
#
# VER 2.5.1-01 - (2010-07-06)
#     - Fixed pathname bug item #3025849 (by Johannes Kolter)
# VER 2.5.1 - (2010-07-04)
#     - Added support for default and optional config file (by Johannes Kolter)
#     - Rotating after backup was successful whith find(1) (by Johannes Kolter)
#     - Implementation of Variables containing full path to binaries to
#       avoid possibly confusion with aliases or builtins. (by Johannes Kolter)
#     - Fixed bug where weekly backups were not being rotated.
#       Added rotation of 5 monthly backups
#       Now all old backups are deleted, not only the most recent one
#       (inspired by oleg@bintime.com)
#     - Use Debian special-file to access database (by Johannes Kolter)
#     - Fixed bug ID: 1438565
#       Moved IO redirection to a place before decicions are made and actions are taken.
#       (inspired by Derk Bernhardt)
#     - Fixed bug ID: #3000316 (reported by Sascha Feldhorst)
#     - Fixed bug ID: #1529458 (reported by Natalie ( njwood ))
#     - Fixed bug ID: #1548919 (reported by Piotr Kuczynski)
# VER 2.5 - (2006-01-15)
#		Added support for setting MAXIMUM_PACKET_SIZE and SOCKET parameters (suggested by Yvo van Doorn)
# VER 2.4 - (2006-01-23)
#    Fixed bug where weekly backups were not being rotated. (Fix by wolf02)
#    Added hour an min to backup filename for the case where backups are taken multiple
#    times in a day. NOTE This is not complete support for mutiple executions of the script
#    in a single day.
#    Added MAILCONTENT="quiet" option, see docs for details. (requested by snowsam)
#    Updated path statment for compatibility with OSX.
#    Added "LATEST" to additionally store the last backup to a standard location. (request by Grant29)
# VER 2.3 - (2005-11-07)
#    Better error handling and notification of errors (a long time coming)
#    Compression on Backup server to MySQL server communications. 
# VER 2.2 - (2004-12-05)
#    Changed from using depricated "-N" to "--skip-column-names".
#    Added ability to have compressed backup's emailed out. (code from Thomas Heiserowski)
#    Added maximum attachment size setting.
# VER 2.1 - (2004-11-04)
#    Fixed a bug in daily rotation when not using gzip compression. (Fix by Rob Rosenfeld)
# VER 2.0 - (2004-07-28)
#    Switched to using IO redirection instead of pipeing the output to the logfile.
#    Added choice of compression of backups being gzip of bzip2.
#    Switched to using functions to facilitate more functionality.
#    Added option of either gzip or bzip2 compression. 
# VER 1.10 - (2004-07-17)
#    Another fix for spaces in the paths (fix by Thomas von Eyben)
#    Fixed bug when using PREBACKUP and POSTBACKUP commands containing many arguments.
# VER 1.9 - (2004-05-25)
#    Small bug fix to handle spaces in LOGFILE path which contains spaces (reported by Thomas von Eyben)
#    Updated docs to mention that Log email can be sent to multiple email addresses.
# VER 1.8 - (2004-05-01)
#    Added option to make backups restorable to alternate database names
#    meaning that a copy of the database can be created (Based on patch by Rene Hoffmann)
#    Seperated options into standard and advanced.
#    Removed " from single file dump DBMANES because it caused an error but
#    this means that if DB's have spaces in the name they will not dump when SEPDIR=no.
#    Added -p option to mkdir commands to create multiple subdirs without error.
#    Added disk usage and location to the bottom of the backup report.
# VER 1.7 - (2004-04-22)
#    Fixed an issue where weelky backups would only work correctly if server
#    locale was set to English (issue reported by Tom Ingberg)
#    used "eval" for "rm" commands to try and resolve rotation issues.
#    Changed name of status log so multiple scripts can be run at the same time.
# VER 1.6 - (2004-03-14)
#   Added PREBACKUP and POSTBACKUP command functions. (patch by markpustjens)
#   Added support for backing up DB's with Spaces in the name.
#   (patch by markpustjens)
# VER 1.5 - (2004-02-24)
#   Added the ability to exclude DB's when the "all" option is used.
#   (Patch by kampftitan)
# VER 1.4 - (2004-02-02)
#   Project moved to Sourceforge.net
# VER 1.3 - (2003-09-25)
#   Added support for backing up "all" databases on the server without
#    having to list each one seperately in the configuration.
#   Added DB restore instructions.
# VER 1.2 - (2003-03-16)
#   Added server name to the backup log so logs from multiple servers
#   can be easily identified.
# VER 1.1 - (2003-03-13)
#   Small Bug fix in monthly report. (Thanks Stoyanski)
#   Added option to email log to any email address. (Inspired by Stoyanski)
#   Changed Standard file name to .sh extention.
#   Option are set using yes and no rather than 1 or 0.
# VER 1.0 - (2003-01-30)
#   Added the ability to have all databases backup to a single dump
#   file or seperate directory and file for each database.
#   Output is better for log keeping.
# VER 0.6 - (2003-01-22)
#   Bug fix for daily directory (Added in VER 0.5) rotation.
# VER 0.5 - (2003-01-20)
#   Added "daily" directory for daily backups for neatness (suggestion by Jason)
#   Added DBHOST option to allow backing up a remote server (Suggestion by Jason)
#   Added "--quote-names" option to mysqldump command.
#   Bug fix for handling the last and first of the year week rotation.
# VER 0.4 - (2002-11-06)
#   Added the abaility for the script to create its own directory structure.
# VER 0.3 - (2002-10-01)
#   Changed Naming of Weekly backups so they will show in order.
# VER 0.2 - (2002-09-27)
#   Corrected weekly rotation logic to handle weeks 0 - 10 
# VER 0.1 - (2002-09-21)
#   Initial Release
#
#=====================================================================
#=====================================================================
#=====================================================================
#
# Should not need to be modified from here down!!
#
#=====================================================================
#=====================================================================
#=====================================================================
#
# Full pathname to binaries to avoid problems with aliases and builtins etc.
#
WHICH="`which which`"
AWK="`${WHICH} gawk`"
LOGGER="`${WHICH} logger`"
ECHO="`${WHICH} echo`"
CAT="`${WHICH} cat`"
BASENAME="`${WHICH} basename`"
DATEC="`${WHICH} date`"
DU="`${WHICH} du`"
EXPR="`${WHICH} expr`"
FIND="`${WHICH} find`"
RM="`${WHICH} rm`"
MYSQL="`${WHICH} mysql`"
MYSQLDUMP="`${WHICH} mysqldump`"
GZIP="`${WHICH} gzip`"
BZIP2="`${WHICH} bzip2`"
CP="`${WHICH} cp`"
HOSTNAMEC="`${WHICH} hostname`"
SED="`${WHICH} sed`"
GREP="`${WHICH} grep`"

function get_debian_pw() {
	if [ -r /etc/mysql/debian.cnf ]; then
		eval $(${AWK} '
			! user && /^[[:space:]]*user[[:space:]]*=[[:space:]]*/ {
				print "USERNAME=" gensub(/.+[[:space:]]+([^[:space:]]+)[[:space:]]*$/, "\\1", "1"); user++
			}
			! pass && /^[[:space:]]*password[[:space:]]*=[[:space:]]*/ {
				print "PASSWORD=" gensub(/.+[[:space:]]+([^[:space:]]+)[[:space:]]*$/, "\\1", "1"); pass++
			}' /etc/mysql/debian.cnf
		)
	else
		${LOGGER} "${PROGNAME}: File \"/etc/mysql/debian.cnf\" not found."
		exit 1
	fi
}

[ "x${USERNAME}" = "xdebian" -a "x${PASSWORD}" = "x" ] && get_debian_pw 

while [ $# -gt 0 ]; do
	case $1 in
		-c)
			if [ -r "$2" ]; then
				source "$2"
				shift 2
			else
				${ECHO} "Ureadable config file \"$2\""
				exit 1
			fi
			;;
		*)
			${ECHO} "Unknown Option \"$1\""
			exit 2
			;;
	esac
done

export LC_ALL=C
PROGNAME=`${BASENAME} $0`
PATH=/usr/local/bin:/usr/bin:/bin:/usr/local/mysql/bin 
DATE=`${DATEC} +%Y-%m-%d_%Hh%Mm`				# Datestamp e.g 2002-09-21
DOW=`${DATEC} +%A`							# Day of the week e.g. Monday
DNOW=`${DATEC} +%u`						# Day number of the week 1 to 7 where 1 represents Monday
DOM=`${DATEC} +%d`							# Date of the Month e.g. 27
M=`${DATEC} +%B`							# Month e.g January
W=`${DATEC} +%V`							# Week Number e.g 37
VER=2.5.1									# Version Number
LOGFILE=${BACKUPDIR}/${DBHOST}-`${DATEC} +%N`.log		# Logfile Name
LOGERR=${BACKUPDIR}/ERRORS_${DBHOST}-`${DATEC} +%N`.log		# Logfile Name
BACKUPFILES=""
OPT="--quote-names --opt"			# OPT string for use with mysqldump ( see man mysqldump )

# IO redirection for logging.
touch ${LOGFILE}
exec 6>&1           # Link file descriptor #6 with stdout.
                    # Saves stdout.
exec > ${LOGFILE}     # stdout replaced with file ${LOGFILE}.
touch ${LOGERR}
exec 7>&2           # Link file descriptor #7 with stderr.
                    # Saves stderr.
exec 2> ${LOGERR}     # stderr replaced with file ${LOGERR}.

# Add --compress mysqldump option to ${OPT}
if [ "${COMMCOMP}" = "yes" ];
	then
		OPT="${OPT} --compress"
	fi

# Add --max_allowed_packet=... mysqldump option to ${OPT}
if [ "${MAX_ALLOWED_PACKET}" ];
	then
		OPT="${OPT} --max_allowed_packet=${MAX_ALLOWED_PACKET}"
	fi

# Create required directories
if [ ! -e "${BACKUPDIR}" ]		# Check Backup Directory exists.
	then
	mkdir -p "${BACKUPDIR}"
fi

if [ ! -e "${BACKUPDIR}/daily" ]		# Check Daily Directory exists.
	then
	mkdir -p "${BACKUPDIR}/daily"
fi

if [ ! -e "${BACKUPDIR}/weekly" ]		# Check Weekly Directory exists.
	then
	mkdir -p "${BACKUPDIR}/weekly"
fi

if [ ! -e "${BACKUPDIR}/monthly" ]	# Check Monthly Directory exists.
	then
	mkdir -p "${BACKUPDIR}/monthly"
fi

if [ "${LATEST}" = "yes" ]
then
	if [ ! -e "${BACKUPDIR}/latest" ]	# Check Latest Directory exists.
	then
		mkdir -p "${BACKUPDIR}/latest"
	fi
eval ${RM} -fv "${BACKUPDIR}/latest/*"
fi


# Functions

# Database dump function
dbdump () {
${MYSQLDUMP} --user=${USERNAME} --password=${PASSWORD} --host=${DBHOST} ${OPT} ${1} > ${2}
return $?
}

# Compression function plus latest copy
SUFFIX=""
compression () {
if [ "${COMP}" = "gzip" ]; then
	${GZIP} -f "${1}"
	${ECHO}
	${ECHO} Backup Information for "${1}"
	${GZIP} -l "${1}.gz"
	SUFFIX=".gz"
elif [ "${COMP}" = "bzip2" ]; then
	${ECHO} Compression information for "${1}.bz2"
	${BZIP2} -f -v ${1} 2>&1
	SUFFIX=".bz2"
else
	${ECHO} "No compression option set, check advanced settings"
fi
if [ "${LATEST}" = "yes" ]; then
	${CP} ${1}${SUFFIX} "${BACKUPDIR}/latest/"
fi	
return 0
}


# Run command before we begin
if [ "${PREBACKUP}" ]
	then
	${ECHO} ======================================================================
	${ECHO} "Prebackup command output."
	${ECHO}
	eval ${PREBACKUP}
	${ECHO}
	${ECHO} ======================================================================
	${ECHO}
fi


if [ "${SEPDIR}" = "yes" ]; then # Check if CREATE DATABSE should be included in Dump
	if [ "${CREATE_DATABASE}" = "no" ]; then
		OPT="${OPT} --no-create-db"
	else
		OPT="${OPT} --databases"
	fi
else
	OPT="${OPT} --databases"
fi

# Hostname for LOG information
if [ "${DBHOST}" = "localhost" ]; then
	HOST=`${HOSTNAMEC}`
	if [ "${SOCKET}" ]; then
		OPT="${OPT} --socket=${SOCKET}"
	fi
else
	HOST=${DBHOST}
fi

# If backing up all DBs on the server
if [ "${DBNAMES}" = "all" ]; then
        DBNAMES="`${MYSQL} --user=${USERNAME} --password=${PASSWORD} --host=${DBHOST} --batch --skip-column-names -e "show databases"| ${SED} 's/ /%/g'`"

	# If DBs are excluded
	for exclude in ${DBEXCLUDE}
	do
		DBNAMES=`${ECHO} ${DBNAMES} | ${SED} "s/\b${exclude}\b//g"`
	done

        MDBNAMES=${DBNAMES}
fi
	
${ECHO} ======================================================================
${ECHO} AutoMySQLBackup VER ${VER}
${ECHO} http://sourceforge.net/projects/automysqlbackup/
${ECHO} 
${ECHO} Backup of Database Server - ${HOST}
${ECHO} ======================================================================

# Test is seperate DB backups are required
if [ "${SEPDIR}" = "yes" ]; then
${ECHO} Backup Start Time `${DATEC}`
${ECHO} ======================================================================
	# Monthly Full Backup of all Databases
	if [ ${DOM} = "01" ]; then
		for MDB in ${MDBNAMES}
		do
 
			 # Prepare ${DB} for using
		        MDB="`${ECHO} ${MDB} | ${SED} 's/%/ /g'`"

			if [ ! -e "${BACKUPDIR}/monthly/${MDB}" ]		# Check Monthly DB Directory exists.
			then
				mkdir -p "${BACKUPDIR}/monthly/${MDB}"
			fi
			${ECHO} Monthly Backup of ${MDB}...
				dbdump "${MDB}" "${BACKUPDIR}/monthly/${MDB}/${MDB}_${DATE}.${M}.${MDB}.sql"
				[ $? -eq 0 ] && {
					${ECHO} "Rotating 5 month backups for ${MDB}"
					${FIND} "${BACKUPDIR}/monthly/${MDB}" -mtime +150 -type f -exec ${RM} -v {} \; 
				}
				compression "${BACKUPDIR}/monthly/${MDB}/${MDB}_${DATE}.${M}.${MDB}.sql"
				BACKUPFILES="${BACKUPFILES} ${BACKUPDIR}/monthly/${MDB}/${MDB}_${DATE}.${M}.${MDB}.sql${SUFFIX}"
			${ECHO} ----------------------------------------------------------------------
		done
	fi

	for DB in ${DBNAMES}
	do
	# Prepare ${DB} for using
	DB="`${ECHO} ${DB} | ${SED} 's/%/ /g'`"
	
	# Create Seperate directory for each DB
	if [ ! -e "${BACKUPDIR}/daily/${DB}" ]		# Check Daily DB Directory exists.
		then
		mkdir -p "${BACKUPDIR}/daily/${DB}"
	fi
	
	if [ ! -e "${BACKUPDIR}/weekly/${DB}" ]		# Check Weekly DB Directory exists.
		then
		mkdir -p "${BACKUPDIR}/weekly/${DB}"
	fi
	
	# Weekly Backup
	if [ ${DNOW} = ${DOWEEKLY} ]; then
		${ECHO} Weekly Backup of Database \( ${DB} \)
		${ECHO}
			dbdump "${DB}" "${BACKUPDIR}/weekly/${DB}/${DB}_week.${W}.${DATE}.sql"
			[ $? -eq 0 ] && {
				${ECHO} Rotating 5 weeks Backups...
				${FIND} "${BACKUPDIR}/weekly/${DB}" -mtime +35 -type f -exec ${RM} -v {} \; 
			}
			compression "${BACKUPDIR}/weekly/${DB}/${DB}_week.${W}.${DATE}.sql"
			BACKUPFILES="${BACKUPFILES} ${BACKUPDIR}/weekly/${DB}/${DB}_week.${W}.${DATE}.sql${SUFFIX}"
		${ECHO} ----------------------------------------------------------------------
	
	# Daily Backup
	else
		${ECHO} Daily Backup of Database \( ${DB} \)
		${ECHO}
			dbdump "${DB}" "${BACKUPDIR}/daily/${DB}/${DB}_${DATE}.${DOW}.sql"
			[ $? -eq 0 ] && {
				${ECHO} Rotating last weeks Backup...
				${FIND} "${BACKUPDIR}/daily/${DB}" -mtime +6 -type f -exec ${RM} -v {} \; 
			}
			compression "${BACKUPDIR}/daily/${DB}/${DB}_${DATE}.${DOW}.sql"
			BACKUPFILES="${BACKUPFILES} ${BACKUPDIR}/daily/${DB}/${DB}_${DATE}.${DOW}.sql${SUFFIX}"
		${ECHO} ----------------------------------------------------------------------
	fi
	done
${ECHO} Backup End `${DATEC}`
${ECHO} ======================================================================


else # One backup file for all DBs
${ECHO} Backup Start `${DATEC}`
${ECHO} ======================================================================
	# Monthly Full Backup of all Databases
	if [ ${DOM} = "01" ]; then
		${ECHO} Monthly full Backup of \( ${MDBNAMES} \)...
			dbdump "${MDBNAMES}" "${BACKUPDIR}/monthly/${DATE}.${M}.all-databases.sql"
			[ $? -eq 0 ] && {
				${ECHO} "Rotating 5 month backups."
				${FIND} "${BACKUPDIR}/monthly" -mtime +150 -type f -exec ${RM} -v {} \; 
			}
			compression "${BACKUPDIR}/monthly/${DATE}.${M}.all-databases.sql"
			BACKUPFILES="${BACKUPFILES} ${BACKUPDIR}/monthly/${DATE}.${M}.all-databases.sql${SUFFIX}"
		${ECHO} ----------------------------------------------------------------------
	fi

	# Weekly Backup
	if [ ${DNOW} = ${DOWEEKLY} ]; then
		${ECHO} Weekly Backup of Databases \( ${DBNAMES} \)
		${ECHO}
		${ECHO}
			dbdump "${DBNAMES}" "${BACKUPDIR}/weekly/week.${W}.${DATE}.sql"
			[ $? -eq 0 ] && {
				${ECHO} Rotating 5 weeks Backups...
				${FIND} "${BACKUPDIR}/weekly/" -mtime +35 -type f -exec ${RM} -v {} \; 
			}
			compression "${BACKUPDIR}/weekly/week.${W}.${DATE}.sql"
			BACKUPFILES="${BACKUPFILES} ${BACKUPDIR}/weekly/week.${W}.${DATE}.sql${SUFFIX}"
		${ECHO} ----------------------------------------------------------------------
		
	# Daily Backup
	else
		${ECHO} Daily Backup of Databases \( ${DBNAMES} \)
		${ECHO}
		${ECHO}
			dbdump "${DBNAMES}" "${BACKUPDIR}/daily/${DATE}.${DOW}.sql"
			[ $? -eq 0 ] && {
				${ECHO} Rotating last weeks Backup...
				${FIND} "${BACKUPDIR}/daily" -mtime +6 -type f -exec ${RM} -v {} \; 
			}
			compression "${BACKUPDIR}/daily/${DATE}.${DOW}.sql"
			BACKUPFILES="${BACKUPFILES} ${BACKUPDIR}/daily/${DATE}.${DOW}.sql${SUFFIX}"
		${ECHO} ----------------------------------------------------------------------
	fi
${ECHO} Backup End Time `${DATEC}`
${ECHO} ======================================================================
fi
${ECHO} Total disk space used for backup storage..
${ECHO} Size - Location
${ECHO} `${DU} -hs "${BACKUPDIR}"`
${ECHO}
${ECHO} ======================================================================
${ECHO} If you find AutoMySQLBackup valuable please make a donation at
${ECHO} http://sourceforge.net/project/project_donations.php?group_id=101066
${ECHO} ======================================================================

# Run command when we're done
if [ "${POSTBACKUP}" ]
	then
	${ECHO} ======================================================================
	${ECHO} "Postbackup command output."
	${ECHO}
	eval ${POSTBACKUP}
	${ECHO}
	${ECHO} ======================================================================
fi

#Clean up IO redirection
exec 1>&6 6>&-      # Restore stdout and close file descriptor #6.
exec 2>&7 7>&-      # Restore stdout and close file descriptor #7.

if [ "${MAILCONTENT}" = "files" ]
then
	if [ -s "${LOGERR}" ]
	then
		# Include error log if is larger than zero.
		BACKUPFILES="${BACKUPFILES} ${LOGERR}"
		ERRORNOTE="WARNING: Error Reported - "
	fi
	#Get backup size
	ATTSIZE=`${DU} -c ${BACKUPFILES} | ${GREP} "[[:digit:][:space:]]total$" |${SED} s/\s*total//`
	if [ ${MAXATTSIZE} -ge ${ATTSIZE} ]
	then
		BACKUPFILES=`${ECHO} "${BACKUPFILES}" | ${SED} -e "s# # -a #g"`	#enable multiple attachments
		mutt -s "${ERRORNOTE} MySQL Backup Log and SQL Files for ${HOST} - ${DATE}" ${BACKUPFILES} ${MAILADDR} < ${LOGFILE}		#send via mutt
	else
		${CAT} "${LOGFILE}" | mail -s "WARNING! - MySQL Backup exceeds set maximum attachment size on ${HOST} - ${DATE}" ${MAILADDR}
	fi
elif [ "${MAILCONTENT}" = "log" ]
then
	${CAT} "${LOGFILE}" | mail -s "MySQL Backup Log for ${HOST} - ${DATE}" ${MAILADDR}
	if [ -s "${LOGERR}" ]
		then
			${CAT} "${LOGERR}" | mail -s "ERRORS REPORTED: MySQL Backup error Log for ${HOST} - ${DATE}" ${MAILADDR}
	fi	
elif [ "${MAILCONTENT}" = "quiet" ]
then
	if [ -s "${LOGERR}" ]
		then
			${CAT} "${LOGERR}" | mail -s "ERRORS REPORTED: MySQL Backup error Log for ${HOST} - ${DATE}" ${MAILADDR}
			${CAT} "${LOGFILE}" | mail -s "MySQL Backup Log for ${HOST} - ${DATE}" ${MAILADDR}
	fi
else
	if [ -s "${LOGERR}" ]
		then
			${CAT} "${LOGFILE}"
			${ECHO}
			${ECHO} "###### WARNING ######"
			${ECHO} "Errors reported during AutoMySQLBackup execution.. Backup failed"
			${ECHO} "Error log below.."
			${CAT} "${LOGERR}"
	else
		${CAT} "${LOGFILE}"
	fi	
fi

if [ -s "${LOGERR}" ]
	then
		STATUS=1
	else
		STATUS=0
fi

# Clean up Logfile
eval ${RM} -f "${LOGFILE}"
eval ${RM} -f "${LOGERR}"

exit ${STATUS}


```

---

### Post by SeijiSensei on 2010-09-28
> **Vegan said:**
> ```

#!/bin/bash
#
# MySQL Backup Script
# VER. 2.5.1 - http://sourceforge.net/projects/automysqlbackup/
# Copyright (c) 2002-2003 wipe_out@lycos.co.uk

```

That's not my script; I'm guessing it's the one you said you downloaded from the Internet.  I posted my script [above]("http://ubuntuforums.org/showpost.php?p=9882114&postcount=5").  I can help you with mine, but it's too much effort to debug someone else's script.

---

### Post by Vegan on 2010-09-28
```

date +%Y%m%d
mysqldump -u root -p********* --all-databases > /public/backup/"`date`.sql"

```

---

### Post by Vegan on 2010-09-28
That script is now making a full dump to the desired path. And I have added a cd to the target and called gzip to compress *.sql and then remove and uncompressed files.

So now I only need some code to remove gziped files based on age, say < 90 days from today.

---

### Post by SeijiSensei on 2010-09-28
> **Vegan said:**
> So now I only need some code to remove gziped files based on age, say < 90 days from today.

Something like this

```

ROTATE=90
STALE=`date --date="$ROTATE days ago"`
rm -f "/public/backup/$STALE.sql"

```

---

### Post by Vegan on 2010-09-29
Here is the latest version of the bash script needed to achieve the solution in my original post.

```

#backup MySQL to a date named file
mysqldump -u root -p******** --all-databases > "/public/backup/`date +%Y%m%d`$
cd /public/backup
gzip *.sql
chmod 777 *.*
#remove older backups so as not to consume infinite space
#90 days is plenty, but a variable is used to make modification easy
ROTATE=90
STALE=`date --date="$ROTATE days ago"`
rm -f "/public/backup/$STALE.sql.gz"

```

---

### Post by Vegan on 2010-09-29
Now some additional tweaks would be helpful

Such as force overwrite of an existing file when the dump is being tested and developed

The gzip will not choke if there is nothing to do

I yanked the rm *,sql as gzip seemed to know I wanted the file moved into the archive.

So now the script spits out what I wanted, 20100929.sql.gz is now today's backup. The default name is usable, but not what I was seeking. So using the suggested data argv make the name what I wanted.

Th script is far briefer than the other offerings, but mine is rather specialized to my needs. Still its documented enough in this thread for most to modify it to their need with out additional advise.

I now have the script sym-linked to /etc/cron.daily and I hope it works fine for everyone.

---

### Post by SeijiSensei on 2010-09-29
You didn't capture the entire mysqldump line from the screen before pasting; that's why it ends in a "$".

The file will be overwritten automatically unless you mark it read-only.  You can run this script multiple times on the same day and get a new file each time.

To test for the existence of a file use the -s test in a bash if construct like this:

```

if [ -s /path/to/myfile ]
then
     do stuff
else 
     do other stuff or nothing
fi

``` 

That is true when the file exists and has a non-zero size.  Use -a if you only want to test for existence.

See the section called CONDITIONAL EXPRESSIONS in the bash man page ("man bash" at a prompt).  In my copy it's around line 1800.

---

### Post by Vegan on 2010-09-29
Thanks for all of the help.

I am trying to backup, a mundane task.

next idea is to tar the web site folder to the same target

cd /public/backup
tar -cf 'date +%Y%m%d'.tar /www
gzip *.tar

tar by default will recursively collect everything into the archive which is perfect

so bolting that onto the script gives is 2x backups, the /www folder and the server's database.

---

