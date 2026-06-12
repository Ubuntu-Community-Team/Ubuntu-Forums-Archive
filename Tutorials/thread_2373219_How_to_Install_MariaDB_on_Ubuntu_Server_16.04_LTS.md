---
title: "How to Install MariaDB on Ubuntu Server 16.04 LTS"
date: 2017-10-04
forum: Tutorials
---

### Post by LHammonds on 2017-10-04
Greetings and salutations,

I hope this thread will be helpful to those who follow in my foot steps as well as getting any advice based on what I have done / documented.

Link to original post: [HammondsLegacy Forums]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=225") (best when viewed at original location due to custom formatting)

[SIZE=5]High-level overview[/SIZE]
 
This thread will cover installation of a dedicated Ubuntu server and MariaDB database. MariaDB is a drop-in replacement for MySQL which is enjoying feature/security/performance updates by the original MySQL team while MySQL languishes under the thumb of Oracle.  The server will be installed inside a virtual machine in vSphere running on ESXi servers. Notes will also be supplied for doing the same thing for VirtualBox on a Windows 7 PC. Migration of data from an older MySQL server to the new one will be covered. Although there are some VMware-specific and VirtualBox-specific steps, they are very few and the majority of this documentation will work for other Virtual Machines or even directly installed onto a physical machine (e.g. bare-metal install). If you have any advice on doing things better, please let me know by replying to >>this thread on the Ubuntu forums<< (need to create).
 
This thread will also cover some custom scripts to help automate tasks such as backing up, automatically growing the file system when free space is low, etc.
 
[SIZE=5]Tools utilized in this process[/SIZE]


[LIST]
[*][Ubuntu Server]("http://www.ubuntu.com/download/ubuntu/download") 16.04.3 LTS, 64-bit 
[*][MariaDB]("http://www.mariadb.org/") 10.1.28 
[*][Portable PuTTY]("http://portableapps.com/apps/internet/putty_portable") 0.62 
[*][VMware vSphere]("http://www.vmware.com/products/vsphere/overview.html") 6.0.0 
[*][VirtualBox]("http://www.virtualbox.org/") 5.1.18 
[/LIST]

[SIZE=5]Helpful links[/SIZE]

The list below are sources of information that was helpful in the creation of this document.


[LIST]
[*][Ubuntu Documentation]("https://help.ubuntu.com") 
[*][Ubuntu Firewall Basics]("https://help.ubuntu.com/community/IptablesHowTo#Disabling%20the%20firewall") 
[*][Ubuntu AppArmor Basics]("https://help.ubuntu.com/community/AppArmor#Disable%20AppArmor%20framework") 
[/LIST]

[SIZE=5]Assumptions[/SIZE]
 
This documentation will need to make use of some very-specific information that will most-likely be different for each person / location. And as such, this information will be noted in this section. They will be highlighted in red throughout the document as a reminder that you should plug-in your own value rather than actually using these "place-holder" values.

Under no circumstance should you use the actual values listed below. They are place-holders for the real thing. This is just a checklist template you need to have answered before you start the install process.

Wherever you see [COLOR=red]RED[/COLOR] in this document, you need to substitute it for you will use in your environment.


[LIST]
[*]Ubuntu Server name: [COLOR=red]srv-mysql[/COLOR] 
[*]Internet domain: [COLOR=red]mydomain.com[/COLOR] 
[*]Ubuntu Server IP address: [COLOR=red]192.168.107.27[/COLOR] 
[*]Ubuntu Server IP subnet mask: [COLOR=red]255.255.255.0[/COLOR] 
[*]Ubuntu Server IP gateway: [COLOR=red]192.168.107.1[/COLOR] 
[*]Internal DNS Server 1: [COLOR=red]192.168.107.212[/COLOR] 
[*]Internal DNS Server 2: [COLOR=red]192.168.107.213[/COLOR] 
[*]External DNS Server 1: [COLOR=red]8.8.8.4[/COLOR] 
[*]External DNS Server 2: [COLOR=red]8.8.8.5[/COLOR] 
[*]Ubuntu Admin ID: [COLOR=red]administrator[/COLOR] 
[*]Ubuntu Admin Password: [COLOR=red]myadminpass[/COLOR] 
[*]Email Server (remote): [COLOR=red]192.168.107.25[/COLOR] 
[*]MySQL root Password: [COLOR=red]mysqlrootpass[/COLOR] 
[*]Windows Share ID: [COLOR=red]mysqlshare[/COLOR] 
[*]Windows Share Password: [COLOR=red]mysqlsharepass[/COLOR] 
[/LIST]

It is also assumed the reader knows how to use the VI editor. If not, you will need to [beef up your skill set]("http://www.washington.edu/computing/unix/vi.html") or use a different editor in place of it.

---

### Post by LHammonds on 2017-10-04
[SIZE=5]Install Ubuntu Server[/SIZE]

The Ubuntu Server Long-Term Support (LTS) is free but we have the option of buy support and that is the main reason this server was selected.

The steps for setting up the base server are covered in this article: [How to install and configure Ubuntu Server]("https://ubuntuforums.org/showthread.php?t=2373161")

It is assumed that the server was configured according to that article with the exceptions that the assumptions in red (variables above) are used instead of the assumptions in that document since we are building a database server.

---

### Post by LHammonds on 2017-10-04
[size=5]Add MariaDB Repositories[/size]

Source of information: [MariaDB](https://downloads.mariadb.org/mariadb/repositories/) (NOTE: Your flavor of Linux and download location may vary and that page will help)


[list=1]
[*]Start the Ubuntu server and connect using PuTTY.
[*]At the login prompt, login with your administrator account ([color=red]**administrator**[/color] / [color=red]**myadminpass**[/color]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]Type the following:
```

apt install software-properties-common
apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xF1656F24C74CD1D8
add-apt-repository 'deb [arch=amd64,i386,ppc64el] http://nyc2.mirrors.digitalocean.com/mariadb/repo/10.1/ubuntu xenial main'
apt update

```
[/list]


[size=5]Install MariaDB[/size]


[list=1]
[*]Start the Ubuntu server and connect using PuTTY.
[*]At the login prompt, login with your administrator account ([color=red]**administrator**[/color] / [color=red]**myadminpass**[/color]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]Install MariaDB by typing:
```
apt -y install mariadb-server
```
[*]Type your password for the MySQL "root" user account [color=red]**mysqlrootpass**[/color] [color=green]{ENTER}[/color]
[*]Re-type the password again [color=red]**mysqlrootpass**[/color] [color=green]{ENTER}[/color]
[*]When installation is completed, the MySQL service should automatically start
[*]Verify the service is running by typing either of the following two commands:
```
service mysql status
```
or
```
netstat -tap | grep mysql
```
[/list]

---

### Post by LHammonds on 2017-10-04
[size=5]Configure MariaDB[/size]


[list=1]
[*]Make a personal MySQL config file for the root user so the password is not required when running MySQL commands
```
touch ~/.my.cnf
chmod 0600 ~/.my.cnf
vi ~/.my.cnf
```
[*]Add the following lines to ~/.my.cnf
```
[client]
password=mysqlrootpass
```
[*]Edit the global mysql config file by typing **vi /etc/mysql/my.cnf**
[*]Comment-out the bind-address by adding a pound sign (#) at the beginning of the line:
```
#bind-address = 127.0.0.1
```
[*]Restart the mysql service by typing ```
service mysql restart
```
[*]See if the following command will work without prompting for a password: ```
mysqladmin status
```
[*]If this did not work, it is possible you did not uninstall apparmor in an earlier step
[/list]

 
[size=5]Tighten Security[/size]

MySQL comes with a script to tighten-down security for a production server.


[list=1]
[*]Connect to the server using PuTTY and at the login prompt, login with your administrator account ([color=red]**administrator**[/color] / [color=red]**myadminpass**[/color]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]Type **mysql_secure_installation**
[*]Type the MySQL "root" password: [color=red]**mysqlrootpass**[/color]
[*]Type **N** to skip changing the password
[*]Type **Y** to remove the anonymous user account
[*]Type **Y** to disallow remote root login
[*]Type **Y** to remove the test database
[*]Type **Y** to reload privilege tables
[/list]

---

### Post by LHammonds on 2017-10-04
[size=5]Relocate the Databases[/size]

If you do not want to leave your databases in the default location (/var/lib/mysql), then you can follow these steps to move them somewhere else. In this example, we will move them to /opt/mysql


[list=1]
[*]At the login prompt, login with your administrator account ([color=red]administrator[/color] / [color=red]myadminpass[/color]) and then temporarily grant yourself super user privilages by typing **sudo su**
[*]At the console, type the following:
```
mkdir -p /opt/mysql
chown mysql:mysql /opt/mysql
vi /etc/mysql/my.cnf
```
[*]Change the location where the databases by changing datadir from /var/lib/mysql to:
```
datadir = /opt/mysql
```
[*]Type the following commands to move the database(s)
```
service mysql stop
mv /var/lib/mysql/* /opt/mysql/.
service mysql start
```
[*]Verify the service is running by typing either of the following two commands:
```
service mysql status
```
or
```
netstat -tap | grep mysql
```
[/list]


NOTE: If you did not remove apparmor, it will prevent MySQL from starting at this point until you update apparmor or remove it.

---

### Post by LHammonds on 2017-10-04
[size=5]Reset lost root password[/size]

If you ever find yourself in the position of not being able to login (locally) to your database with your root password, you will need to reset the password. For example, phpmyadmin fails to change the password correctly and neither the old nor the new password works.

This procedure will require taking the database offline for a short time...so schedule the downtime appropriately.

In this example, we are going to set the password to [color=red]**mysqlrootpass**[/color] (but please **DO NOT** actually use this exact password for your server...doing so will earn you derp points).


[list=1]
[*]Connect to the server using PuTTY.
[*]Login with your administrator account. At the $ prompt, temporarily grant yourself super user privileges by typing **sudo su**
[*]Shutdown the database service:
```
service mysql stop
```
[*]Start MySQL in safe mode so that it does not try to authenticate users:
```
mysqld_safe --skip-grant-tables &
```
[*]Connect to the MySQL server via the command-line utility (which should not ask for a password):
```
mysql -u root
```
[*]Select the primary database and reset the password:
```
use mysql;
update user set password=PASSWORD("mysqlrootpass") where User='root';
flush privileges;
quit
```
[*]Stop the MySQL service and restart it in the normal mode:
```
service mysql stop
service mysql start
```
[*]Test out the new password by connecting with the command-line utility:
```
mysql -u root -p
quit
```
[*]Update your **~/my.cnf** file with the current password.
[/list]

---

### Post by LHammonds on 2017-10-04
[size=5]Usage Examples[/size]


[list=1]
[*]Connect to the server using PuTTY.
[*]At the login prompt, login with your administrator account ([color=red]**administrator**[/color] / [color=red]**myadminpass**[/color]) and then temporarily grant yourself super user privileges by typing **sudo su**
[*]Start a mysql session and create a database called minecraft and a user called minecraftuser with a password of "mysqlpass" and grant the user access to the database:
```
mysql -u root -p
CREATE DATABASE minecraft CHARACTER SET utf8 COLLATE utf8_bin;;
GRANT ALL PRIVILEGES ON minecraft.* TO 'minecraftuser'@'%' IDENTIFIED BY 'mysqlpass';
FLUSH PRIVILEGES;
QUIT
```
[*]To remove the changes you just made, you can run the following commands to delete the user and database:
```
DROP USER minecraftuser;
DROP DATABASE minecraft;
```
[*]NOTE #1: The [color=red]**'minecraftuser'@'%'**[/color] above means that user can login from anywhere so the application can connect no matter what server it is on. If you want tighter security, you can specify the IP address of the web server as part of the login permissions. For example, the following would tell the DB server to only allow the database user access from the web server only:
```
GRANT ALL PRIVILEGES ON minecraft.* TO 'minecraftuser'@'192.168.107.26' IDENTIFIED BY 'mysqlpass';
```
[*]NOTE #2: Another modification to the grant command can limit the user to just the local machine which is perfect if your web application and database are on the same machine:
```
GRANT ALL PRIVILEGES ON minecraft.* TO 'minecraftuser'@'localhost' IDENTIFIED BY 'mysqlpass';
```
[/list]

---

### Post by LHammonds on 2017-10-04
[size=5]Scripting[/size]

Much of the solutions beyond this point involve scripts (programming snippets / automated commands).

In particular, they are Bash Scripts. I chose this due to its popularity and the fact it comes with Ubuntu. I try to make use of what comes with the system without requiring additional software / services unless they really add to the bottom line such as decreasing the time it takes for a process to run or to conserve storage and bandwidth usage.

---

### Post by LHammonds on 2017-10-04
[SIZE=5]MySQL Backup Script[/SIZE]

This script is designed to perform a full backup of all databases while the server is online. It actually does three kinds of backups. First, it pulls all the databases into a single file which is good for restoring everything on new servers. It then pulls by database to create database files and then it pulls each individual table into its own file which is easier to isolate individual items to restore if necessary.

My needs are not that great at the moment so I backup one time per day...which is handled by a crontab schedule covered later in this thread.

/var/scripts/prod/mysql-backup.sh
```
#!/bin/bash
#############################################
## Name          : mysql-backup.sh
## Version       : 1.4
## Date          : 2017-09-01
## Author        : LHammonds
## Purpose       : Complete backup of MySQL database.
## Compatibility : Verified on to work on:
##                  - Ubuntu Server 10.04 LTS - 16.04 LTS
##                  - MySQL 5.1.41 - 5.5.22
##                  - MariaDB 10.1.22
## Requirements  : p7zip-full (if ArchiveMethod=tar.7z), sendemail
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
## 2017-04-13 LTH Corrected variable casing.
## 2017-04-24 LTH All databases minus an exception list.
## 2017-09-01 LTH Handle folder creation upon 1st time run.
#############################################

## Import common variables and functions. ##
source /var/scripts/common/standard.conf

LogFile="${LogDir}/mysql-backup.log"
LockFile="${TempDir}/mysql-backup.lock"
TargetDir="${BackupDir}/mysql"
MySQLDir="/opt/mysql"
DatabasesToExclude="JunkDB1 JunkDB2"
ExclusionList="'information_schema','mysql'"
OffsiteBackDir="${OffsiteDir}/${Hostname}/mysql"
ArchiveFile="`date +%Y-%m-%d-%H-%M`_mysql-backup.${ArchiveMethod}"
ErrorFlag=0

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
  if [ ${OffsiteBackDir} = "" ]; then
    ## Make darn sure the path is not empty since we do NOT
    ## want to start purging files from a random location.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- Purge error: OffsiteBackDir site variable is empty!" >> ${LogFile}
    return 9
  fi
  ## Get the name of the oldest file.
  OldestFile=`ls -1t ${OffsiteBackDir} | tail -1`
  if [ "${OldestFile}" = "" ]; then
    ## Error. Filename variable empty.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- Purge error: OldestFile variable is empty." >> ${LogFile}
    return 9
  else   
    DataFileSIZE=`ls -lak "${OffsiteBackDir}/${OldestFile}" | awk '{ print $5 }' | sed -e :a -e 's/\(.*[0-9]\)\([0-9]\{3\}\)/\1,\2/;ta'`
    echo "`date +%Y-%m-%d_%H:%M:%S` --- Purging old file: ${OffsiteBackDir}/${OldestFile}, Size = ${DataFileSIZE} kb" >> ${LogFile}
    rm "${OffsiteBackDir}/${OldestFile}"
    if [ -f "${OffsiteBackDir}/${OldestFile}" ]; then
      ## File still exists.  Return error.
      return 1
    else
      return 0
    fi
  fi
}

function f_cleanup()
{
  echo "`date +%Y-%m-%d_%H:%M:%S` - MySQL backup exit code: ${ErrorFlag}" >> ${LogFile}

  if [ -f ${LockFile} ];then
    ## Remove lock file so other backup jobs can run.
    rm ${LockFile} 1>/dev/null 2>&1
  fi
  ## Email the result to the administrator.
  if [ ${ErrorFlag} -eq 0 ]; then
    f_sendmail "[Success] MySQL Backup" "MySQL backup completed with no errors."
  else
    f_sendmail "[Failure] MySQL Backup" "MySQL backup failed.  ErrorFlag = ${ErrorFlag}"
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

if [ -f ${LockFile} ]; then
  ## Program lock file detected.  Abort script.
  f_sendmail "MySQL Backup aborted - Lock File" "This script tried to run but detected the lock file: ${LockFile}\n\nPlease check to make sure the file does not remain when this script is not actually running."
  exit 1
else
  ## Create the lock file to ensure only one script is running at a time.
  echo "`date +%Y-%m-%d_%H:%M:%S` ${ScriptName}" > ${LockFile}
fi

echo "`date +%Y-%m-%d_%H:%M:%S` - MySQL Backup started." >> ${LogFile}

## If the 7-Zip archive method is specified, make sure the package is installed.
if [ "${ArchiveMethod}" = "tar.7z" ]; then
  if [ ! -f "/usr/bin/7za" ]; then
    ## Required package (7-Zip) not installed.
    echo "`date +%Y-%m-%d_%H:%M:%S` - CRITICAL ERROR: 7-Zip package not installed.  Please install by typing 'aptitude -y install p7zip-full'" >> ${LogFile}
    ErrorFlag=1
    f_emergencyexit ${ErrorFlag}
  fi
fi

echo "`date +%Y-%m-%d_%H:%M:%S` --- Partition status:" >> ${LogFile}
df -h >> ${LogFile}

## Document the current uptime.
${MYSQL} -e status | grep -i uptime >> ${LogFile}

StartTime="$(date +%s)"

echo "`date +%Y-%m-%d_%H:%M:%S` --- Space consumed in ${MySQLDir} = `du -sh ${MySQLDir} | awk '{ print $1 }'`" >> ${LogFile}


for DB in `echo "${DatabasesToExclude}"`
do
  ExclusionList="${ExclusionList},'${DB}'"
done
SQLSTMT="SELECT schema_name FROM information_schema.schemata"
SQLSTMT="${SQLSTMT} WHERE schema_name NOT IN (${ExclusionList})"
MYSQLDUMP_DATABASES=""
for DB in `mysql -ANe"${SQLSTMT}"`
do
  MYSQLDUMP_DATABASES="${MYSQLDUMP_DATABASES} ${DB}"
done
MYSQLDUMP_OPTIONS="--skip-lock-tables"

## Backup all databases.
${MYSQLDUMP} ${MYSQLDUMP_OPTIONS} --databases ${MYSQLDUMP_DATABASES} > ${TargetDir}/mysql-all.sql

## Loop through every database.
#DBList=$(echo "show databases;"|mysql --skip-column-names)
#for SingleDB in ${DBList}

for SingleDB in ${MYSQLDUMP_DATABASES}
do
  if [ "${SingleDB}" != "information_schema" ] && [ "${SingleDB}" != "performance_schema" ]; then
    ## Backup individual database.
    ${MYSQLDUMP} ${SingleDB} > ${TargetDir}/${SingleDB}.sql
    ## Create database sub-folder.
    mkdir -p ${TargetDir}/${SingleDB}
    ## Export each table in the database individually.
    for SingleTable in `echo "show tables" | $MYSQL ${SingleDB}|grep -v Tables_in_`;
    do
      DataFile=${TargetDir}/${SingleDB}/${SingleTable}.sql
      case "${SingleTable}" in
        general_log)
          ${MYSQLDUMP} ${SingleDB} ${SingleTable} --skip-lock-tables > ${DataFile}
          ;;
        slow_log)
          ${MYSQLDUMP} ${SingleDB} ${SingleTable} --skip-lock-tables > ${DataFile}
          ;;
        *)
          ${MYSQLDUMP} ${SingleDB} ${SingleTable} > ${DataFile}
          ;;
      esac
    done
  fi
done

## Compress the backup into a single file based on archive method specified.
echo "`date +%Y-%m-%d_%H:%M:%S` --- Compressing archive: ${TempDir}/${ArchiveFile}" >> ${LogFile}
case "${ArchiveMethod}" in
tar.7z)
  ${TAR} -cpf - ${TargetDir} | ${MY7ZIP} a -si -mx=7 -w${TempDir} ${TempDir}/${ArchiveFile} 1>/dev/null 2>&1
  ReturnValue=$?
  ## Restore using one of the following commands (do not uncomment, only for notation):
  ## 7za x -so -w/tmp ${TempDir}/${ArchiveFile} | tar -C / -xf -
  ## 7za x -so -w/tmp ${TempDir}/${ArchiveFile} | tar -C ${TempDir}/restore --strip-components=1 -xf -
  ;;
tgz)
  ${TAR} -cpzf ${TempDir}/${ArchiveFile} ${TargetDir} 1>/dev/null 2>&1
  ReturnValue=$?
  ## Restore using one of the following commands (do not uncomment, only for notation):
  ## tar -C / -xzf ${TempDir}/${ArchiveFile}
  ## tar -C ${TempDir}/restore --strip-components=1 -xzf ${TempDir}/${ArchiveFile}
  ;;
*)
  ${TAR} -cpzf ${TempDir}/${ArchiveFile} ${TargetDir} 1>/dev/null 2>&1
  ReturnValue=$?
  ;;
esac

if [ ${ReturnValue} -ne 0 ]; then
  ## tar command failed.  Send warning email.
  f_sendmail "MySQL Backup Failure - tar" "tar failed with return value of ${ReturnValue}"
  ErrorFlag=$((${ErrorFlag} + 2))
fi

## Mount the remote folder. ##
f_mount

if [ -f ${OffsiteTestFile} ]; then
  ## Offline file detected.  Assuming failed mount.
  ErrorFlag=$((${ErrorFlag} + 16))
  echo "`date +%Y-%m-%d_%H:%M:%S` --- ERROR: Offline file detected: ${OffsiteTestFile}" >> ${LogFile}
  f_emergencyexit ${ErrorFlag}
fi

## If destination folder does not exist, create it. Mainly for 1st time use.
if [ ! -d ${OffsiteBackDir} ]; then
  mkdir -p ${OffsiteBackDir}
fi

FreeSpace=`df -k ${OffsiteDir} | grep ${OffsiteDir} | awk '{ print $3 }'`
BackupSize=`ls -lak "${TempDir}/${ArchiveFile}" | awk '{ print $5 }'`

## Make sure space is available on the remote server to copy the file.
if [ ${FreeSpace} -lt ${BackupSize} ]; then
  ## Not enough free space available.  Purge existing backups until there is room.
  EnoughSpace=0
  while [ ${EnoughSpace} -eq 0 ]
  do
    f_PurgeOldestArchive
    ReturnValue=$?
    case ${ReturnValue} in
    1)
      ## Cannot purge archives to free up space.  End program gracefully.
      echo "`date +%Y-%m-%d_%H:%M:%S` - ERROR: Not enough free space on ${OffsiteBackDir} and cannot purge old archives.  Script aborted." >> ${LogFile}
      ## Stop and exit the script with an error code.
      ErrorFlag=$((${ErrorFlag} + 4))
      f_emergencyexit ${ErrorFlag}
      ;;
    9)
      ## Configuration error, end program gracefully.
      echo "`date +%Y-%m-%d_%H:%M:%S` - ERROR: Configuration problem. Script aborted." >> ${LogFile}
      ## Stop and exit the script with an error code.
      ErrorFlag=$((${ErrorFlag} + 8))
      f_emergencyexit ${ErrorFlag}
      ;;
    esac
    FreeSpace=`df -k ${OffsiteDir} | grep ${OffsiteDir} | awk '{ print $3 }'`
    if [ ${FreeSpace} -gt ${BackupSize} ]; then
      ## Enough space is now available.
      EnoughSpace=1
    else
      ## Not enough space is available yet.
      EnoughSpace=0
    fi
  done
fi

## Copy the backup to an offsite storage location.
echo "`date +%Y-%m-%d_%H:%M:%S` --- Copying archive file to offsite location." >> ${LogFile}
cp ${TempDir}/${ArchiveFile} ${OffsiteBackDir}/${ArchiveFile} 1>/dev/null 2>&1
if [ ! -f ${OffsiteBackDir}/${ArchiveFile} ]; then
  ## NON-FATAL ERROR: Copy command did not work.  Send email notification.
  echo "`date +%Y-%m-%d_%H:%M:%S` --- WARNING: Remote copy failed. ${OffsiteBackDir}/${ArchiveFile} does not exist!" >> ${LogFile}
  f_sendmail "MySQL Backup Failure - Remote Copy" "Remote copy failed. ${OffsiteBackDir}/${ArchiveFile} does not exist\n\nBackup file still remains in this location: ${Hostname}:${TempDir}/${ArchiveFile}"
else
  ## Remove local copy of the compressed backup file
  rm ${TempDir}/${ArchiveFile}
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

echo "`date +%Y-%m-%d_%H:%M:%S` --- Total backup time: ${Hours} hour(s) ${Minutes} minute(s) ${Seconds} second(s)" >> ${LogFile}

echo "`date +%Y-%m-%d_%H:%M:%S` - MySQL backup completed." >> ${LogFile}

## Perform cleanup routine.
f_cleanup
## Exit with the combined return code value.
exit ${ErrorFlag}
```Here is a sample of the log output:
 
/var/log/mysql-backup.log
```
2012-05-16_23:00:01 - MySQL backup started.
2012-05-16_23:00:01 --- Partition status:
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root  3.8G  1.1G  2.6G  29% /
udev                  237M  4.0K  237M   1% /dev
tmpfs                  99M  540K   98M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  246M     0  246M   0% /run/shm
/dev/sda1             179M   25M  145M  15% /boot
/dev/mapper/LVG-bak   4.0G   65M  3.8G   2% /backup
/dev/mapper/LVG-var   2.0G  347M  1.6G  18% /var
/dev/mapper/LVG-tmp   2.0G   31M  1.9G   2% /tmp
Uptime:            13 days 8 hours 50 min 14 sec
2012-05-16_23:00:01 --- Space consumed in  = 104K
2012-05-16_23:00:07 --- Compressing archive: /tmp/2012-05-16-23-00_mysql-backup.tar.7z
2012-05-16_23:00:18 --- Copying archive file to offsite location.
2012-05-16_23:00:19 --- Total backup time: 0 hour(s) 0 minute(s) 18 second(s)
2012-05-16_23:00:19 - MySQL backup completed.
2012-05-16_23:00:19 - MySQL backup exit code: 0
2012-05-17_23:00:02 - MySQL backup started.
2012-05-17_23:00:02 --- Partition status:
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root  3.8G  1.1G  2.6G  29% /
udev                  237M  4.0K  237M   1% /dev
tmpfs                  99M  540K   98M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  246M     0  246M   0% /run/shm
/dev/sda1             179M   25M  145M  15% /boot
/dev/mapper/LVG-bak   4.0G   65M  3.8G   2% /backup
/dev/mapper/LVG-var   2.0G  347M  1.6G  18% /var
/dev/mapper/LVG-tmp   2.0G   31M  1.9G   2% /tmp
Uptime:            8 hours 38 min 26 sec
2012-05-17_23:00:02 --- Space consumed in  = 104K
2012-05-17_23:00:07 --- Compressing archive: /tmp/2012-05-17-23-00_mysql-backup.tar.7z
2012-05-17_23:00:19 --- Copying archive file to offsite location.
2012-05-17_23:00:25 --- Total backup time: 0 hour(s) 0 minute(s) 23 second(s)
2012-05-17_23:00:25 - MySQL backup completed.
2012-05-17_23:00:25 - MySQL backup exit code: 0
2012-05-18_23:00:01 - MySQL backup started.
2012-05-18_23:00:01 --- Partition status:
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root  3.8G  1.1G  2.6G  29% /
udev                  237M  4.0K  237M   1% /dev
tmpfs                  99M  540K   98M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  246M     0  246M   0% /run/shm
/dev/sda1             179M   25M  145M  15% /boot
/dev/mapper/LVG-bak   4.0G   65M  3.8G   2% /backup
/dev/mapper/LVG-var   2.0G  347M  1.6G  18% /var
/dev/mapper/LVG-tmp   2.0G   31M  1.9G   2% /tmp
Uptime:            1 day 8 hours 38 min 25 sec
2012-05-18_23:00:01 --- Space consumed in  = 108K
2012-05-18_23:00:05 --- Compressing archive: /tmp/2012-05-18-23-00_mysql-backup.tar.7z
2012-05-18_23:00:16 --- Copying archive file to offsite location.
2012-05-18_23:00:17 --- Total backup time: 0 hour(s) 0 minute(s) 16 second(s)
2012-05-18_23:00:17 - MySQL backup completed.
2012-05-18_23:00:17 - MySQL backup exit code: 0
2012-05-19_23:00:01 - MySQL backup started.
2012-05-19_23:00:01 --- Partition status:
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root  3.8G  1.1G  2.6G  29% /
udev                  237M  4.0K  237M   1% /dev
tmpfs                  99M  540K   98M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  246M     0  246M   0% /run/shm
/dev/sda1             179M   25M  145M  15% /boot
/dev/mapper/LVG-bak   4.0G   65M  3.8G   2% /backup
/dev/mapper/LVG-var   2.0G  347M  1.6G  18% /var
/dev/mapper/LVG-tmp   2.0G   31M  1.9G   2% /tmp
Uptime:            2 days 8 hours 38 min 25 sec
2012-05-19_23:00:01 --- Space consumed in  = 108K
2012-05-19_23:00:04 --- Compressing archive: /tmp/2012-05-19-23-00_mysql-backup.tar.7z
2012-05-19_23:00:16 --- Copying archive file to offsite location.
2012-05-19_23:00:17 --- Total backup time: 0 hour(s) 0 minute(s) 16 second(s)
2012-05-19_23:00:17 - MySQL backup completed.
2012-05-19_23:00:17 - MySQL backup exit code: 0
```Here is a sample of the files stored on the offsite server:
 
D:\MySQL\MySQL
```
2012-05-09-23-00_mysql-backup.tar.7z
2012-05-10-23-00_mysql-backup.tar.7z
2012-05-11-23-00_mysql-backup.tar.7z
2012-05-12-23-00_mysql-backup.tar.7z
2012-05-13-23-00_mysql-backup.tar.7z
2012-05-14-23-00_mysql-backup.tar.7z
2012-05-15-23-00_mysql-backup.tar.7z
2012-05-16-23-00_mysql-backup.tar.7z
2012-05-17-23-00_mysql-backup.tar.7z
2012-05-18-23-00_mysql-backup.tar.7z
2012-05-19-23-00_mysql-backup.tar.7z
```

---

### Post by LHammonds on 2017-10-04
[size=5]Database Backup On Demand[/size]

This script is designed to run every minute looking for key files. If a specific file shows up on the samba share, it will trigger an immediate backup of the specified database. This is helpful when scheduling the backup of an app server and coordinating the backup of the database at the same time. The remote app backup script can trigger the database backup anytime it runs no matter if it is schedule via crontab or manually run.

For an example of a app server configured to make use of the script, take a look at the [MediaWiki thread](http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=226).

If a file such as /srv/samba/share/mediawiki shows up, this script will delete that file and perform a backup of the mediawiki database.

To configure this script for your own needs, modify the IF statements between lines 116 and 130.

/var/scripts/prod/mysql-db-backup.sh
```
#!/bin/bash
#############################################
## Name          : mysql-db-backup.sh
## Version       : 1.2
## Date          : 2017-09-01
## Author        : LHammonds
## Purpose       : Backup of a single database
## Compatibility : Verified on Ubuntu Server 10.04 - 12.04 LTS, MySQL 5.1.62 - 5.5.22
## Requirements  : p7zip-full (if ArchiveMethod=tar.7z), sendemail
## Run Frequency : As needed
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
## 2012-05-14 LTH Created script.
## 2017-04-13 LTH Corrected variable casing.
## 2017-09-01 LTH Handle folder creation upon 1st time run.
#############################################

## Import common variables and functions. ##
source /var/scripts/common/standard.conf

LogFile="${LogDir}/mysql-db-backup.log"
LockFile="${TempDir}/mysql-db-backup.lock"
TargetDir="${BackupDir}/mysql-db"
OffsiteBackDir="${OffsiteDir}/${Hostname}/mysql-db"
ErrorFlag=0

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
  if [ ${OffsiteBackDir} = "" ]; then
    ## Make darn sure the path is not empty since we do NOT
    ## want to start purging files from a random location.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- Purge error: OffsiteBackDir site variable is empty!" >> ${LogFile}
    return 9
  fi
  ## Get the name of the oldest file.
  OldestFile=`ls -1t ${OffsiteBackDir} | tail -1`
  if [ "${OldestFile}" = "" ]; then
    ## Error. Filename variable empty.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- Purge error: OldestFile variable is empty." >> ${LogFile}
    return 9
  else   
    FileSize=`ls -lak "${OffsiteBackDir}/${OldestFile}" | awk '{ print $5 }' | sed -e :a -e 's/\(.*[0-9]\)\([0-9]\{3\}\)/\1,\2/;ta'`
    echo "`date +%Y-%m-%d_%H:%M:%S` --- Purging old file: ${OffsiteBackDir}/${OldestFile}, Size = ${FileSize} kb" >> ${LogFile}
    rm "${OffsiteBackDir}/${OldestFile}"
    if [ -f "${OffsiteBackDir}/${OldestFile}" ]; then
      ## File still exists.  Return error.
      return 1
    else
      return 0
    fi
  fi
}

function f_cleanup()
{
  if [ -f ${LockFile} ];then
    ## Remove lock file so other rsync jobs can run.
    rm ${LockFile} 1>/dev/null 2>&1
  fi
  if [[ "${TargetDir}" != "" && "{TargetDir}" != "/" ]]; then
    ## Remove local backup files.
    rm -rf ${TargetDir}/*
  fi
}

function f_emergencyexit()
{
  ## Purpose: Exit script as cleanly as possible.
  ## Parameter #1 = Error Code
  f_cleanup
  echo "`date +%Y-%m-%d_%H:%M:%S` - MySQL backup exit code: ${ErrorFlag}" >> ${LogFile}
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

if [ -f ${LockFile} ]; then
  ## Program lock file detected.  Abort script.
  echo "Lock file detected, aborting script."
  f_sendmail "[Failure] MySQL DB Backup Aborted - Lock File" "This script tried to run but detected the lock file: ${LockFile}\n\nPlease check to make sure the file does not remain when this script is not actually running."
  exit 1
else
  ## Create the lock file to ensure only one script is running at a time.
  echo "`date +%Y-%m-%d_%H:%M:%S` ${ScriptName}" > ${LockFile}
fi

## Figure out which database will be backed up. Only one per run.
if [ -f "${ShareDir}/mediawiki" ]; then
  DatabaseName="mediawiki"
  rm "${ShareDir}/mediawiki"
elif [ -f "${ShareDir}/intranetwp" ]; then
  DatabaseName="intranetwp"
  rm "${ShareDir}/intranetwp"
elif [ -f "${ShareDir}/intranetwpdev" ]; then
  DatabaseName="intranetwpdev"
  rm "${ShareDir}/intranetwpdev"
elif [ -f "${ShareDir}/owncloud" ]; then
  DatabaseName="owncloud"
  rm "${ShareDir}/owncloud"
elif [ -f "${ShareDir}/phpbb" ]; then
  DatabaseName="phpbb"
  rm "${ShareDir}/phpbb"
elif [ -f "${ShareDir}/wordpress" ]; then
  DatabaseName="wordpress"
  rm "${ShareDir}/wordpress"
fi
if [[ "${DatabaseName}" = "" ]]; then
  echo "No database selected. Exiting script."
  f_cleanup 0
  exit 0
fi

ArchiveFile="`date +%Y-%m-%d-%H-%M`_mysql-db-${DatabaseName}.${ArchiveMethod}"

echo "`date +%Y-%m-%d_%H:%M:%S` - MySQL ${DatabaseName} backup started." >> ${LogFile}

## If the 7-Zip archive method is specified, make sure the package is installed.
if [ "${ArchiveMethod}" = "tar.7z" ]; then
  if [ ! -f "/usr/bin/7za" ]; then
    ## Required package (7-Zip) not installed.
    echo "`date +%Y-%m-%d_%H:%M:%S` - CRITICAL ERROR: 7-Zip package not installed.  Please install by typing 'aptitude -y install p7zip-full'" >> ${LogFile}
    ErrorFlag=1
    f_emergencyexit ${ErrorFlag}
  fi
fi

StartTime="$(date +%s)"

## Backup individual database.
${MYSQLDUMP} ${DatabaseName} > ${TargetDir}/${DatabaseName}.sql
## Create database sub-folder.
mkdir -p ${TargetDir}/${DatabaseName}
## Export each table in the database individually.
for SingleTable in `echo "show tables" | $MYSQL ${DatabaseName}|grep -v Tables_in_`;
do
  FileName=${TargetDir}/${DatabaseName}/${SingleTable}.sql
  case "${SingleTable}" in
    general_log)
      ${MYSQLDUMP} ${DatabaseName} ${SingleTable} --skip-lock-tables > ${FileName}
      ;;
    slow_log)
      ${MYSQLDUMP} ${DatabaseName} ${SingleTable} --skip-lock-tables > ${FileName}
      ;;
    *)
      ${MYSQLDUMP} ${DatabaseName} ${SingleTable} > ${FileName}
      ;;
  esac
done

## Compress the backup into a single file based on archive method specified.
echo "`date +%Y-%m-%d_%H:%M:%S` --- Compressing archive: ${TempDir}/${ArchiveFile}" >> ${LogFile}
case "${ArchiveMethod}" in
tar.7z)
  ${TAR} -cpf - ${TargetDir} | ${MY7ZIP} a -si -mx=7 -w${TempDir} ${TempDir}/${ArchiveFile} 1>/dev/null 2>&1
  ReturnValue=$?
  ## Restore using one of the following commands (do not uncomment, only for notation):
  ## 7za x -so -w/tmp ${TempDir}/${ArchiveFile} | tar -C / -xf -
  ## 7za x -so -w/tmp ${TempDir}/${ArchiveFile} | tar -C ${TempDir}/restore --strip-components=1 -xf -
  ;;
tgz)
  ${TAR} -cpzf ${TempDir}/${ArchiveFile} ${TargetDir} 1>/dev/null 2>&1
  ReturnValue=$?
  ## Restore using one of the following commands (do not uncomment, only for notation):
  ## tar -C / -xzf ${TempDir}/${ArchiveFile}
  ## tar -C ${TempDir}/restore --strip-components=1 -xzf ${TempDir}/${ArchiveFile}
  ;;
*)
  ${TAR} -cpzf ${TempDir}/${ArchiveFile} ${TargetDir} 1>/dev/null 2>&1
  ReturnValue=$?
  ;;
esac

if [ ${ReturnValue} -ne 0 ]; then
  ## tar command failed.  Send warning email.
  f_sendmail "[Failure] MySQL Backup Failure - tar" "tar failed with return value of ${ReturnValue}"
  ErrorFlag=$((${ErrorFlag} + 2))
fi

## Mount the remote folder. ##
f_mount

if [ -f ${OffsiteTestFile} ]; then
  ## Offline file found. Assuming failed mount.
  ErrorFlag=$((${ErrorFlag} + 16))
  echo "`date +%Y-%m-%d_%H:%M:%S` --- ERROR: Offline file detected: ${OffsiteTestFile}" >> ${LogFile}
  f_emergencyexit ${ErrorFlag}
fi

## If destination folder does not exist, create it. Mainly for 1st time use.
if [ ! -d ${OffsiteBackDir} ]; then
  mkdir -p ${OffsiteBackDir}
fi

FreeSpace=`df -k ${OffsiteDir} | grep ${OffsiteDir} | awk '{ print $3 }'`
BackupSize=`ls -lak "${TempDir}/${ArchiveFile}" | awk '{ print $5 }'`

## Make sure space is available on the remote server to copy the file.
if [ ${FreeSpace} -lt ${BackupSize} ]; then
  ## Not enough free space available.  Purge existing backups until there is room.
  EnoughSpace=0
  while [ ${EnoughSpace} -eq 0 ]
  do
    f_PurgeOldestArchive
    ReturnValue=$?
    case ${ReturnValue} in
    1)
      ## Cannot purge archives to free up space.  End program gracefully.
      echo "`date +%Y-%m-%d_%H:%M:%S` - ERROR: Not enough free space on ${OffsiteBackDir} and cannot purge old archives.  Script aborted." >> ${LogFile}
      ## Stop and exit the script with an error code.
      ErrorFlag=$((${ErrorFlag} + 4))
      f_emergencyexit ${ErrorFlag}
      ;;
    9)
      ## Configuration error, end program gracefully.
      echo "`date +%Y-%m-%d_%H:%M:%S` - ERROR: Configuration problem. Script aborted." >> ${LogFile}
      ## Stop and exit the script with an error code.
      ErrorFlag=$((${ErrorFlag} + 8))
      f_emergencyexit ${ErrorFlag}
      ;;
    esac
    FreeSpace=`df -k ${OffsiteDir} | grep ${OffsiteDir} | awk '{ print $3 }'`
    if [ ${FreeSpace} -gt ${BackupSize} ]; then
      ## Enough space is now available.
      EnoughSpace=1
    else
      ## Not enough space is available yet.
      EnoughSpace=0
    fi
  done
fi

## Copy the backup to an offsite storage location.
echo "`date +%Y-%m-%d_%H:%M:%S` --- Copying archive file to offsite location." >> ${LogFile}
cp ${TempDir}/${ArchiveFile} ${OffsiteBackDir}/${ArchiveFile} 1>/dev/null 2>&1
if [ ! -f ${OffsiteBackDir}/${ArchiveFile} ]; then
  ## NON-FATAL ERROR: Copy command did not work.  Send email notification.
  echo "`date +%Y-%m-%d_%H:%M:%S` --- WARNING: Remote copy failed. ${OffsiteBackDir}/${ArchiveFile} does not exist!" >> ${LogFile}
  f_sendmail "[Failure] MySQL Backup Failure - Remote Copy" "Remote copy failed. ${OffsiteBackDir}/${ArchiveFile} does not exist\n\nBackup file still remains in this location: ${Hostname}:${TempDir}/${ArchiveFile}"
else
  ## Remove local copy of the compressed backup file
  rm ${TempDir}/${ArchiveFile}
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

echo "`date +%Y-%m-%d_%H:%M:%S` --- Total backup time: ${Hours} hour(s) ${Minutes} minute(s) ${Seconds} second(s)" >> ${LogFile}

echo "`date +%Y-%m-%d_%H:%M:%S` - MySQL ${DatabaseName} backup completed." >> ${LogFile}

## Perform cleanup routine.
f_cleanup

## Email the result to the administrator.
if [ ${ErrorFlag} -eq 0 ]; then
  f_sendmail "[Success] MySQL DB Backup Success" "MySQL backup completed with no errors."
else
  f_sendmail "[Failure] MySQL DB Backup ERROR" "MySQL backup failed.  ErrorFlag = ${ErrorFlag}"
fi

## Exit with the combined return code value.
exit ${ErrorFlag}


```Here is a sample of the log output:
 
/var/log/mysql-db-backup.log
```
2012-05-16_20:00:01 - MySQL mediawiki backup started.
2012-05-16_20:00:02 --- Compressing archive: /var/temp/2012-05-16-20-00_mysql-db-mediawiki.tar.7z
2012-05-16_20:00:05 --- Copying archive file to offsite location.
2012-05-16_20:00:06 --- Total backup time: 0 hour(s) 0 minute(s) 5 second(s)
2012-05-16_20:00:06 - MySQL mediawiki backup completed.
2012-05-17_20:00:02 - MySQL mediawiki backup started.
2012-05-17_20:00:02 --- Compressing archive: /var/temp/2012-05-17-20-00_mysql-db-mediawiki.tar.7z
2012-05-17_20:00:07 --- Copying archive file to offsite location.
2012-05-17_20:00:11 --- Total backup time: 0 hour(s) 0 minute(s) 9 second(s)
2012-05-17_20:00:11 - MySQL mediawiki backup completed.
2012-05-18_20:01:01 - MySQL mediawiki backup started.
2012-05-18_20:01:02 --- Compressing archive: /var/temp/2012-05-18-20-01_mysql-db-mediawiki.tar.7z
2012-05-18_20:01:03 --- Copying archive file to offsite location.
2012-05-18_20:01:04 --- Total backup time: 0 hour(s) 0 minute(s) 3 second(s)
2012-05-18_20:01:04 - MySQL mediawiki backup completed.
2012-05-19_20:01:01 - MySQL mediawiki backup started.
2012-05-19_20:01:02 --- Compressing archive: /var/temp/2012-05-19-20-01_mysql-db-mediawiki.tar.7z
2012-05-19_20:01:03 --- Copying archive file to offsite location.
2012-05-19_20:01:03 --- Total backup time: 0 hour(s) 0 minute(s) 2 second(s)
2012-05-19_20:01:03 - MySQL mediawiki backup completed.
```Here is a sample of the files stored on the offsite server:
 
D:\MySQL\MySQL-DB
```
2012-05-16-20-00_mysql-db-mediawiki.tar.7z
2012-05-17-20-00_mysql-db-mediawiki.tar.7z
2012-05-18-20-01_mysql-db-mediawiki.tar.7z
2012-05-19-20-01_mysql-db-mediawiki.tar.7z
```

---

### Post by LHammonds on 2017-10-04
[size=5]Migrate Database from Old Server[/size]

You can use the full backup automatically made by the "mysql-backup.sh" script (/bak/mysql/mysql-all.sql) if you have that already running or you can create a manual backup.  The steps below will document how to do it manually but you could just as easily use your existing backup file(s).

Here are the steps to import the databases from the old server into the new server:


[list=1]
[*]On the old server, make a full backup of the current database by typing: **mysqldump --all-databases > /tmp/mysql-all.sql**
[*]Transfer mysql-all.sql to the new server (via WinSCP or other means)
[*]On the new server, Import the all-database file by typing: **mysql < /tmp/mysql-all.sql**
[*]Make a full backup of the current database by typing: **mysqldump --all-databases > /tmp/all-db-after.sql**
[*]Verify that your databases, tables, rows and users are now on the new server
[*]Cleanup by removing the database archives: **rm /tmp/*.sql**
[*]Now would be a good time to run your backup script: **/var/scripts/prod/mysql-backup.sh**
[/list]

Now you can point your apps to the new database server or shutdown the old server and then change the IP of this server to match the old server.

NOTE: Saving the following lines in case I expand this further by showing how to extract an archive 1st and then restore from that.

[list]
[*]Make a restore folder by typing: **mkdir /tmp/restore**
[*]Extract the archive by typing: **7za x -so -w/tmp /tmp/*.7z | tar -C /tmp/restore --strip-components=3 -xf -**
[/list]


NOTE: If you see the following error in the syslog, especially after doing an "apt-get upgrade" and noticing the mysqld service stopped, you need to simply run "**mysql_upgrade**" to fix the problem. [Reference Bug](https://bugs.mysql.com/bug.php?id=29378)

```

Jun  1 14:25:48 srv-mysql mysqld_safe[23145]: ERROR: 1136  Column count doesn't match value count at row 1
Jun  1 14:25:48 srv-mysql mysqld_safe[23145]: 2017-06-01 14:25:48 140594627692800 [ERROR] Aborting
Jun  1 14:25:50 srv-mysql mysqld_safe[23145]: Installation of system tables failed!
```

---

### Post by LHammonds on 2017-10-04
[size=5]Crontab Schedule[/size]

I would not advise anyone to ever "edit" a live crontab schedule by typing "crontab -e" but rather edit a saved schedule file and then load the schedule file. This will allow you to make backups of the schedule so you can always go back to a known-good schedule or at least back to the way it was before you made a change...assuming you always work with a copy of the schedule 1st.

Here is my root crontab scheduling file:

/var/scripts/data/crontab.root
```
########################################
# Name: Crontab Schedule for root user
# Author: LHammonds
############# Update Log ###############
# 2012-05-20 - LTH - Created schedule
########################################
 
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
 
# m h dom mon dow command
 
#
# Adjust the time clock
#
0 1-23 * * * /usr/sbin/ntpdate ntp.ubuntu.com > /dev/null 2>&1
#
# Backup MySQL Server
#
0 23 * * * /var/scripts/prod/mysql-backup.sh > /dev/null 2>&1
#
# Backup MySQL Database On Demand
#
0-59 * * * * /var/scripts/prod/mysql-db-backup.sh > /dev/null 2>&1
#
# Daily check for available space on /var
#
0 1 * * * /var/scripts/prod/check-storage.sh opt 50 50 > /dev/null 2>&1
#
# Daily check for available space on /backup
#
0 2 * * * /var/scripts/prod/check-storage.sh bak 50 50 > /dev/null 2>&1
#
# Daily check for available space on /temp
#
0 3 * * * /var/scripts/prod/check-storage.sh tmp 50 50 > /dev/null 2>&1
```

Once you have created the file, make sure appropriate permissions are set by typing the following:
```
chown root:root /var/scripts/data/crontab.root
chmod 0600 /var/scripts/data/crontab.root
```
To enable the root schedule using this file, type the following:
```
crontab -u root /var/scripts/data/crontab.root
```
To disable the root schedule, type the following:
```
touch /tmp/deleteme
crontab -u root /tmp/deleteme
rm /tmp/deleteme
```
If you need to modify the schedule, make a backup copy 1st. For example:
```
cp /var/scripts/data/crontab.root /var/scripts/data/2011-11-28-crontab.root
vi /var/scripts/data/crontab.root (make your changes)
crontab -u root /var/scripts/data/crontab.root
```

---

### Post by LHammonds on 2017-10-04
[size=5]Web Front-end[/size]

Someone asked if there was a graphical way to manage the server. After a long sigh, I mentioned that phpmyadmin is a popular front-end.

Here is how you install it:
```
apt install phpmyadmin
```

I would recommend uninstalling it after your initial setup since having an Apache web service tends to eat away at your CPU/RAM. My corporate DB server runs happily on 512 MB of RAM.  Security is also reduced due to additional services upon which can be attacked for vulnerabilities.

---

