---
title: "Backup Script"
date: 2012-05-03
forum: Server Platforms
---

### Post by maverickaddicted on 2012-05-03
Hello,

I found one backup shell script on the Internet for creating backups of the directory and mysql databases. I modified the script according to my need. However I am getting following error messages when running the script -

```

serveradmin@openserver:~/$ sudo sh backup.sh
backup.sh: 32: $: not found
backup.sh: 34: $: not found
backup.sh: 38: $: not found
backup.sh: 38: $: not found

```

Here is the script -

```

serveradmin@openserver:~/$ cat backup.sh
#!/bin/bash
# Path to backup directories
DIRS="/home/serveradmin/LAMP/ /home/developer/public_html/ /home/wranglers/"
# Store todays date
NOW=$(date +"%F")
# Store backup path
BACKUP="/home/serveradmin/backup/"
# Backup file name hostname.time.tar.gz
BFILE="$(hostname).$(date +'%T').tar.gz"
# PFILE="$(hostname).$(date +'%T').pg.sql.gz"
MFILE="$(hostname).$(date +'%T').mysql.sq.gz"
# Set Pgsql username
# PGSQLUSER="username"
# Set MySQL username and password
MYSQLUSER="root"
MYSQLPASSWORD="mypassword"
# Remote SSH server setup
# SSHSERVER="example.com" # your remote ssh server
# SSHUSER="username"                # username
# SSHDUMPDIR="/remote/server/path/"    # remote ssh server directory to store dumps
# Paths for binary files
TAR="/bin/tar"
PGDUMP="/usr/bin/pg_dump"
MYSQLDUMP="/usr/bin/mysqldump"
GZIP="/bin/gzip"
SCP="/usr/bin/scp"
SSH="/usr/bin/ssh"
LOGGER="/usr/bin/logger"
# make sure backup directory exists
[ ! -d "$BACKUP" ] && mkdir -p "${BACKUP}"
# Log backup start time in /var/log/messages
$ LOGGER "$0: *** Backup started @ $(date) ***"
# Backup websever dirs
$ TAR -zcvf "${BACKUP}/${BFILE}" "${DIRS}"
# Backup PgSQL
# $PGDUMP -x -D -U${PGSQLUSER} | $GZIP -c > ${BACKUP}/${PFILE}
# Backup MySQL
$ MYSQLDUMP -u "${MYSQLUSER}" -h localhost -p "${MYSQLPASSWORD}" --all-databases | $ GZIP -9 > [datbasebackup.sql.gz]

```

Can anyone please help me out?

---

### Post by Hakunka-Matata on 2012-05-03
It looks like you are trying to start the shell script program incorrectly.  Sure you don't need bash?, like
sudo bash backup.sh

And it may be that backup.sh in not in your PATH.  If the backup.sh file is in e.g. "/backup"  then the command to run the program from your home directory would be:
sudo bash /backup/backup.sh

But I feel a bit stupid telling you these things, you likely know the system better than I do.
Good Luck

---

### Post by Hakunka-Matata on 2012-05-03
What does your first command do?

sudo sh

---

### Post by Jonathan L on 2012-05-03
Hi maverickaddicted

[```

serveradmin@openserver:~/$ sudo sh backup.sh
backup.sh: 32: $: not found
backup.sh: 34: $: not found
backup.sh: 38: $: not found
backup.sh: 38: $: not found

```Here is the script -
It's complaining that on lines, 32, 34, and 38 (twice) that it doesn't know the command called literally "$".  Because you're using variables for all your commands that you have the dollar signs, and a space has crept in between the dollar and the variable name: just remove those spaces.

```

...
# Log backup start time in /var/log/messages
[COLOR=Red]$LOGGER "$0: *** Backup started @ $(date) ***"[/COLOR]
# Backup websever dirs
[COLOR=Red]$TAR -zcvf "${BACKUP}/${BFILE}" "${DIRS}"[/COLOR]
# Backup PgSQL
# $PGDUMP -x -D -U${PGSQLUSER} | $GZIP -c > ${BACKUP}/${PFILE}
# Backup MySQL
[COLOR=Red]$MYSQLDUMP -u "${MYSQLUSER}" -h localhost -p "${MYSQLPASSWORD}" --all-databases | $GZIP -9 > datbasebackup.sql.gz[/COLOR]

```You'll also need to remove the square brackets on the MySQL line, and probably wanted the $BACKUP directory in there:
```
... > [COLOR=Red]${BACKUP}/datbasebackup.sql.gz[/COLOR]
```[COLOR=Red]
[COLOR=Black]
Can I ask why you've used variables for the commands?  (I'm guessing to hide the absolute paths, which you're using because you're trying to get this run by crontab?)

Especially for backup scripts, readability is important. Because your filenames are sensible (no spaces or unusual characters), you can simply omit all the quotes and brackets for the variables, and perhaps the following is helpful for you:
[/COLOR][/COLOR]```
#!/bin/sh

if [ $# -lt 2 ]; then
    echo "Usage: destdir backupdirs..."
    echo "  also backs up mysql into the destdir"
    exit 1
fi
BACKUP=$1
shift

# where and when
#
NOW=$(/bin/date +"%Y%m%d-%H%M")
HOST=$(/bin/hostname)

# directory and filenames for backups
#
BFILE=$BACKUP/$HOST.$NOW.tar.gz
MFILE=$BACKUP/$HOST.$NOW.mysql.gz

# mysql credentials
#
DBUSER=root
DBPW=mypassword

/usr/bin/logger "$0: *** Backup started ***"

# make directory, back up files, back up db
#
/bin/mkdir -p $BACKUP
/bin/tar -zcvf $BFILE $*
/usr/bin/mysqldump -u $DBUSER -h localhost -p $DBPW --all-databases \
    | /bin/gzip -9 \
    > $MFILE

/usr/bin/logger "$0: *** Backup finished ***"
```[COLOR=Red][COLOR=Black]

Stick it somewhere like ~serveradmin/bin/dobackup.sh or /root/dobackup.sh and run it, perhaps from crontab as:
[/COLOR][/COLOR]```
0 3 * * * /root/dobackup.sh /home/serveradmin/backup /home/serveradmin/LAMP /home/developer/public_html /home/wranglers

```[COLOR=Red][COLOR=Black]
[/COLOR][/COLOR][COLOR=Red][COLOR=Black]
If you are running from cron but don't like all the absolute paths (personally I think it's ugly), put this at the top of your crontab:
PATH=/usr/sbin:/usr/bin:/sbin:/bin


Hope that's helpful.

Kind regards,
Jonathan.
[/COLOR][/COLOR]

---

### Post by Hakunka-Matata on 2012-05-03
Thanks to **Jonathan L**.  

#I post stupid things in an effort to help, then
#Someone nice replies with intelligent good information
#I thank you, pretty cheap way to learn, but learn I did.

THanks again.

---

### Post by CharlesA on 2012-05-03
> **Hakunka-Matata said:**
> What does your first command do?

sudo sh
It's the wrong way to run a shell script. ;)

@Jonathan: Good catch with the spaces. +1 to keeping the least amount of variables.

Altho my backup script is probably pretty poor looking, all it does is rsync, without doing anything with databases.

---

### Post by LHammonds on 2012-05-03
When executing a script or scheduling one, always use the full path.  You can use a . to shorten it if you know what you are doing but like I said, use the full path to avoid problems.

Full path example:

/var/scripts/runme.sh
or
sudo /var/scripts/runme.sh

Short path example:

./runme.sh
or
sudo ./runme.sh

The short path example will ONLY work if you are currently "in" the directory where the script is located.

--------------------------------------------------------------------

I looked around the web for backup scripts too but nothing did exactly what I wanted so I made up my own...centralized around the mysql dump command.

Here is the schedule that runs my backup every day at 11pm.  I have it saved to a file so I can archive changes to the schedule.  I then load it by typing something similar to crontab -u root /var/scripts/prod/crontab.root

```

########################################
# Name: Crontab Schedule for root user
# Author: LHammonds
# To enable, type: crontab -u root crontab.root
# To disable, type: crontab -u root emptyfile
############# Update Log ###############
# 2011-12-19 - LTH - Created schedule
########################################

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow command

#
# Backup MySQL to a local folder, archive and store offsite.
#
0 23 * * * /var/scripts/prod/mysql-backup.sh > /dev/null 2>&1

```I also use a standard "include" file to keep a single place for all my global variables and functions.

/var/scripts/common/standard.conf
```

## Global Variables ##
TEMPDIR="/var/temp"
SHAREDIR="/srv/samba/share"
MYDOMAIN="example.com"
ADMINEMAIL="admin@${MYDOMAIN}"
REPORTEMAIL="lhammonds@${MYDOMAIN}"
BACKUPDIR="/var/backup"
OFFSITEDIR="/mnt/backup"
OFFSITETESTFILE="${OFFSITEDIR}/online.txt"
ARCHIVEMETHOD="tar.7z"    ## Choices are tar.7z or tgz
HOSTNAME=$(hostname -s)
SCRIPTNAME=$0
MAILFILE="${TEMPDIR}/mailfile.$$"

## Global Functions ##

function f_sendmail()
{
  ## Purpose: Send email message.
  ## Parameter #1 = Subject
  ## Parameter #2 = Body
  sendemail -f "${ADMINEMAIL}" -t "${REPORTEMAIL}" -u "${1}" -m "${2}\n\nServer: ${HOSTNAME}\nProgram: ${SCRIPTNAME}\nLog: ${LOGFILE}" -s mailserver:25 1>/dev/null 2>&1
}

function f_mount()
{
  ## Mount the pre-configured Windows share folder.
  ## NOTE: The Windows share should have a file called "online.txt"
  if [ ! -f ${OFFSITEDIR}/online.txt ]; then
    mount -t cifs //srv-winbackup/mysql ${OFFSITEDIR} --options nouser,rw,nofail,noatime,noexec,credentials=/etc/cifspw
  fi
}

function f_umount()
{
  ## Dismount the Windows share folder.
  ## NOTE: The unmounted folder should have a file called "offline.txt"
  if [ -f ${OFFSITEDIR}/online.txt ]; then
    umount ${OFFSITEDIR}
  fi
}

```The mount stuff above simply mounts a Windows share where I save my offsite files.

And here is the script I use to backup my database.  The archives are stored offsite and whenever there is not enough room at the offsite location to copy the archive, it goes through and removes the oldest archives until there is enough room.  That means you can go back to an old archive as far back as your storage space will allow.

/var/scripts/prod/mysql-backup.sh
```

#!/bin/bash
#############################################
## Name          : mysql-backup.sh
## Version       : 1.1
## Date          : 2012-01-09
## Author        : LHammonds
## Purpose       : Complete backup of MySQL database.
## Compatibility : Verified on Ubuntu Server 10.04.3 LTS, MySQL 5.1.41
## Requirements  : p7zip-full (if ARCHIVEMETHOD=tar.7z), sendemail
## Run Frequency : Once per day after hours or as needed (will not shutdown service)
## Exit Codes    : (if multiple errors, value is the addition of codes)
##    0 = success
##    1 = 7zip not installed
##    2 = archive failure
##    4 = archive purge failure
##    8 = configuration error
##   16 = mount warning
################ CHANGE LOG #################
## DATE       WHO WHAT WAS CHANGED
## ---------- --- ----------------------------
## 2011-12-19 LTH Created script.
## 2012-01-09 LTH Bugfix - f_PurgeOldestArchive
#############################################

## Import common variables and functions. ##
source /var/scripts/common/standard.conf

LOGFILE="${TEMPDIR}/mysql-backup.log"
LOCKFILE="${TEMPDIR}/mysql-backup.lock"
TARGETDIR="${BACKUPDIR}/mysql"
OFFSITEBACKDIR="${OFFSITEDIR}/mysql"
ARCHIVEFILE="`date +%Y-%m-%d-%H-%M`_mysql-backup.${ARCHIVEMETHOD}"
ERRORFLAG=0

#######################################
##            FUNCTIONS              ##
#######################################
function f_PurgeOldestArchive()
{
  ## Purpose: Delete the oldest archive on the remote site.
  ## Return values:
  ##    0 = Success
  ##    1 = Cannot delete file
  ##    9 = Configuration error, path empty

  ## Variable Error Check. *
  if [ ${OFFSITEBACKDIR} = "" ]; then
    ## Make darn sure the path is not empty since we do NOT
    ## want to start purging files from a random location.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- Purge error: OFFSITEBACKDIR site variable is empty!" >> ${LOGFILE}
    return 9
  fi
  ## Get the name of the oldest file.
  OLDESTFILE=`ls -1t ${OFFSITEBACKDIR} | tail -1`
  if [ "${OLDESTFILE}" = "" ]; then
    ## Error. Filename variable empty.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- Purge error: OLDESTFILE variable is empty." >> ${LOGFILE}
    return 9
  else   
    FILESIZE=`ls -lak "${OFFSITEBACKDIR}/${OLDESTFILE}" | awk '{ print $5 }' | sed -e :a -e 's/\(.*[0-9]\)\([0-9]\{3\}\)/\1,\2/;ta'`
    echo "`date +%Y-%m-%d_%H:%M:%S` --- Purging old file: ${OFFSITEBACKDIR}/${OLDESTFILE}, Size = ${FILESIZE} kb" >> ${LOGFILE}
    rm "${OFFSITEBACKDIR}/${OLDESTFILE}"
    if [ -f "${OFFSITEBACKDIR}/${OLDESTFILE}" ]; then
      ## File still exists.  Return error.
      return 1
    else
      return 0
    fi
  fi
}

function f_cleanup()
{
  echo "`date +%Y-%m-%d_%H:%M:%S` - MySQL backup exit code: ${ERRORFLAG}" >> ${LOGFILE}

  if [ -f ${LOCKFILE} ];then
    ## Remove lock file so other rsync jobs can run.
    rm ${LOCKFILE} 1>/dev/null 2>&1
  fi
  ## Email the result to the administrator.
  if [ ${ERRORFLAG} -eq 0 ]; then
    f_sendmail "MySQL Backup Success" "MySQL backup completed with no errors."
  else
    f_sendmail "MySQL Backup ERROR" "MySQL backup failed.  ERRORFLAG = ${ERRORFLAG}"
  fi
}

function f_emergencyexit()
{
  ## Purpose: Exit script as cleanly as possible.
  ## Parameter #1 = Error Code
  f_cleanup
  exit $1
}

#######################################
##           MAIN PROGRAM            ##
#######################################

## Binaries ##
TAR="$(which tar)"
MY7ZIP="$(which 7za)"
MYSQL="$(which mysql)"
MYSQLDUMP="$(which mysqldump)"

if [ -f ${LOCKFILE} ]; then
  ## Program lock file detected.  Abort script.
  f_sendmail "MySQL Backup Aborted - Lock File" "This script tried to run but detected the lock file: ${LOCKFILE}\n\nPlease check to make sure the file does not remain when this script is not actually running."
  exit 1
else
  ## Create the lock file to ensure only one script is running at a time.
  echo "`date +%Y-%m-%d_%H:%M:%S` ${SCRIPTNAME}" > ${LOCKFILE}
fi

echo "`date +%Y-%m-%d_%H:%M:%S` - MySQL backup started." >> ${LOGFILE}

## If the 7-Zip archive method is specified, make sure the package is installed.
if [ "${ARCHIVEMETHOD}" = "tar.7z" ]; then
  if [ ! -f "/usr/bin/7za" ]; then
    ## Required package (7-Zip) not installed.
    echo "`date +%Y-%m-%d_%H:%M:%S` - CRITICAL ERROR: 7-Zip package not installed.  Please install by typing 'aptitude -y install p7zip-full'" >> ${LOGFILE}
    ERRORFLAG=1
    f_emergencyexit ${ERRORFLAG}
  fi
fi

echo "`date +%Y-%m-%d_%H:%M:%S` --- Partition status:" >> ${LOGFILE}
df -h >> ${LOGFILE}

## Document the current uptime.
${MYSQL} -e status | grep -i uptime >> ${LOGFILE}

StartTime="$(date +%s)"

echo "`date +%Y-%m-%d_%H:%M:%S` --- Space consumed in ${MYSQLDIR} = `du -sh ${MYSQLDIR} | awk '{ print $1 }'`" >> ${LOGFILE}

## Backup all databases.
${MYSQLDUMP} --all-databases > ${TARGETDIR}/mysql-all.sql

## Loop through every database.
DATABASES=$(echo "show databases;"|mysql --skip-column-names)
for DATABASE in ${DATABASES}
do
  if [ "${DATABASE}" != "information_schema" ]; then
    ## Backup individual database.
    ${MYSQLDUMP} ${DATABASE} > ${TARGETDIR}/${DATABASE}.sql
    ## Create database sub-folder.
    mkdir -p ${TARGETDIR}/${DATABASE}
    ## Export each table in the database individually.
    for TABLE in `echo "show tables" | $MYSQL ${DATABASE}|grep -v Tables_in_`;
    do
      FILE=${TARGETDIR}/${DATABASE}/${TABLE}.sql
      case "${TABLE}" in
        general_log)
          ${MYSQLDUMP} ${DATABASE} ${TABLE} --skip-lock-tables > ${FILE}
          ;;
        slow_log)
          ${MYSQLDUMP} ${DATABASE} ${TABLE} --skip-lock-tables > ${FILE}
          ;;
        *)
          ${MYSQLDUMP} ${DATABASE} ${TABLE} > ${FILE}
          ;;
      esac
    done
  fi
done

## Compress the backup into a single file based on archive method specified.
echo "`date +%Y-%m-%d_%H:%M:%S` --- Compressing archive: ${TEMPDIR}/${ARCHIVEFILE}" >> ${LOGFILE}
case "${ARCHIVEMETHOD}" in
tar.7z)
  ${TAR} -cpf - ${TARGETDIR} | ${MY7ZIP} a -si -mx=9 -w${TEMPDIR} ${TEMPDIR}/${ARCHIVEFILE} 1>/dev/null 2>&1
  RETURNVALUE=$?
  ## Restore using one of the following commands (do not uncomment, only for notation):
  ## 7za x -so -w/tmp ${TEMPDIR}/${ARCHIVEFILE} | tar -C / -xf -
  ## 7za x -so -w/tmp ${TEMPDIR}/${ARCHIVEFILE} | tar -C ${TEMPDIR}/restore --strip-components=1 -xf -
  ;;
tgz)
  ${TAR} -cpzf ${TEMPDIR}/${ARCHIVEFILE} ${TARGETDIR} 1>/dev/null 2>&1
  RETURNVALUE=$?
  ## Restore using one of the following commands (do not uncomment, only for notation):
  ## tar -C / -xzf ${TEMPDIR}/${ARCHIVEFILE}
  ## tar -C ${TEMPDIR}/restore --strip-components=1 -xzf ${TEMPDIR}/${ARCHIVEFILE}
  ;;
*)
  ${TAR} -cpzf ${TEMPDIR}/${ARCHIVEFILE} ${TARGETDIR} 1>/dev/null 2>&1
  RETURNVALUE=$?
  ;;
esac

if [ ${RETURNVALUE} -ne 0 ]; then
  ## tar command failed.  Send warning email.
  f_sendmail "MySQL Backup Failure - tar" "tar failed with return value of ${RETURNVALUE}"
  ERRORFLAG=$((${ERRORFLAG} + 2))
fi

## Mount the remote folder. ##
f_mount

if [ ! -f ${OFFSITETESTFILE} ]; then
  ## Could not find expected file on remote site.  Assuming failed mount.
  ERRORFLAG=$((${ERRORFLAG} + 16))
  echo "`date +%Y-%m-%d_%H:%M:%S` --- ERROR: Cannot detect remote location: ${OFFSITETESTFILE}" >> ${LOGFILE}
  f_emergencyexit ${ERRORFLAG}
fi

FREESPACE=`df -k ${OFFSITEDIR} | grep ${OFFSITEDIR} | awk '{ print $3 }'`
BACKUPSIZE=`ls -lak "${TEMPDIR}/${ARCHIVEFILE}" | awk '{ print $5 }'`

## Make sure space is available on the remote server to copy the file.
if [ ${FREESPACE} -lt ${BACKUPSIZE} ]; then
  ## Not enough free space available.  Purge existing backups until there is room.
  ENOUGHSPACE=0
  while [ ${ENOUGHSPACE} -eq 0 ]
  do
    f_PurgeOldestArchive
    RETURNVALUE=$?
    case ${RETURNVALUE} in
    1)
      ## Cannot purge archives to free up space.  End program gracefully.
      echo "`date +%Y-%m-%d_%H:%M:%S` - ERROR: Not enough free space on ${OFFSITEBACKDIR} and cannot purge old archives.  Script aborted." >> ${LOGFILE}
      ## Stop and exit the script with an error code.
      ERRORFLAG=$((${ERRORFLAG} + 4))
      f_emergencyexit ${ERRORFLAG}
      ;;
    9)
      ## Configuration error, end program gracefully.
      echo "`date +%Y-%m-%d_%H:%M:%S` - ERROR: Configuration problem. Script aborted." >> ${LOGFILE}
      ## Stop and exit the script with an error code.
      ERRORFLAG=$((${ERRORFLAG} + 8))
      f_emergencyexit ${ERRORFLAG}
      ;;
    esac
    FREESPACE=`df -k ${OFFSITEDIR} | grep ${OFFSITEDIR} | awk '{ print $3 }'`
    if [ ${FREESPACE} -gt ${BACKUPSIZE} ]; then
      ## Enough space is now available.
      ENOUGHSPACE=1
    else
      ## Not enough space is available yet.
      ENOUGHSPACE=0
    fi
  done
fi

## Copy the backup to an offsite storage location.
echo "`date +%Y-%m-%d_%H:%M:%S` --- Copying archive file to offsite location." >> ${LOGFILE}
cp ${TEMPDIR}/${ARCHIVEFILE} ${OFFSITEBACKDIR}/${ARCHIVEFILE} 1>/dev/null 2>&1
if [ ! -f ${OFFSITEBACKDIR}/${ARCHIVEFILE} ]; then
  ## NON-FATAL ERROR: Copy command did not work.  Send email notification.
  echo "`date +%Y-%m-%d_%H:%M:%S` --- WARNING: Remote copy failed. ${OFFSITEBACKDIR}/${ARCHIVEFILE} does not exist!" >> ${LOGFILE}
  f_sendmail "Offline RSync Backup Failure - Remote Copy" "Remote copy failed. ${OFFSITEBACKDIR}/${ARCHIVEFILE} does not exist\n\nBackup file still remains in this location: ${HOSTNAME}:${TEMPDIR}/${ARCHIVEFILE}"
else
  ## Remove local copy of the compressed backup file
  rm ${TEMPDIR}/${ARCHIVEFILE}
fi

## Unmount the Windows shared folder.
f_umount

## Calculate total time for backup.
FinishTime="$(date +%s)"
ElapsedTime="$(expr ${FinishTime} - ${StartTime})"
Hours=$((${ElapsedTime} / 3600))
ElapsedTime=$((${ElapsedTime} - ${Hours} * 3600))
Minutes=$((${ElapsedTime} / 60))
Seconds=$((${ElapsedTime} - ${Minutes} * 60))

echo "`date +%Y-%m-%d_%H:%M:%S` --- Total backup time: ${Hours} hour(s) ${Minutes} minute(s) ${Seconds} second(s)" >> ${LOGFILE}

echo "`date +%Y-%m-%d_%H:%M:%S` - Offline RSync backup completed." >> ${LOGFILE}

## Perform cleanup routine.
f_cleanup
## Exit with the combined return code value.
exit ${ERRORFLAG}

```Do whatever you want with it or ignore it completely.  But remember, have fun!
LHammonds

---

### Post by rubylaser on 2012-05-03
Those scripts look very well thought out.  Thanks for sharing.  It's not very often I see users rolling functions into their homemade scripts :)

---

### Post by Habitual on 2012-05-03
> **rubylaser said:**
> Those scripts look very well thought out...

+1 and I plan to use some of that code (with Credit, of course)

---

### Post by CharlesA on 2012-05-03
> **rubylaser said:**
> Those scripts look very well thought out.  Thanks for sharing.  It's not very often I see users rolling functions into their homemade scripts :)
Agreed.

Mine are just a mess!

```
#!/bin/bash

###
### daily.sh
### Script to backup RAID Array
### Created by Charles Auer
### Tested 03/22/2011
### Updated 03/22/2011
###

# Standard Variables
BIN=/bin/
USR=/usr/bin/
# Email Variable
EMAIL=email@domain
CELL=email@domain
# Backup Paths
ARRAYPATH=/array/
DAILYPATH=/daily/
HOME=/home/charles/
ERROR=${HOME}logs/daily_backup_error.log
# Date Variables
DATE=$(${BIN}date +%D)
FOLDER=$(${BIN}date +%m%d%Y)

# Get Date/Time backup started
STARTDATE=$(${BIN}date +%D)
STARTTIME=$(${BIN}date +%T)
START=$(date +%s)

# Check if RAID Array is mounted
if ${BIN}mountpoint -q $ARRAYPATH
# If Array is mounted, then mount both backup drives
  then
    { ${BIN}mount -t ext4 UUID=49a8cdd0-a4fd-43e5-9c6e-3a4a3363b770 $DAILYPATH; } 2> $ERROR || { echo "Mounting of backup drives failed" | ${USR}mail -s "Backup failed for $DATE" $EMAIL $CELL; exit; }
# If not, email me that the array isn't mounted and that the backup failed
  else
    { echo "Raid Array not mounted!" | ${USR}mail -s "RAID Array not mounted! Backup Failed for $DATE" $EMAIL $CELL; exit; }
fi

# Gather info about free space of drives
BEFOREFREE=$(${BIN}df -h | ${BIN}egrep '(Filesystem)|(sd)')

# Variables for Doc Backup
OLDDAILYNAME=$(${BIN}cat ${DAILYPATH}latest)
NEWDAILYDIR=$DAILYPATH$FOLDER
OLDDAILYDIR=$DAILYPATH$OLDDAILYNAME
DAILYLOG=${DAILYPATH}log/${FOLDER}.txt

# Check if Doc is mounted and if so, do a incremental backup of it.
if ${BIN}mountpoint -q $DAILYPATH
  then
    { ${BIN}cp --archive --link $OLDDAILYDIR $NEWDAILYDIR && echo $FOLDER > ${DAILYPATH}latest && ${USR}rsync --archive --itemize-changes --delete --log-file $DAILYLOG $ARRAYPATH --exclude dvds --exclude lost+found $NEWDAILYDIR; } 2> $ERROR || { ${BIN}cat $ERROR | ${USR}mail -s "Daily Backup failed for $DATE" $EMAIL $CELL; exit; }
fi

# Get Date/Time backup completed
STOPDATE=$(${BIN}date +%D)
STOPTIME=$(${BIN}date +%T)
END=$(date +%s)

# Gather info about free space of drives after backup is complete
AFTERFREE=$(${BIN}df -h | ${BIN}egrep '(Filesystem)|(sd)')

# Unmount backup drives
${BIN}umount $DAILYPATH #$DVDPATH

# Send email of success
# Based on backup notification by Demented ZA
# http://ubuntuforums.org/showthread.php?t=1701292
(echo "Backup started at:  $STARTDATE  $STARTTIME" && echo "Backup finished at: $STOPDATE  $STOPTIME" && echo && echo "Duration in seconds: $(($END-$START))" && echo && echo "Disk Usage Before Backup:" && echo && echo "$BEFOREFREE" && echo && echo "Disk Space After Backup:" && echo && echo "$AFTERFREE" ) | mail -s "Daily Backup Complete for $DATE" $EMAIL
# eof

```

---

### Post by maverickaddicted on 2012-05-04
> **LHammonds said:**
> When executing a script or scheduling one, always use the full path.  You can use a . to shorten it if you know what you are doing but like I said, use the full path to avoid problems.

Full path example:

/var/scripts/runme.sh
or
sudo /var/scripts/runme.sh

Short path example:

./runme.sh
or
sudo ./runme.sh

The short path example will ONLY work if you are currently "in" the directory where the script is located.

--------------------------------------------------------------------

I looked around the web for backup scripts too but nothing did exactly what I wanted so I made up my own...centralized around the mysql dump command.

Here is the schedule that runs my backup every day at 11pm.  I have it saved to a file so I can archive changes to the schedule.  I then load it by typing something similar to crontab -u root /var/scripts/prod/crontab.root


Hi Hammonds

Thank you providing the script. I will surely try once I get my script working, so as to acquire little more knowledge about shell scripts. Also this is my first shell script.

---

### Post by maverickaddicted on 2012-05-04
> **Jonathan L said:**
> Hi maverickaddicted

[```

serveradmin@openserver:~/$ sudo sh backup.sh
backup.sh: 32: $: not found
backup.sh: 34: $: not found
backup.sh: 38: $: not found
backup.sh: 38: $: not found

```Here is the script -
It's complaining that on lines, 32, 34, and 38 (twice) that it doesn't know the command called literally "$".  Because you're using variables for all your commands that you have the dollar signs, and a space has crept in between the dollar and the variable name: just remove those spaces.

```

...
# Log backup start time in /var/log/messages
[COLOR=Red]$LOGGER "$0: *** Backup started @ $(date) ***"[/COLOR]
# Backup websever dirs
[COLOR=Red]$TAR -zcvf "${BACKUP}/${BFILE}" "${DIRS}"[/COLOR]
# Backup PgSQL
# $PGDUMP -x -D -U${PGSQLUSER} | $GZIP -c > ${BACKUP}/${PFILE}
# Backup MySQL
[COLOR=Red]$MYSQLDUMP -u "${MYSQLUSER}" -h localhost -p "${MYSQLPASSWORD}" --all-databases | $GZIP -9 > datbasebackup.sql.gz[/COLOR]

```You'll also need to remove the square brackets on the MySQL line, and probably wanted the $BACKUP directory in there:
```
... > [COLOR=Red]${BACKUP}/datbasebackup.sql.gz[/COLOR]
```[COLOR=Red]
[COLOR=Black]
Can I ask why you've used variables for the commands?  (I'm guessing to hide the absolute paths, which you're using because you're trying to get this run by crontab?)


Hi Jonathan,

I modified my script as you have shown. I wanted to provide the directory path inside the file, there is some reason for doing that. But for other backups I will be doing the same as you have given in the code. Now, I am facing this problem -

/home/designer/public_html/fashion/temp0016/wp-links-opml.php
/bin/tar: /home/wranglers\r\r: Cannot stat: No such file or directory
/bin/tar: Exiting with failure status due to previous errors

I don't know why it is taking \r\r after the directory name?

The modified code is - 
```

#!/bin/bash
# Path to backup directories
DIRS="/home/serveradmin/LAMP/ /home/designer/public_html/ /home/wranglers/"
# Store todays date
NOW=$(/bin/date +"%Y%m%d-%H%M")
# Store backup path
BACKUP="/home/serveradmin/backup/"
# Backup file name hostname.time.tar.gz
BFILE="$(hostname)-$NOW.tar.gz"
echo $BFILE
# PFILE="$(hostname).$NOW.pg.sql.gz"
BPATH="$BACKUP$BFILE"
echo $BPATH
MFILE="$(hostname)-$NOW.mysql.sq.gz"
# Set Pgsql username
# PGSQLUSER="username"
# Set MySQL username and password
MYSQLUSER="root"
MYSQLPASSWORD="123india"
# Remote SSH server setup
# SSHSERVER="192.168.1.156" # your remote ssh server
# SSHUSER="nexusadmin"                # username
# SSHDUMPDIR="/home/nexusadmin/Desktop/openserverbackup/"    # remote ssh server directory to store dumps
# make sure backup directory exists
# Log backup start time in /var/log/messages
/usr/bin/logger "$0: *** Backup started @ $(date) ***"
# Backup websever dirs
/bin/tar -cvzf $BPATH $DIRS
# Backup PgSQL
# $PGDUMP -x -D -U${PGSQLUSER} | $GZIP -c > ${BACKUP}/${PFILE}
# Backup MySQL
/usr/bin/mysqldump -u $MYSQLUSER -h localhost -p $MYSQLPASSWORD --all-databases | /bin/gzip -9 > $MFILE
/usr/bin/logger "$0: *** Backup finished ***"

```

---

### Post by LHammonds on 2012-05-04
> **rubylaser said:**
> Those scripts look very well thought out.   Thanks for sharing.  It's not very often I see users rolling functions  into their homemade scripts :smile:
  Thank you.  I've been trained long ago in the arcane arts of computer science.  Old habits are hard to break.

 > **Habitual said:**
> +1 and I plan to use some of that code (with Credit, of course)
 Good luck and have fun!

> **CharlesA said:**
> Agreed.
Thank you.

> **maverickaddicted said:**
> 
Thank you providing the script. I will surely try once I get my script working, so as to acquire little more knowledge about shell scripts. Also this is my first shell script.
You are quite welcome.  My code is littered with comments mainly because the code starts off with plain English of what I am trying to accomplish, it then turns into a pseudo-code to better match the language I am going to implement but without worry about specific syntax.  The next phase of creation is the actual coding with correct syntax...however, the main things that "do" stuff remains commented out or are turned into echo statements.  The reason is that I like to have all of my code's framework in place so I can test various events to make sure everything flows the way I expect.  It is very helpful to have echo statements sending debug info to the screen and/or log file at this point.  Once I am satisfied that everything is working as it should, the last step is to enable the commands that actually "do" stuff such as dumping sql tables, creating archives, etc.

If you need any help, figuring things out, the man pages are excellent places to get detailed info about commands.  And of course keeping your eye out during google searches for code can help you better understand how things can be done differently.  There are usually many ways to achieve the same result and sneaking a peek at how other people do things can often give you an edge on being able to improve / tweak how you do things.  Having more tools than just a hammer in your toolbox is always advised. ;)

**EDIT:** Oh, one last thing, if you want to know how my server is setup, along with how the samba and Windows shares are created, you can find them in a thread called [My Notes on Installing Zimbra on Ubuntu Server]("http://www.zimbra.com/forums/installation/56367-my-notes-installing-zimbra-ose-ubuntu-server-10-04-lts.html").

Have fun,
LHammonds

---

### Post by maverickaddicted on 2012-05-05
Any idea about the error?

---

### Post by CharlesA on 2012-05-05
> **maverickaddicted said:**
> Any idea about the error?
After running the script, run this:

```
echo $DIRS
```

That should tell you if that variable is doing what you think it is doing.

---

### Post by Hakunka-Matata on 2012-05-05
Your wonder about 
#/bin/tar: /home/wranglers\r\r

For what it's worth, I ran your script and got the same error.  I did fix it by adding my username into the path.  e.g.```
Code:
#!/bin/bash
################################################################################################################
#
# Modified backup script from ubuntu forums.
#
################################################################################################################
# Path to backup directories
DIRS="/home/[COLOR="Red"]**das**[/COLOR]/Pictures/ /home/[COLOR="Red"]**das**[/COLOR]/Public/"
echo $DIRS
###### AND SO FORTH

```

the .sh file is on the Desktop, and I started it from "das@M5A78L-1204-64:~$ " 

OS: Linux M5A78L-1204-64 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux 
seems too simple a solution, but it does work for me

---

### Post by LHammonds on 2012-05-05
> **maverickaddicted said:**
> Any idea about the error?
CharlesA gave you some good advice.

When building a script, I recommend testing the flow first to make sure it will do what you "think" it should be doing.  In this case, echo commands and variables so you can see what the script sees.

Example:
```

#!/bin/bash
# Path to backup directories
DIRS="/home/serveradmin/LAMP/ /home/designer/public_html/ /home/wranglers/"
[COLOR=Red]echo "DEBUG: DIRS=${DIRS}"[/COLOR]
# Store todays date
NOW=$(/bin/date +"%Y%m%d-%H%M")
[COLOR=Red]echo "DEBUG: NOW=${NOW}"[/COLOR]
# Store backup path
BACKUP="/home/serveradmin/backup/"
# Backup file name hostname.time.tar.gz
BFILE="$(hostname)-$NOW.tar.gz"
[COLOR=Red]echo "DEBUG: BFILE=${BFILE}"[/COLOR]
# PFILE="$(hostname).$NOW.pg.sql.gz"
BPATH="$BACKUP$BFILE"
[COLOR=Red]echo "DEBUG: BPATH=${BPATH}"[/COLOR]
MFILE="$(hostname)-$NOW.mysql.sq.gz"
[COLOR=Red]echo "DEBUG: MFILE=${MFILE}"[/COLOR]
# Set Pgsql username
# PGSQLUSER="username"
# Set MySQL username and password
MYSQLUSER="root"
MYSQLPASSWORD="123india"
# Remote SSH server setup
# SSHSERVER="192.168.1.156" # your remote ssh server
# SSHUSER="nexusadmin"                # username
# SSHDUMPDIR="/home/nexusadmin/Desktop/openserverbackup/"    # remote ssh server directory to store dumps
# make sure backup directory exists
# Log backup start time in /var/log/messages
/usr/bin/logger "$0: *** Backup started @ $(date) ***"
# Backup websever dirs
[COLOR=Red]echo "DEBUG: /bin/tar -cvzf $BPATH $DIRS"[/COLOR]
/bin/tar -cvzf $BPATH $DIRS
# Backup PgSQL
# $PGDUMP -x -D -U${PGSQLUSER} | $GZIP -c > ${BACKUP}/${PFILE}
# Backup MySQL
[COLOR=Red]echo "DEBUG: /usr/bin/mysqldump -u $MYSQLUSER -h localhost -p $MYSQLPASSWORD --all-databases | /bin/gzip -9 into $MFILE"[/COLOR]
/usr/bin/mysqldump -u $MYSQLUSER -h localhost -p $MYSQLPASSWORD --all-databases | /bin/gzip -9 > $MFILE
/usr/bin/logger "$0: *** Backup finished ***"

```

---

### Post by maverickaddicted on 2012-05-07
Thank you for the reply. Here is the output, when I ran the script with echo command -

```

serveradmin@openserver:~/Desktop$ sudo sh ./backup.sh 
[sudo] password for serveradmin: 
DEBUG: DIRS=/home/serveradmin/LAMP/ /home/designer/public_html/ /home/wranglers/

DEBUG: NOW=20120507-1243

.tar.gzBFILE=openserver-20120507-1243

.tar.gzver-20120507-1243radmin/backup/

.mysql.sq.gz=openserver-20120507-1243

 /home/serveradmin/LAMP/ /home/designer/public_html/ /home/wranglers/

/bin/tar: Removing leading `/' from member names
/bin/tar: /home/serveradmin/LAMP/ /home/designer/public_html/ /home/wranglers/\r\r: Cannot stat: No such file or directory
/bin/tar: Exiting with failure status due to previous errors
.mysql.sq.gz0120507-1243gzip -9 into /home/serveradmin/backup

```

Also, This path, /home/wranglers/, is correct, wranglers is the username.

---

### Post by CharlesA on 2012-05-07
Does tar work fine if you remove /home/wranglers/ ?

The \r looks like a line return.

[http://stackoverflow.com/questions/73833/how-do-you-search-for-files-containing-dos-line-endings-crlf-with-grep-under-l](http://stackoverflow.com/questions/73833/how-do-you-search-for-files-containing-dos-line-endings-crlf-with-grep-under-l)

---

### Post by LHammonds on 2012-05-07
Now that I can access my Linux server, I copied the debug script in my prior post and made a few modifications to fit my environment for testing.  I ran just fine.  The only thing I can think of is that you have some Windows-formatted lines in your script.

Open your script in the VI editor.  Type the following to set everything to "DOS" format:

```
:set ff=dos
```

Save and exit the file.

Now open the file again with VI.  You should see [dos] at the bottom beside the filename.

Now change it back to unix format with the following command:

```
:set ff=unix
```

Save and exit the file.

See if this fixes your problem.

LHammonds

---

### Post by maverickaddicted on 2012-05-08
> **CharlesA said:**
> Does tar work fine if you remove /home/wranglers/ ?

The \r looks like a line return.

[http://stackoverflow.com/questions/73833/how-do-you-search-for-files-containing-dos-line-endings-crlf-with-grep-under-l](http://stackoverflow.com/questions/73833/how-do-you-search-for-files-containing-dos-line-endings-crlf-with-grep-under-l)

I have already tried that but it gives the same error.

> **LHammonds said:**
> Now that I can access my Linux server, I copied the debug script in my prior post and made a few modifications to fit my environment for testing.  I ran just fine.  The only thing I can think of is that you have some Windows-formatted lines in your script.

Open your script in the VI editor.  Type the following to set everything to "DOS" format:



Yeah, you are right. The problem is that only. I have created the file on windows machine. I rewrote the script in vi editor and its worked but not completely.
Getting this on the console, however the archive is getting created and I am able to extract it.

```
/bin/tar: Removing leading `/' from member names
```

second problem is mysqldump, it is not dumping all the databases in the files. Here is the content of the file created by mysqldump

```

Usage: mysqldump [OPTIONS] database [tables]
OR     mysqldump [OPTIONS] --databases [OPTIONS] DB1 [DB2 DB3...]
OR     mysqldump [OPTIONS] --all-databases [OPTIONS]
For more options, use mysqldump --help

```

Here is the edited script file - 
```

serveradmin@openserver:~$ cat backupnew.sh
#!/bin/bash
# List of Directories to backup
dirs="/home/serveradmin/LAMP/ /home/designer/public_html/ /home/wranglers/"
# echo "DEBUG: dirs = $dirs"
# Backup Date and Time
now=$(/bin/date +"%d%m%Y-%H%M")
# echo "DEBUG: now = $now"
# Hostname of server
hostname="$(hostname -s)"
# echo "DEBUG: hostname = $hostname"
# Where to store backup files
backuppath=/home/serveradmin/backup/
# echo "backuppath = $backuppath"
# Backup file name
bfile="$hostname-$now.tar.gz"
# echo "DEBUG: bfile = $bfile"
# Database Backup file name
mfile="$hostname-$now.mysql.sq.gz"
# echo "DEBUG: mfile = $mfile"
# MySql username and password
mysqluser=root
mysqlpasswd=123india
# Generating Log files
/usr/bin/logger "@@@@@Backup Started on $(/bin/date) @@@@@"
# echo "/bin/tar -czf $backuppath$bfile -C / $dirs"
# Creating archive of directories
# /bin/tar -czf $backuppath$bfile -C / $dirs
# Creating DB backup using mysqldump and archiving it
/usr/bin/mysqldump -u $mysqluser -h localhost -p $mysqlpasswd --all-databases | /bin/gzip > $backuppath$mfile
# Backup finished successfully log entry
/usr/bin/logger "@@@@@ Backup Finished @@@@@"
serveradmin@openserver:~$ 

```

---

### Post by LHammonds on 2012-05-08
> **maverickaddicted said:**
> 
Getting this on the console, however the archive is getting created and I am able to extract it.

```
/bin/tar: Removing leading `/' from member names
```
I think you can safely ignore that.  I see that all the time.  I believe it says that for any folder that is "not" the root folder in order to keep the folder structure of what you want backed up...and not the entire path all the way back to the root.  However, always check to make sure your script is getting everything you "think" it should be getting.  Extract it somewhere and make sure you are getting all the files and folders you would expect.

I like comparing the source and target folders by issuing a "du -sh /foldername/" to do a quick filesize check for each folder I specify to backup.  You can also run commands to make sure the size count is accurate to the byte and count the number of files.  There are tons of ways to check things out.

> **maverickaddicted said:**
> 
second problem is mysqldump, it is not dumping all the databases in the files. Here is the content of the file created by mysqldump

```

Usage: mysqldump [OPTIONS] database [tables]
OR     mysqldump [OPTIONS] --databases [OPTIONS] DB1 [DB2 DB3...]
OR     mysqldump [OPTIONS] --all-databases [OPTIONS]
For more options, use mysqldump --help

```
That means it is not happy with the parameters you passed to it.

Looking at the man page, it seems like it "should" work with the settings you have defined but try running them manually at the command line to verify each base component.

At a command prompt, run just the mysqldump command as you have it defined to run:

```
/usr/bin/mysqldump -u root -h localhost -p 123india --all-databases
```You will notice that it gives you that same error that you are not doing something right.  If you keep playing with it and looking at other examples online, you will figure out that you need to run the command like this:

```
/usr/bin/mysqldump -uroot -hlocalhost -p123india --all-databases
```If you noticed in my script, I issued the following command:

```
mysqldump --all-databases
```Notice how the ID and Password are not exposed in the command.  Having them as parameters to the command can give away your credentials to anyone that can see the script or simply looking at the running processes which will also expose the ID/pass combo.  Best practice says to save this password in a personal "my.cnf" file in the user's home directory and lock it down so that only that user has access to the sensitive file.  Then modify your database configuration file to include the user config file.  Also note that you do not need to specify "localhost" since it will assume the local machine by default.

Here is an example of how configure mysql commands to be more secure:


[LIST=1]
[*]Make a personal mysql config file for the root user so the password is not required when running mysql commands
```

touch ~/my.cnf
chmod 0600 ~/my.cnf
vi ~/my.cnf
```
[*]Add the following lines to ~/my.cnf
```
[client]
password=type-my-password-here
```
[*]Edit the global mysql config file by typing **vi /etc/mysql/my.cnf**
[*]Add the following line to the very bottom:
```
!include ~/my.cnf
```
[*]Stop the mysql service by typing **service mysql stop**
[*]Start the mysql service by typing **service mysql start**
[*]Verify the service is running by typing either of the following two commands:
```
service mysql status
```or
```
netstat -tap | grep mysql
```
[*]See if the following command will work without prompting for a password: **mysqladmin status**
[/LIST]

---

### Post by maverickaddicted on 2012-05-10
> **LHammonds said:**
> 

[LIST=1]
[*]Make a personal mysql config file for the root user so the password is not required when running mysql commands
```

touch ~/my.cnf
chmod 0600 ~/my.cnf
vi ~/my.cnf
```
[*]Add the following lines to ~/my.cnf
```
[client]
password=type-my-password-here
```
[*]Edit the global mysql config file by typing **vi /etc/mysql/my.cnf**
[*]Add the following line to the very bottom:
```
!include ~/my.cnf
```
[*]Stop the mysql service by typing **service mysql stop**
[*]Start the mysql service by typing **service mysql start**
[*]Verify the service is running by typing either of the following two commands:
```
service mysql status
```or
```
netstat -tap | grep mysql
```
[*]See if the following command will work without prompting for a password: **mysqladmin status**
[/LIST]


Thank You, this solved the problem. Also tar is archiving it correctly, no problem there. Now I am wondering about modifying the script to take differential backup, is there any way to do that?

---

### Post by LHammonds on 2012-05-10
> **maverickaddicted said:**
> Thank YouYou're welcome.  ;)

> **maverickaddicted said:**
> Now I am wondering about modifying the script to take differential backup, is there any way to do that?
:-k  For that, you will need to look into [Binary Log backups]("http://dev.mysql.com/doc/refman/5.1/en/backup-methods.html").  If you go that route, make sure you test and document your restore methods.  Nothing is worse than finding out that your backup methods were flawed and that you cannot restore the way you thought you could.

LHammonds

---

### Post by CharlesA on 2012-05-10
> **LHammonds said:**
> :-k  For that, you will need to look into [Binary Log backups]("http://dev.mysql.com/doc/refman/5.1/en/backup-methods.html").  If you go that route, make sure you test and document your restore methods.  Nothing is worse than finding out that your backup methods were flawed and that you cannot restore the way you thought you could.

LHammonds

I do my backups a completely different way cuz they work for me and restoring from backups is dead simple too. ;)

---

