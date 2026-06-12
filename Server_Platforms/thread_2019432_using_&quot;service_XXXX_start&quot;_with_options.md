---
title: "using &quot;service XXXX start&quot; with options???"
date: 2012-07-07
forum: Server Platforms
---

### Post by jdmcmillian on 2012-07-07
I need to shut down mysql, then restart it with select options.
Its not a permanent change, so changing the mysql my.cnf file is not an option.

Is there a way to pass arguments through the upstart command to the target service?

How can I do this? or do I need to write my own startup/shutdown scripts to do it?

---

### Post by CharlesA on 2012-07-07
As far as I know, you would need to either modify the current mysql startup script, or write your own.

Are you able to just start /usr/bin/mysqld with the options you want?

---

### Post by SeijiSensei on 2012-07-07
I don't have MySQL installed on the machine I'm on at the moment, but is there a file called /etc/default/mysql?  Oftentimes you can tweak command-line options by changing the corresponding file in /etc/default.

---

### Post by jdmcmillian on 2012-07-07
I was afraid that was the case, but was hoping to keep it simple.... sigh... time to write script... Thanks for the replies.

For the record, 

        service XXXX start

does not allow options to be passed to the service being started.

---

### Post by SeijiSensei on 2012-07-07
Well if you can't find a way to manipulate the options in /etc/default/mysql, you could simply add them manually to the line /etc/init.d/mysql that starts the server.  I usually make a copy of the distribution version of that file, edit the copy, then do this:

```

cd /etc/init.d
sudo cp mysql mysql.mine
[edit mysql.mine accordingly]
sudo mv mysql mysql.dist
sudo ln -s mysql.mine mysql
sudo service mysql restart

```

Now if I need to switch back to the distribution version, I just delete the symlink to mysql.mine and link to the original copy.

---

### Post by jdmcmillian on 2012-07-08
Thanks,

But I broker down and wrote some bash scripts for it.  The goal was to be able to turn disconnect mysql from anything outside of the host machine (the network) during backups, this has more to do with client software that connects to the SQL server, and forcing the client to fail over to the replication/backup server during this period.  Anyways.. heres the code,placed here if anyone else wants/needs it or desires to modify it.

These scripts work with automysqlbackup, the proper setting in automysqlbackup.config also need to be set.  Annotation is sparse, but gets the point across where its at.

Code to be placed in "mysql-backup-pre.sh"
```

#!/bin/bash
#       This is really is inelegent, but the paths are requied by various calls, this really should be exported by automysqlbackup
HEADER="AutoMySQLBackup Pre-Process"

PATH=${PATH}:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

echo "${HEADER} : Loading Automysqlbackup Configuration"
AUTOMYSQLBACKUPCONFIG=/etc/automation/automysqlbackup.config
BASETIMEOUT=60
echo "${HEADER} : Initializing Pre Backup Process"
WHICH=`which which`
SERVICE=`${WHICH} service`
STOP=`${WHICH} stop`
SLEEP=`${WHICH} sleep`
MYSQL=`${WHICH} mysql`
MYSQLD=`${WHICH} mysqld`
MYSQLADMIN=`${WHICH} mysqladmin`

if [ ! -f ${AUTOMYSQLBACKUPCONFIG} ]; then
        echo "${HEADER} : Error: Unable to load automysqlbackup.config file at $AUTOMYSQLBACKUP.  EXITING BACKUP"
        exit 1
else
        . ${AUTOMYSQLBACKUPCONFIG}
fi

#       assign variable information
PIDFILE=`cat /etc/mysql/my.cnf | grep pid-file | awk '{print $3}'`

if [ ! -f ${PIDFILE} ]; then
        echo "${HEADER} : Unable to locate PID file at $PIDFILE"
        exit 1
fi

PID=`cat ${PIDFILE}`

#       Verify mysqld is running
RUNNING=`ps -ef | grep "$PID" | grep "$MYSQLD" | wc -l`

#       Exit with error if mysqld is not running
if [ ${RUNNING} -eq 0 ]; then
        echo "${HEADER} : Unable to locate running instance of MYSQLD, despite PID file presence.  EXITING BACKUP"
        exit 1
fi

#       Stop mysqld
echo "${HEADER} : Stopping MYSQL PID:$PID"
${********* mysql stop

#       wait up to 30 seconds for it to stop
TIMEOUT=${BASETIMEOUT}
while [ ${TIMEOUT} -gt 0 -a ${RUNNING} -gt 0 ]
do
        TIMEOUT=$((${TIMEOUT}-1))
        ${SLEEP} 1
        RUNNING=`ps -ef | grep "$PID" | grep "$MYSQLD" | grep -v grep | wc -l`
        echo "PID: $PID   RUNNING: $RUNNING"
done
#       if its still running, then fail
if [ ${RUNNING} -gt 0 ]; then
        echo "${HEADER} : MYSQLD Failed to shutdown within a reasonable time. EXITING BACKUP"
        exit 1
fi
echo "${HEADER} : Old MYSQL Daemon stopped"

#       restart server with --skip-networking
echo "${HEADER} : Restarting MYSQL without networking"
${MYSQLD} --user=mysql --skip-networking --bind-address=127.0.0.1 > /dev/null &
echo "${HEADER} : Service is running without networking"
#       wait up to 30 seconds for it to start
TIMEOUT=${BASETIMEOUT}
while [ ${TIMEOUT} -gt 0 -a ${RUNNING} -eq 0 ]
do
        ${SLEEP} 1
        TIMEOUT=$((${TIMEOUT}-1))
        if [ -f ${PIDFILE} ]; then
                PID=`cat ${PIDFILE}`
        fi
        RUNNING=`ps -ef | grep "$PID" | grep "$MYSQLD" | wc -l`
done

#       if its not running fail
if [ ${RUNNING} -eq 0 ]; then
        echo "${HEADER} : MYSQLD Failed to start with '--skip-networking' option. EXITING BACKUP"
        exit 1
fi

# See the following web page : http://dev.mysql.com/doc/refman/5.5/en/mysqladmin.html
${MYSQLADMIN} --host=${DBHOST} --user=${USERNAME} --password=${PASSWORD} stop-slave
${MYSQLADMIN} --host=${DBHOST} --user=${USERNAME} --password=${PASSWORD} refresh
# See the following web page : http://docs.oracle.com/cd/E17952_01/refman-5.0-en/replication-administration-pausing.html
echo "STOP SLAVE IO_THREAD;" | ${MYSQL} --user=${USERNAME} --password=${PASSWORD}
echo "STOP SLAVE SQL_THREAD;" | ${MYSQL} --user=${USERNAME} --password=${PASSWORD}

#       Continue on.
echo "${HEADER} : MYSQLD started without networking"
exit 0

```Code to be placed in "mysql-backup-post.sh"
```

#!/bin/sh
#       This is really is inelegent, but the paths are requied by various calls, this really should be exported by automysqlbackup
HEADER="AutoMySQLBackup Post-Process"

PATH=${PATH}:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

echo "$HEADER : Loading Automysqlbackup Configuration"
AUTOMYSQLBACKUPCONFIG=/etc/automation/automysqlbackup.config
BASETIMEOUT=30

if [ ! -f $AUTOMYSQLBACKUPCONFIG ]; then
        echo "$HEADER : Unable to load automysqlbackup.config file at $AUTOMYSQLBACKUP.  EXITING BACKUP"
        exit 1
else
        . $AUTOMYSQLBACKUPCONFIG
fi

echo "$HEADER : Initializing Post Backup Procedure"
WHICH=`which which`
SLEEP=`$WHICH sleep`
SERVICE=`$WHICH service`
GREP=`$WHICH grep`
MYSQL=`$WHICH mysql`
MYSQLD=`$WHICH mysqld`
MYSQLADMIN=`$WHICH mysqladmin`

#       assign variable information
PIDFILE=`cat /etc/mysql/my.cnf | $GREP pid-file | awk '{print $3}'`

if [ ! -f $PIDFILE ]; then
        echo "$HEADER : Unable to locate PID file at $PIDFILE"
        exit 1
fi

PID=`cat $PIDFILE`
#PID=`ps -ef | grep $MYSQLD | grep -v grep | awk '{print $1}'`

#       Verify mysqld is running
RUNNING=`ps -ef | $GREP "$PID" | $GREP "$MYSQLD" | wc -l`

#       Exit with error if mysqld is not running
if [ $RUNNING -eq 0 ]; then
        echo "$HEADER : Unable to locate running instance of MYSQLD, despite PID file presence.  EXITING BACKUP"
        exit 1
fi

#       Stop mysqld
echo "$HEADER : Stopping MYSQLD"
$MYSQLADMIN --host=$DBHOST --user=$USERNAME --password=$PASSWORD shutdown

#       wait up to 30 seconds for it to stop
TIMEOUT=$BASETIMEOUT
while [ $TIMEOUT -gt 0 -a $RUNNING -gt 0 ]
do
        TIMEOUT=$(($TIMEOUT-1))
        $SLEEP 1
        RUNNING=`ps -ef | $GREP "$PID" | $GREP "$MYSQLD" | wc -l`
done

#       if its still running, then fail
if [ $RUNNING -gt 0 ]; then
        echo "$HEADER : MYSQLD service Failed to shutdown within a reasonable time. EXITING BACKUP"
        exit 1
fi
echo "$HEADER : MYSQLD service stopped"

echo "$HEADER : Restarting MYSQL service normally"
$SERVICE mysql start

#       wait up to 30 seconds for it to start
TIMEOUT=$BASETIMEOUT
while [ $TIMEOUT -gt 0 -a $RUNNING -eq 0 ]
do
        $SLEEP 1
        TIMEOUT=$(($TIMEOUT-1))
        if [ -f $PIDFILE ]; then
                PID=`cat $PIDFILE`
        fi
        RUNNING=`ps -ef | $GREP "$PID" | $GREP "$MYSQLD" | wc -l`
done

#       if its not running fail
if [ $RUNNING -eq 0 ]; then
        echo "$HEADER : MYSQLD Failed to start by normal service"
        exit 1
fi

# See the following web page : http://dev.mysql.com/doc/refman/5.5/en/mysqladmin.html
$MYSQLADMIN --host=$DBHOST --user=$USERNAME --password=$PASSWORD start-slave
$MYSQLADMIN --host=$DBHOST --user=$USERNAME --password=$PASSWORD refresh

# See the following web page : http://docs.oracle.com/cd/E17952_01/refman-5.0-en/replication-administration-pausing.html
echo "START SLAVE IO_THREAD;" | $MYSQL --user=$USERNAME --password=$PASSWORD
echo "START SLAVE SQL_THREAD;" | $MYSQL --user=$USERNAME --password=$PASSWORD

#       Continue on.
echo "$HEADER : MYSQL Daemon started normally"

```Thats it... it pulls all the information from the normal config file, of which whose path needs to be set for both, at the beginning of the scripts.

---

### Post by CharlesA on 2012-07-08
Just as a tiny nitpick, it is sometimes easier to just use $(...) instead of backticks (`...`) when doing command substitution.

They both do the same thing but using $(...) is easier to nest and looks better.

See here for more infos on shell expansion/command substitution:
[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_04.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_04.html)

---

