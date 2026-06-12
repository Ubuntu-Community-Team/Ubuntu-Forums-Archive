---
title: "custom service start at boot"
date: 2011-07-06
forum: Server Platforms
---

### Post by balderdk on 2011-07-06
Hi all

I have a few problems getting a custom service/daemon to auto-start at boot.

I'm running ubuntu 11.04 Server amd64 edition.

One of the services is a Teamspeak3 server I'm trying to start. I would like it to start up automatically on boot.

ts3 already have a script with start/stop commands so all i have done is make a little script for it to get it to run as the correct user.

```

#!/bin/sh
### BEGIN INIT INFO
# Provides:          ts3
# Required-Start:    $all
# Required-Stop:     $local_fs $remote_fs $network $syslog $named
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# X-Interactive:     true
# Short-Description: Start/stop ts3 server
### END INIT INFO

TSUSER="ts3user"
TS3PATH="/home/ts3user/teamspeak3-server_linux-amd64"

su $TSUSER -c "cd $TS3PATH; ./ts3server_startscript.sh $1"
exit 0

```the script is in /etc/init.d/

i have tried adding it to the startup first with 

```
update-rc.d ts3 defaults
```but that was before i learned about the new dependencies way of doing it.

so i added the INIT info and tried to add the service using rcconf still no luck.

What i need better understanding of:

1. How init works, is the $all variable actually working?
2. Could it be a leftover from the previous attempt to get the service up that's preventing this from working? (residual code)
3. Where can i see if it failed to start during boot, or if it was even called?

So if you can answer one or more of these question or point me in the right direction i would appreciate it. :)

---

### Post by balderdk on 2011-07-07
no one able to give me a few pointers on this one?

---

### Post by rubylaser on 2011-07-07
Does this script execute from the command line if you try to run it by hand? 

Also, what are the contents of this file?
```
cat /home/ts3user/teamspeak3-server_linux-amd64/ts3server_startscript.sh
```

**EDIT:** A quick Google, turned this up.  [This]("http://robert.penz.name/296/howto-install-teamspeak-3-server-on-ubuntu-10-04-lucid/") looks like a perfectly functional init script, so I'd probably just try it this way.

---

### Post by balderdk on 2011-07-07
hey thanks for replying, i have been digging a bit in the mean time and here is what i found out so far.

First off i have changed my script alot and here is what it looks like now.

```
#! /bin/sh
### BEGIN INIT INFO
# Provides: teamspeak
# Required-Start: $all
# Required-Stop: $local_fs $remote_fs $network $syslog $named
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# X-Interactive: true
# Short-Description: TeamSpeak Server Daemon
# Description: Starts/Stops/Restarts the TeamSpeak Server Daemon
### END INIT INFO

set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="TeamSpeak3 3.0.0-beta30"
NAME=ts3srv
USER=ts3user
DIR=/opt/ts3/teamspeak3-server_linux-amd64/
DAEMON=$DIR/ts3server_startscript.sh
#PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME

# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0
cd $DIR
sudo -u $USER ./ts3server_startscript.sh $1
```so that's pretty close to the one you linked :)

I'm getting the following error now:

```
2011-07-07 13:53:07.735575|ERROR   |              |   | TS3ANetwork::ResolveHostName failed error: -2 (Name or service not known) 0
2011-07-07 13:53:07.737372|ERROR   |              |   | TS3ANetwork::ResolveHostName failed error: -2 (Name or service not known) 2
2011-07-07 13:53:07.738492|ERROR   |Accounting    |   | Unable to connect to accounting server
2011-07-07 13:53:07.738597|ERROR   |ServerLibPriv |   | Server() error while starting servermanager, error: unable to connect to accounting server

```This is from the ts3 log file, so it seems that the server is starting BUT not having any dns service at the time, so it shuts down again because it cant resolve the hostname.

The script it self works perfectly, i can run it when i log in by using sudo /etc/init.d/ts3srv start 

I have then read up in the thread that you linked than many are having this problem and are fixing it by adding 

```
update-rc.d -f ts3srv remove
update-rc.d ts3srv defaults 99 01
```But this isen't working for everyone, and no luck here either.


So i wonder if there is anything else i can add to make sure the dns is up and running before it starts?

also here is the cat you wanted of the ts3 script (i'm 100% sure that's not the problem btw since it's the std script and it does work)

```
#!/bin/sh
# Copyright (c) 2010 TeamSpeak Systems GmbH
# All rights reserved

COMMANDLINE_PARAMETERS="${2}" #add any command line parameters you want to pass here
D1=$(readlink -f "$0")
BINARYPATH="$(dirname "${D1}")"
cd "${BINARYPATH}"
LIBRARYPATH="$(pwd)"

if [ -e "ts3server_linux_x86" ]; then
        BINARYNAME="ts3server_linux_x86"
elif [ -e "ts3server_linux_amd64" ]; then
        BINARYNAME="ts3server_linux_amd64"
elif [ -e "ts3server_freebsd_x86" ]; then
        BINARYNAME="ts3server_freebsd_x86"
elif [ -e "ts3server_freebsd_amd64" ]; then
        BINARYNAME="ts3server_freebsd_amd64"
else
        echo "Could not locate binary file, aborting"
        exit 5
fi

case "$1" in
        start)
                if [ -e ts3server.pid ]; then
                        if ( kill -0 $(cat ts3server.pid) 2> /dev/null ); then
                                echo "The server is already running, try restart or stop"
                                exit 1
                        else
                                echo "ts3server.pid found, but no server running. Possibly your previously started server crashed"
                                echo "Please view the logfile for details."
                                rm ts3server.pid
                        fi
                fi
                if [ "${UID}" = "0" ]; then
                        echo WARNING ! For security reasons we advise: DO NOT RUN THE SERVER AS ROOT
                        c=1
                        while [ "$c" -le 10 ]; do
                                echo -n "!"
                                sleep 1
                                c=$((++c))
                        done
                        echo "!"
                fi
                echo "Starting the TeamSpeak 3 server"
                if [ -e "$BINARYNAME" ]; then
                        if [ ! -x "$BINARYNAME" ]; then
                                echo "${BINARYNAME} is not executable, trying to set it"
                                chmod u+x "${BINARYNAME}"
                        fi
                        if [ -x "$BINARYNAME" ]; then
                                export LD_LIBRARY_PATH="${LIBRARYPATH}:${LD_LIBRARY_PATH}"
                                "./${BINARYNAME}" ${COMMANDLINE_PARAMETERS} > /dev/null &
                                echo $! > ts3server.pid
                                echo "TeamSpeak 3 server started, for details please view the log file"
                        else
                                echo "${BINARNAME} is not exectuable, cannot start TeamSpeak 3 server"
                        fi
                else
                        echo "Could not find binary, aborting"
                        exit 5
                fi
        ;;
        stop)
                if [ -e ts3server.pid ]; then
                        echo -n "Stopping the TeamSpeak 3 server"
                        if ( kill -TERM $(cat ts3server.pid) 2> /dev/null ); then
                                c=1
                                while [ "$c" -le 300 ]; do
                                        if ( kill -0 $(cat ts3server.pid) 2> /dev/null ); then
                                                echo -n "."
                                                sleep 1
                                        else
                                                break
                                        fi
                                        c=$((++c))
                                done
                        fi
                        if ( kill -0 $(cat ts3server.pid) 2> /dev/null ); then
                                echo "Server is not shutting down cleanly - killing"
                                kill -KILL $(cat ts3server.pid)
                        else
                                echo "done"
                        fi
                        rm ts3server.pid
                else
                        echo "No server running (ts3server.pid is missing)"
                        exit 7
                fi
        ;;
        restart)
                $0 stop && $0 start || exit 1
        ;;
        status)
                if [ -e ts3server.pid ]; then
                        if ( kill -0 $(cat ts3server.pid) 2> /dev/null ); then
                                echo "Server is running"
                        else
                                echo "Server seems to have died"
                        fi
                else
                        echo "No server running (ts3server.pid is missing)"
                fi
        ;;
        *)
                echo "Usage: ${0} {start|stop|restart|status}"
                exit 2
esac
exit 0


```

---

### Post by rubylaser on 2011-07-07
The easiest way to test would be to try to ping the accounting server's hostname prior to trying to start the Teamspeak Server.  If it fails have it sleep for 60 seconds, then try again.

This needs to be changed...
```
update-rc.d ts3srv defaults 99 01
```
to this...
```
update-rc.d ts3srv defaults 99
```
The 99 tells it to be the last thing to start, but by adding the 01 (not the correct format anyways, you'd want it as 0 1), your attempting to tell it to start on runlevels 0 and 1.  Just leave it at defaults and 99, that will be fine.  I suspect this may solve your problem.

---

### Post by balderdk on 2011-07-07
> **rubylaser said:**
> The 99 tells it to be the last thing to start, but by adding the 01 (not the correct format anyways, you'd want it as 0 1), your attempting to tell it to start on runlevels 0 and 1.  Just leave it at defaults and 99, that will be fine.  I suspect this may solve your problem.

Hi again

According to [this page]("https://help.ubuntu.com/community/UbuntuBootupHowto") the format should be correct

> ```
sudo update-rc.d myscript defaults 98 02
```98  and 02 are the start and stop sequence numbers respectively. Both are  numbers between 00 and 99 and specify how early or late a service is  started or killed. If a service is started late, it should be killed  early and vice-versa. A good rule of thumb is to make the stop sequence  number equal to 100 minus the start sequence number. But i tried it the way you described with only writing 99 and still a no go i'll look into changing the script to look trying to ping something on the outside first :)

---

### Post by rubylaser on 2011-07-07
Thanks for sharing, I've never used the values like that for shutdown levels, but I guess I should start :)  Makes sense after reading it.

Something like this is easy to do.
```

host=`ping -c1 google.com  | grep unknown`
if [ ! "$host" = "" ]; then
        echo "Host not known"
else
        echo "DNS is working!!!"
fi

```

Just replace the echo "DNS is working!!!" with your Teamspeak server startup line.

---

### Post by balderdk on 2011-07-08
Thanks for the example i finally got it working now i had to change the shell script a bit though, the example you provided alwayse returns "DNS is working" on my machine, i must admit that my understanding of exacly shell scripting is some what limited :)

Here is the script I'm using now that's working

Content of /etc/init.d/ts3srv

```
#! /bin/sh
### BEGIN INIT INFO
# Provides: teamspeak
# Required-Start: $local_fs $remote_fs $network $syslog $named $networking
# Required-Stop: $local_fs $remote_fs $network $syslog $named $networking
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# X-Interactive: true
# Short-Description: TeamSpeak Server Daemon
# Description: Starts/Stops/Restarts the TeamSpeak Server Daemon
### END INIT INFO

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="TeamSpeak3 3.0.0-beta30"
NAME=ts3srv
USER=ts3user
DIR=/opt/ts3/teamspeak3-server_linux-amd64/
DAEMON=$DIR/ts3server_startscript.sh
#PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME

set -e

# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0

if [ "$1" = "start" ]; then
        ping -c 1 google.com
        if [ $? != 0 ]; then
                sleep 30
        fi
fi
cd $DIR
sudo -u $USER ./ts3server_startscript.sh $1

```

i read up that ping returns a true/false if it suceeded or not so you just grapping that with the $? variable.

and i added the script to the startup by running:

```
sudo update-rc.d ts3srv defaults 98 02
```

Thanks for the help rubylaser, all it takes sometimes is a bit of ping pong of ideas :)

---

