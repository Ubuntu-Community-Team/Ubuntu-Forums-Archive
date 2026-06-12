---
title: "MySQL to MariaDB Migration Walkthrough - Ubuntu 16.04 Server"
date: 2018-04-15
forum: Server Platforms
---

### Post by m-dw on 2018-04-15
I am looking to migrate/upgrade from MySQL to MariaDB.

I am running Ubuntu16.04LTS on a small headless server at home, having upgraded from 14.04. I'm not planning to go to 18.04, as I suspect I'll have new hardware in 3 years. I intend to stick to the default MariaDB version in the Ubuntu repositories which appears to be 10.0.

I've attempted the migration following instructions in this page: at [https://www.labsrc.com/migrating-from-mysql-5-7-to-mariadb-10-2-on-ubuntu-16-04/](https://www.labsrc.com/migrating-from-mysql-5-7-to-mariadb-10-2-on-ubuntu-16-04/).
 
The install process reported that the databases on my system weren't compatible with MariaDB10.0 and moved /var/lib/mysql to /var/lib/mysql.5.7. The install process didn't give me an opportunity to set a root password for Maria DB, and since the databases were moved, the previous root password was not carried over. Running mysql_upgrade failed reporting that the database had already been upgraded (probably it was looking at the newly created databases, not my original ones). Moving the moved files back to /var/lib/mysql didn't help because MariaDB wouldn't start.

Reverting back to MySQL was complicated because the passwords used by the dpkg scripts were missing in the MariaDB files. I was able to restore everything from backups and have fixed all the broken dependencies. No data was lost but I have a few more grey hairs.

I am now ready to try again, but obviously not using the same process. This gives rise to some questions:

[LIST]
[*]Should the upgrade have worked seamlessly or are MySQL 5.7 and MariaDB 10.0 incompatible? 
[*]If they are compatible, what stopped it? 
[*]I have empty files called debian-5.6.flag and debian-5.7.flag in the mysql data directory. Did the presence of 5.6.flag confuse the installer? 
[*]Would it be better to dump my databases with mysql-dump, remove MySQL completely, and restore the databases into a new MariaDB install? 
[/LIST]

Hope this gives enough for one of you gurus to diagnose my issue.

---

### Post by SeijiSensei on 2018-04-15
I'd take the dump and restore approach myself. I never migrate the binary representations of any database. Using the --all-databases switch in mysqldump makes it easy to do a complete backup and restore.

---

### Post by m-dw on 2018-04-15
I guessed that would be the prudent approach. I only have two databases defined (zoneminder and a shopping list app). Am I right to believe all the others are system databases which I won't need to restore?

---

### Post by LHammonds on 2018-04-15
Yes, just mysqldump your user databases.  No need to backup the system databases for migration.

It might also be a good idea to upgrade your "database" before changing out the database engine from MySQL to MariaDB.  I'd even do it again after you restore the database under the MariaDB system.

```

mysql_upgrade

```

Reference: [MySQL Manual]("https://dev.mysql.com/doc/refman/5.7/en/mysql-upgrade.html"), [MariaDB Manual]("https://mariadb.com/kb/en/library/mysql_upgrade/")

The nice thing about migrating from MySQL to MariaDB is that you won't need to change anything in your applications and you don't need to change any of your scripts that manage the database server either.

LHammonds

---

### Post by m-dw on 2018-04-16
It just occurred to me to ask... How would I backup and restore the users, passwords and grants?

---

### Post by SeijiSensei on 2018-04-16
If you use the --all-databases option, all those things will be taken care of.

---

### Post by LHammonds on 2018-04-16
> **m-dw said:**
> It just occurred to me to ask... How would I backup and restore the users, passwords and grants?

"--all-databases" is the main option to use for this.

You can also dump the "mysql" database as well but can be tricky with different database versions if not careful.

Another option is the percona-toolkit using the [pt-show-grants]("https://www.percona.com/doc/percona-toolkit/LATEST/pt-show-grants.html") command that can export the REVOKE, DROP and GRANT commands.

**EDIT:** Having more than one backup option is always a plus to me...which is why I like to backup entire partitions, export all databases in a single file, export individual databases to their own file and export all tables individually into separate folders based on database name.

LHammonds

---

### Post by LHammonds on 2018-04-16
I just wrote a script to automate the backup of the user privileges separate from (but in addition to) the mysqldump.

standard.conf - This is a config file I use to import commonly-used variables and functions.  It has been reduced to just what is used in these scripts to reduce clutter.

mysql-user-encrypt.sh - This extracts the SQL commands to re-create the privilege and encrypts it.  The "grant" file is just the grant commands (good for migrating to new server) and the "revoke" file is the revoke, drop and grant commands together (good to fix/restore permissions on same server).  This is designed to be automatically run via the root crontab schedule.  Use a passphrase isn't the most secure method but for my purposes, it is ok.  Nobody logs into the server other than the root user and the backup files shipped off to a remote location does not contain the decryption info.  The backup of the entire server is encrypted so it is safe at rest as well when offsite.

mysql-user-decrypt.sh - This script automates the decryption of the encrypted SQL files and is designed to be run manually when needed (which should only be in the event of a restore/migration).  This script is completely uneccessary but I find it helpful when emergencies occur to be as fast as possible (rather than looking up correct syntax)

standard.conf
```

## Global Variables ##
Company="nbc"
TempDir="/tmp"
LogDir="/var/log"
MyDomain="mydomain.com"
AdminEmail="linux@${MyDomain}"
ReportEmail="LHammonds <lhammonds@${MyDomain}>"
BackupDir="/bak"
Hostname="$(hostname -s)"
ScriptName="$0"
ScriptDir="/var/scripts"
MailFile="${TempDir}/mailfile.$$"

## Global Functions ##

function f_sendmail()
{
## Purpose: Send administrative email message.
## Parameter #1 = Subject
## Parameter #2 = Body
sendemail -f "${AdminEmail}" -t "${ReportEmail}" -u "${1}" -m "${2}\n\nServer: ${Hostname}\nProgram: ${ScriptName}\nLog: ${LogFile}" -s srv-mail:25 1>/dev/null 2>&1
}

```

mysql-user-encrypt.sh
```

#!/bin/bash
#############################################################
## Name : mysql-user-encrypt.sh
## Version : 1.0
## Date : 2018-04-16
## Author : LHammonds
## Purpose : Export REVOKE,DROP,GRANT statements for all users.
##         : Encrypt the files for storage
## Compatibility : Verified on Ubuntu Server 16.04 thru 16.04 LTS
##               : Verified on MariaDB 10.1.32
## Requirements : percona-toolkit (tested using version 2.2.16-1)
##              : gpgv (tested using version 1.4.20)
## Run Frequency : Often as desired.
## NOTE: Grant files contain the grant commands only.
##       Revoke files contain the revoke, drop and grant commands together.
## Parameters : None
## Exit Codes :
## 0  = Success
## 1  = ERROR: Lock file detected
## 2  = ERROR: Must be root user
## 4  = ERROR: percona-toolkit not installed
## 8  = ERROR: gpgv not installed
## 16 = ERROR: encryption failure
## 32 = ERROR: checksum mismatch
###################### CHANGE LOG ###########################
## DATE       VER WHO WHAT WAS CHANGED
## ---------- --- --- ---------------------------------------
## 2018-04-16 1.0 LTH Created script.
#############################################################

## Import standard variables and functions. ##
source /var/scripts/common/standard.conf

## Define local variables.
Title="${Company}-mysql-user-encrypt"
LogFile="${LogDir}/${Title}.log"
LockFile="${TempDir}/${Title}.lock"
GrantFile="user-grant.sql"
RevokeFile="user-revoke.sql"
CryptPass="MySuperSecretPasswordYouNeedToChange!"
CryptPassFile="${TempDir}/${Title}.gpg"
ErrorFlag=0
ReturnCode=0

#######################################
##            FUNCTIONS              ##
#######################################

function f_cleanup()
{
  if [ -f ${LockFile} ];then
    ## Remove lock file so other check space jobs can run.
    rm ${LockFile} 1>/dev/null 2>&1
  fi
  if [ ${ErrorFlag} != 0 ]; then
    f_sendmail "ERROR: Script Failure" "Please review the log file on ${Hostname}${LogFile}"
    echo "`date +%Y-%m-%d_%H:%M:%S` - Encrypt aborted." >> ${LogFile}
  fi
  if [ -f ${CryptPassFile} ]; then
    ## Remove temporary file
    rm ${CryptPassFile}
  fi
  exit ${ErrorFlag}
} ## f_cleanup

function f_encrypt()
{
  filename=$1
  encrypted=$2
  ## Create temporary password file
  touch ${CryptPassFile}
  chmod 0600 ${CryptPassFile}
  echo ${CryptPass} > ${CryptPassFile}
  if ! gpg --cipher-algo aes256 --output ${encrypted} --passphrase-file ${CryptPassFile} --batch --yes --no-use-agent --no-tty --symmetric ${filename}; then
    ## Encryption failed, log results, send email, terminate program.
    echo "ERROR: Encryption failed. ${filename}" | tee -a ${LogFile}
    ErrorFlag=16
    f_cleanup
  fi
  if [ -f ${CryptPassFile} ]; then
    ## Remove temporary file
    rm ${CryptPassFile}
  fi
} ## f_encrypt

function f_compare()
{
  filename=$1
  if ! sha512sum --status --check ${filename}; then
    ## Comparison failed, log results, send email, terminate program.
    echo "ERROR: Checksum mismatch: ${filename}" | tee -a ${LogFile}
    ErrorFlag=32
    f_cleanup
  fi
} ## f_compare

#######################################
##       PREREQUISITE CHECKS         ##
#######################################

if [ -f ${LockFile} ]; then
  # Lock file detected.  Abort script.
  echo "Backup partitions script aborted"
  echo "This script tried to run but detected the lock file: ${LockFile}"
  echo "Please check to make sure the file does not remain when backup partitions is not actually running."
  f_sendmail "ERROR: Encrypt script aborted" "This script tried to run but detected the lock file: ${LockFile}\n\nPlease check to make sure the file does not remain when script is not actually running.\n\nIf you find that the script is not running/hung, you can remove it by typing 'rm ${LockFile}'"
  ErrorFlag=1
  exit ${ErrorFlag}
else
  echo "`date +%Y-%m-%d_%H:%M:%S` ${ScriptName}" > ${LockFile}
fi

## Requirement Check: Script must run as root user.
if [ "$(id -u)" != "0" ]; then
  ## FATAL ERROR DETECTED: Document problem and terminate script.
  echo "ERROR: Root user required to run this script." | tee -a ${LogFile}
  ErrorFlag=2
  f_cleanup
fi

## Requirement Check: Software
command -v pt-show-grants > /dev/null 2>&1 && ReturnCode=0 || ReturnCode=1
if [ ${ReturnCode} = 1 ]; then
  ## Required program not installed.
  echo "ERROR: percona-toolkit not installed." | tee -a ${LogFile}
  ErrorFlag=4
  f_cleanup
fi
command -v gpg > /dev/null 2>&1 && ReturnCode=0 || ReturnCode=1
if [ ${ReturnCode} = 1 ]; then
  ## Required program not installed.
  ## NOTE: gpgv comes standard with Ubuntu Server 16.04 LTS
  echo "ERROR: gpgv not installed." | tee -a ${LogFile}
  ErrorFlag=8
  f_cleanup
fi

#######################################
##           MAIN PROGRAM            ##
#######################################

echo "`date +%Y-%m-%d_%H:%M:%S` - Export/Encrypt started." | tee -a ${LogFile}

## Export grant commands only
pt-show-grants --user root --separate --flush > ${BackupDir}/${GrantFile}
## Export revoke, drop and grant commands
pt-show-grants --user root --separate --flush --revoke --drop > ${BackupDir}/${RevokeFile}

## Encrypt files for transfer and storage
f_encrypt ${BackupDir}/${GrantFile} ${BackupDir}/${GrantFile}.enc
f_encrypt ${BackupDir}/${RevokeFile} ${BackupDir}/${RevokeFile}.enc

## Create checksum files
sha512sum ${BackupDir}/${GrantFile} > ${BackupDir}/${GrantFile}.sha512
sha512sum ${BackupDir}/${RevokeFile} > ${BackupDir}/${RevokeFile}.sha512
sha512sum ${BackupDir}/${GrantFile}.enc > ${BackupDir}/${GrantFile}.enc.sha512
sha512sum ${BackupDir}/${RevokeFile}.enc > ${BackupDir}/${RevokeFile}.enc.sha512

## Verify checksum results
f_compare ${BackupDir}/${GrantFile}.sha512
f_compare ${BackupDir}/${RevokeFile}.sha512
f_compare ${BackupDir}/${GrantFile}.enc.sha512
f_compare ${BackupDir}/${RevokeFile}.enc.sha512

## Remove unencrypted files
rm ${BackupDir}/${GrantFile}
rm ${BackupDir}/${RevokeFile}

## Set file permissions.
chmod 0600 ${BackupDir}/${GrantFile}*
chmod 0600 ${BackupDir}/${RevokeFile}*

echo "`date +%Y-%m-%d_%H:%M:%S` - Export/Encrypt finished." | tee -a ${LogFile}
f_cleanup

```

mysql-user-decrypt.sh
```

#!/bin/bash
#############################################################
## Name : mysql-user-decrypt.sh
## Version : 1.0
## Date : 2018-04-16
## Author : LHammonds
## Purpose : Decrypt the SQL files that were encrypted during backup.
## Compatibility : Verified on Ubuntu Server 16.04 thru 16.04 LTS
##               : Verified on MariaDB 10.1.32
## Requirements : percona-toolkit (tested using version 2.2.16-1)
##              : gpgv (tested using version 1.4.20)
## Run Frequency : Manually.  When backups need to be decrypted.
## NOTE: Grant files contain the grant commands only.
##       Revoke files contain the revoke, drop and grant commands together.
## Parameters : None
## Exit Codes :
## 0  = Success
## 1  = ERROR: Lock file detected
## 2  = ERROR: Must be root user
## 4  = ERROR: percona-toolkit not installed
## 8  = ERROR: gpgv not installed
## 16 = ERROR: checksum mismatch
## 32 = ERROR: decryption failure
###################### CHANGE LOG ###########################
## DATE       VER WHO WHAT WAS CHANGED
## ---------- --- --- ---------------------------------------
## 2018-04-16 1.0 LTH Created script.
#############################################################

## Import standard variables and functions. ##
source /var/scripts/common/standard.conf

## Define local variables.
Title="${Company}-mysql-user-decrypt"
LogFile="${LogDir}/${Title}.log"
LockFile="${TempDir}/${Title}.lock"
GrantFile="user-grant.sql"
RevokeFile="user-revoke.sql"
CryptPass="MySuperSecretPasswordYouNeedToChange!"
CryptPassFile="${TempDir}/${Title}.gpg"
ErrorFlag=0
ReturnCode=0

#######################################
##            FUNCTIONS              ##
#######################################

function f_cleanup()
{
  if [ -f ${LockFile} ];then
    ## Remove lock file so other check space jobs can run.
    rm ${LockFile} 1>/dev/null 2>&1
  fi
  if [ ${ErrorFlag} != 0 ]; then
    echo "`date +%Y-%m-%d_%H:%M:%S` - Decrypt aborted." | tee -a ${LogFile}
  fi
  if [ -f ${CryptPassFile} ]; then
    ## Remove temporary file
    rm ${CryptPassFile}
  fi
  exit ${ErrorFlag}
} ## f_cleanup

function f_compare()
{
  filename=$1
  if ! sha512sum --status --check ${filename}; then
    ## Comparison failed, log results, terminate program.
    echo "ERROR: Checksum mismatch: ${filename}" | tee -a ${LogFile}
    ErrorFlag=16
    f_cleanup
  fi
} ## f_compare

function f_decrypt()
{
  EncryptedFile=$1
  DecryptedFile=$2
  ## Create temporary password file
  touch ${CryptPassFile}
  chmod 0600 ${CryptPassFile}
  echo ${CryptPass} > ${CryptPassFile}
  if ! gpg --cipher-algo aes256 --output ${DecryptedFile} --passphrase-file ${CryptPassFile} --quiet --batch --yes --no-use-agent --no-tty --decrypt ${EncryptedFile}; then
    ## Decryption failed, log results, send email, terminate program.
    echo "ERROR: Decryption failed: ${EncryptedFile}" | tee -a ${LogFile}
    ErrorFlag=32
    f_cleanup
  fi
  if [ -f ${CryptPassFile} ]; then
    ## Remove temporary file
    rm ${CryptPassFile}
  fi
} ## f_decrypt

#######################################
##       PREREQUISITE CHECKS         ##
#######################################

if [ -f ${LockFile} ]; then
  # Lock file detected.  Abort script.
  echo "Script aborted"
  echo "This script tried to run but detected the lock file: ${LockFile}"
  echo "Please check to make sure the file does not remain when not actually running."
  ErrorFlag=1
  exit ${ErrorFlag}
else
  echo "`date +%Y-%m-%d_%H:%M:%S` ${ScriptName}" > ${LockFile}
fi

## Requirement Check: Script must run as root user.
if [ "$(id -u)" != "0" ]; then
  ## FATAL ERROR DETECTED: Document problem and terminate script.
  echo "ERROR: Root user required to run this script." | tee -a ${LogFile}
  ErrorFlag=2
  f_cleanup
fi

## Requirement Check: Software
command -v pt-show-grants > /dev/null 2>&1 && ReturnCode=0 || ReturnCode=1
if [ ${ReturnCode} = 1 ]; then
  ## Required program not installed.
  echo "ERROR: percona-toolkit not installed." | tee -a ${LogFile}
  ErrorFlag=4
  f_cleanup
fi
command -v gpg > /dev/null 2>&1 && ReturnCode=0 || ReturnCode=1
if [ ${ReturnCode} = 1 ]; then
  ## Required program not installed.
  ## NOTE: gpgv comes standard with Ubuntu Server 16.04 LTS
  echo "ERROR: gpgv not installed." | tee -a ${LogFile}
  ErrorFlag=8
  f_cleanup
fi

#######################################
##           MAIN PROGRAM            ##
#######################################

echo "`date +%Y-%m-%d_%H:%M:%S` - Decrypt started." | tee -a ${LogFile}

## Verify checksum results on encrypted files
echo "Verifying checksums on encrypted files..."
f_compare ${BackupDir}/${GrantFile}.enc.sha512
f_compare ${BackupDir}/${RevokeFile}.enc.sha512
echo "Encrypted checksums: OK."

## Decrypt files
echo "Decrypting files..."
f_decrypt ${BackupDir}/${GrantFile}.enc ${BackupDir}/${GrantFile}
f_decrypt ${BackupDir}/${RevokeFile}.enc ${BackupDir}/${RevokeFile}

## Verify checksum results on decrypted files
echo "Verifying checksums on decrypted files..."
f_compare ${BackupDir}/${GrantFile}.sha512
f_compare ${BackupDir}/${RevokeFile}.sha512
echo "Decrypted checksums: OK."

## Set file permissions.
chmod 0600 ${BackupDir}/${GrantFile}
chmod 0600 ${BackupDir}/${RevokeFile}

echo "`date +%Y-%m-%d_%H:%M:%S` - Decrypt finished." | tee -a ${LogFile}
f_cleanup

```

I then add the encrypt script to my root's crontab schedule to be run daily along with the mysqldump backup.

crontab -u root
```

########################################
# Name: Crontab Schedule for root user
# Author: LHammonds
############# Update Log ###############
# 2012-05-20 - LTH - Created schedule
########################################

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# Crontab SYNTAX:
# minute(0-59) hour(0-23) day-of-month(1-31) month(1-12) day-of-week(0-6) command-to-execute

#
# Backup MySQL user privileges
#
0 22 * * * /var/scripts/prod/mysql-user-encrypt.sh > /dev/null 2>&1
#
# Backup MySQL databases
#
0 23 * * * /var/scripts/prod/mysql-backup.sh > /dev/null 2>&1

```

**EDIT:** The "mysql-backup.sh" script can be found on my [How-To Install MariaDB](https://ubuntuforums.org/showthread.php?t=2373219) thread.

LHammonds

---

### Post by m-dw on 2018-04-18
Thanks to both of you for your advice. I won't have the opportunity to actually do this for a couple of weeks due to work/family commitments, but I'm documenting the process so actually doing it is straight forward and as stress free as possible.

---

### Post by LHammonds on 2018-04-18
> **m-dw said:**
> I'm documenting the process so actually doing it is straight forward and as stress free as possible.The exact reason why I document....well...that and I'm old with a forgetful mind. hehehe.

---

