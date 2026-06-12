---
title: "Dropbox not starting on headless Server 14.04"
date: 2014-10-10
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2014-10-10
Hi all

Am learning how to setup a headless Ubuntu Server 14.04 and have installed Dropbox as per instruction's here,
[http://www.jamescoyle.net/how-to/1147-setup-headless-dropbox-sync-client](http://www.jamescoyle.net/how-to/1147-setup-headless-dropbox-sync-client)

> Add one of the below scripts to your init.d folder and substitute [USER] for the list of users who will use the client.
Have added into /etc/init.d/dropbox
```
#!/bin/sh
#dropbox service
DROPBOX_USERS="[USER]"
 
DAEMON=.dropbox-dist/dropbox
 
start() {
   echo "Starting dropbox..."
   for dbuser in $DROPBOX_USERS; do
       HOMEDIR=`getent passwd $dbuser | cut -d: -f6`
       if [ -x $HOMEDIR/$DAEMON ]; then
           HOME="$HOMEDIR" start-stop-daemon -b -o -c $dbuser -S -u $dbuser -x $HOMEDIR/$DAEMON
       fi
   done
}
 
stop() {
   echo "Stopping dropbox..."
   for dbuser in $DROPBOX_USERS; do
       HOMEDIR=`getent passwd $dbuser | cut -d: -f6`
       if [ -x $HOMEDIR/$DAEMON ]; then
           start-stop-daemon -o -c $dbuser -K -u $dbuser -x $HOMEDIR/$DAEMON
       fi
   done
}
 
status() {
   for dbuser in $DROPBOX_USERS; do
       dbpid=`pgrep -u $dbuser dropbox`
       if [ -z $dbpid ] ; then
           echo "dropboxd for USER $dbuser: not running."
       else
           echo "dropboxd for USER $dbuser: running (pid $dbpid)"
       fi
   done
}
 
case "$1" in
 
   start)
       start
       ;;
   stop)
       stop
       ;;
   restart|reload|force-reload)
       stop
       start
       ;;
   status)
       status
       ;;
   *)
       echo "Usage: /etc/init.d/dropbox {start|stop|reload|force-reload|restart|status}"
       exit 1
 
esac
 
exit 0
```
 and run ```
sudo chmod +x /etc/init.d/dropbox 
sudo update-rc.d dropbox defaults
```

What appears to be wrong is the substitution for [USER] in the script, and so Dropbox is not starting with the server.

The only user is 'chris', so should the substitution be [chris], chris, or something else entirely?

TIA

---

### Post by ChrisRChamberlain on 2014-10-10
The issue of the username is resolved here.
[http://www.dropboxwiki.com/tips-and-tricks/install-dropbox-in-an-entirely-text-based-linux-environment#debianubuntu]("http://www.dropboxwiki.com/tips-and-tricks/install-dropbox-in-an-entirely-text-based-linux-environment#debianubuntu")```
#!/bin/sh
#dropbox service
DROPBOX_USERS="user1 user2"
 
DAEMON=.dropbox-dist/dropbox
 
start() {
   echo "Starting dropbox..."
   for dbuser in $DROPBOX_USERS; do
       HOMEDIR=`getent passwd $dbuser | cut -d: -f6`
       if [ -x $HOMEDIR/$DAEMON ]; then
           HOME="$HOMEDIR" start-stop-daemon -b -o -c $dbuser -S -u $dbuser -x $HOMEDIR/$DAEMON
       fi
   done
}
 
stop() {
   echo "Stopping dropbox..."
   for dbuser in $DROPBOX_USERS; do
       HOMEDIR=`getent passwd $dbuser | cut -d: -f6`
       if [ -x $HOMEDIR/$DAEMON ]; then
           start-stop-daemon -o -c $dbuser -K -u $dbuser -x $HOMEDIR/$DAEMON
       fi
   done
}
 
status() {
   for dbuser in $DROPBOX_USERS; do
       dbpid=`pgrep -u $dbuser dropbox`
       if [ -z $dbpid ] ; then
           echo "dropboxd for USER $dbuser: not running."
       else
           echo "dropboxd for USER $dbuser: running (pid $dbpid)"
       fi
   done
}
 
case "$1" in
 
   start)
       start
       ;;
   stop)
       stop
       ;;
   restart|reload|force-reload)
       stop
       start
       ;;
   status)
       status
       ;;
   *)
       echo "Usage: /etc/init.d/dropbox {start|stop|reload|force-reload|restart|status}"
       exit 1
 
esac
 
exit 0
```and /etc/init.d/dropbox has been updated without success with ```
sudo update-rc.d dropbox defaults
```
Unable to any significant difference between the scripts, but a more experienced eye may spot something

---

### Post by ChrisRChamberlain on 2014-10-13
So can start Dropbox once logged in as user 'chris' with
```
 ~/dropbox.py start
```
in a PuTTY command window.

How could that be used in a root crontab on startup?

Or any other/better way of starting Dropbox please?

TIA

---

### Post by ChrisRChamberlain on 2014-10-15
There is a gotcha on current 32bit Ubuntu 14.04 LTS install in line 5 in Ubuntu/Debian /etc/init.d/dropbox.

The file ‘.dropbox-dist/dropbox’ needs to be ‘.dropbox-dist/dropboxd’

Once corrected, all is well and Dropbox starts on reboot. :p

---

