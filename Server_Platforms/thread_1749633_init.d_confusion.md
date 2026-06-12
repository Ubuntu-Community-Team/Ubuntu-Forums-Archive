---
title: "init.d confusion"
date: 2011-05-04
forum: Server Platforms
---

### Post by trundlenut on 2011-05-04
Right, I have a server which I run Davmail on to allow me to access my exchange server with Thunderbird, it has all been working fine but I hadn't upgraded davmail since I started using it.

I was having a few little issues with davmail so I decided to update it.  In order to run davmail I used the generic version downloaded as a zip file.  I unzipped the files to /usr/bin/davmail/ and then added the properties file which set everything up.  Then to make sure that davmail always started on boot I wrote myself an init.d script which has worked fine since installation.

Today is when it all went pear shaped.  In order to upgrade I grabbed the latest version in the zip file from the davmail website, unzipped it and copied the two files and a folder to the server and then using sudo copied them into /usr/bin/davmail/.  Now davmail won't start on boot anymore, I can start it manually using 
```
sudo bash davmail.sh davmail.properties
```
and it works fine.  If I try 
```
sudo /etc/init.d/davmail start
```
it reports ```
* “davmail started”
```
but then
```
sudo /etc/init.d/davmail status
```
reports
 ```
* “Process has failed... removing pidfile”
```
The permissions for the files are still the same (I think)
```
XXX@cZZZ:/usr/bin/davmail$ ls -l
total 551152
-rw-r--r-- 1 root root    491180 2011-05-04 17:07 davmail.jar
-rw-r--r-- 1 root root       752 2011-05-04 17:19 davmail.log
-rw-r--r-- 1 root root       787 2010-12-09 21:21 davmail.properties
-rwxr-xr-x 1 root root       243 2011-05-04 17:08 davmail.sh
drwxr-xr-x 2 root root      4096 2011-05-04 17:12 lib
-rw------- 1 root root 563866257 2011-05-04 17:28 nohup.out
```

and none of the file names have changed, so I am at a bit of a loss.  I can't find any evidence of the problem in any of the log files.

Any ideas?

---

### Post by trundlenut on 2011-05-04
And here is the init.d script
```
#!/bin/sh

### BEGIN INIT INFO
# Provides:          davmail
# Required-Start:    $local_fs $remote_fs $network
# Required-Stop:     $local_fs $remote_fs $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: start and stop davmail.
### END INIT INFO

. /lib/lsb/init-functions

NAME=davmail
SCRIPT=/usr/bin/davmail/${NAME}.sh
PIDFILE=/var/run/${NAME}.pid
LOGFILE=/var/log/${NAME}.log
CONFFILE=/usr/bin/davmail/${NAME}.properties

start () {
        if [ -f $PIDFILE ]; then
           log_failure_msg “Process running already”
           exit 1
        fi
        start-stop-daemon --start -b --pidfile \
           $PIDFILE --make-pidfile \
             --exec $SCRIPT $CONFFILE $LOGFILE
        log_success_msg “$NAME started”
}

stop () {
        if [ -f $PIDFILE ]; then
           PID=`cat $PIDFILE`
           #check that the process is running
           if `ps $PID >/dev/null` ; then
                kill -HUP $PID
                log_success_msg “Process stopped”
           else
                log_failure_msg “Process not running”
           fi
           # remove pidfile anyhow
           rm $PIDFILE
        else
           log_failure_msg “Process not running”
        fi
}
case $1 in
        start)
                start
                ;;
        stop)
                stop
                ;;
        status)
                if [ -f $PIDFILE ]; then
                   PID=`cat $PIDFILE`
                   #check that the process is running
                   if `ps $PID >/dev/null` ; then
                        log_success_msg “Process running”
                   else
                        log_warning_msg “Process has failed... removing pidfile”
                        rm $PIDFILE
                   fi
                 else
                        log_success_msg “Process not running”
                 fi
                 ;;
        restart)
                 stop
                 start
                 ;;
        *)
                echo $”Usage: $0 {start|stop|status}”
                RETVAL=2
esac


```

Though I haven't changed this at all.

---

### Post by trundlenut on 2011-05-05
I'm now beginning to wonder if this was coincidental and that some other update I recently installed is having some adverse affect on init.d and upstart.

---

