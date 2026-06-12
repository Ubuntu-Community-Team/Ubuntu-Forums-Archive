---
title: "SickBeard start on system startup"
date: 2011-12-22
forum: Server Platforms
---

### Post by JoeGoalie on 2011-12-22
I have got sickbeard to start with:
```
sudo /etc/init.d/sickbeard start
```
However, for whatever reason, it will not start unless manually invoked.  It will not start at system start.  Is there something I can change in the script to make it happen?  Is it possible that somehow the defaults were created wrong?
```
#! /bin/sh

### BEGIN INIT INFO
# Provides:          sickbeard
# Required-Start:    $all
# Required-Stop:     $all
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: starts instance of Sick Beard
# Description:       starts instance of Sick Beard using start-stop-daemon
### END INIT INFO

############### EDIT ME ##################
# path to app
APP_PATH=/home/joseph/.sickbeard

# path to python bin
DAEMON=/usr/bin/python

# Path to store PID file
PID_FILE=/var/run/sickbeard/sickbeard.pid
PID_PATH=`dirname $PID_FILE`

# script name
NAME=sickbeard

# app name
DESC=SickBeard

# user
RUN_AS=joseph

# data directory
DATA_DIR=~/.sickbeard

# startup args
DAEMON_OPTS=" SickBeard.py -q --daemon --pidfile=${PID_FILE} --datadir=${DATA_DIR}"

############### END EDIT ME ##################

test -x $DAEMON || exit 0

set -e

if [ ! -d $PID_PATH ]; then
    mkdir -p $PID_PATH
    chown $RUN_AS $PID_PATH
fi

if [ ! -d $DATA_DIR ]; then
    mkdir -p $DATA_DIR
    chown $RUN_AS $DATA_DIR
fi


case "$1" in
  start)
        echo "Starting $DESC"
        start-stop-daemon -d $APP_PATH -c $RUN_AS --start --pidfile $PID_FILE --exec $DAEMON -- $DAEMON_OPTS
        ;;
  stop)
        echo "Stopping $DESC"
        start-stop-daemon --stop --pidfile $PID_FILE --retry 15
        ;;

  restart|force-reload)
        echo "Restarting $DESC"
        start-stop-daemon --stop --pidfile $PID_FILE --retry 15
        start-stop-daemon -d $APP_PATH -c $RUN_AS --start --pidfile $PID_FILE --exec $DAEMON -- $DAEMON_OPTS
        ;;
  *)
        N=/etc/init.d/$NAME
        echo "Usage: $N {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

exit 0
```
It's just the init.ubuntu script that was in the sickbeard install modified.

---

### Post by rubylaser on 2011-12-23
Having you made it executable and actually added it to the startup scripts like this?

```
sudo -i
```
```
chmod +x /etc/init.d/sickbeard
```
```
update-rc.d sickbeard defaults
```

These steps have Sickbeard starting up on my Ubuntu server.

---

### Post by JoeGoalie on 2011-12-23
> **rubylaser said:**
> Having you made it executable and actually added it to the startup scripts like this?

```
sudo -i
```
```
chmod +x /etc/init.d/sickbeard
```
```
update-rc.d sickbeard defaults
```

These steps have Sickbeard starting up on my Ubuntu server.

I haven't done the sudo -i. What does that do? Which dorectory do I need to be in for that? I'm pretty sure I've done the others though. Let me go run them again.

---

### Post by rubylaser on 2011-12-23
sudo -i, will make you the root user until you exit the shell. That way you don't have to enter sudo in front of every command.  The main command to run is this.

```
update-rc.d sickbeard defaults
```
If you've already run that, it will say the links exist already.  I doubt that you've done this though, because it would be starting up at boot.

---

### Post by JoeGoalie on 2011-12-23
> **rubylaser said:**
> sudo -i, will make you the root user until you exit the shell. That way you don't have to enter sudo in front of every command.  The main command to run is this.

```
update-rc.d sickbeard defaults
```
If you've already run that, it will say the links exist already.  I doubt that you've done this though, because it would be starting up at boot.

Actually, I know that I've done that command.  And although I never did sudo -i I either ran it after sudo su or just putting sudo in front of the commands.

---

### Post by JoeGoalie on 2011-12-23
```
root@ubuntu:~# cd /etc/init.d/
root@ubuntu:/etc/init.d# ls -al | grep sickbeard
-rwxr-xr-x   1 root root  1679 2011-12-20 22:32 sickbeard
root@ubuntu:/etc/init.d# update-rc.d sickbeard defaults
 System start/stop links for /etc/init.d/sickbeard already exist.
```
Well, damn...  This is why I'm at a loss.  Is it possible that it set the wrong defaults when I initially set it up?  Thanks for the help so far btw.

---

### Post by rubylaser on 2011-12-23
If you've made the script executable, and added it to the runlevels, and the paths you've setup are in your /etc/init.d/sickbeard file are valid, it should start on boot.  I don't use the bundled script from Sickbeard. I'm using [Ainer's]("http://www.ainer.org/sick-beard-install-setup-configuration-guide-for-ubuntu-linux-mint/4") startup script.

```
#! /bin/sh

# Author: daemox
# Basis: Parts of the script based on and inspired by work from
#		tret (sabnzbd.org), beckstown (xbmc.org),
#		and midgetspy (sickbeard.com).
# Fixes: Alek (ainer.org), James (ainer.org), Tophicles (ainer.org),
#		croontje (sickbeard.com)
# Contact: http://www.ainer.org
# Version: 3.1

### BEGIN INIT INFO
# Provides:          sickbeard
# Required-Start:    $all
# Required-Stop:     $all
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: starts and stops sick beard
# Description:       Sick Beard is an Usenet PVR. For more information see:
#			http://www.sickbeard.com
### END INIT INFO
 
#Required -- Must Be Changed!
USER="CHANGEME" #Set Linux Mint, Ubuntu, or Debian user name here.
 
#Required -- Defaults Provided (only change if you know you need to).
HOST="127.0.0.1" #Set Sick Beard address here.
PORT="8081" #Set Sick Beard port here.
 
#Optional -- Unneeded unless you have added a user name and password to Sick Beard.
SBUSR="" #Set Sick Beard user name (if you use one) here.
SBPWD="" #Set Sick Beard password (if you use one) here.
 
#Script -- No changes needed below.
case "$1" in
start)
#Start Sick Beard and send all messages to /dev/null.
cd /home/$USER/.sickbeard
echo "Starting Sick Beard"
sudo -u $USER -EH nohup python /home/$USER/.sickbeard/SickBeard.py -q > /dev/null 2>&1 &
;;
stop)
#Shutdown Sick Beard and delete the index.html files that wget generates.
echo "Stopping Sick Beard"
wget -q --user=$SBUSR --password=$SBPWD "http://$HOST:$PORT/home/shutdown/" --delete-after
sleep 6s
;;
*)
echo "Usage: $0 {start|stop}"
exit 1
esac
 
exit 0
```

Sickbeard's bundled script should work as well as all if all of the path's and permissions are correct.  Have you checked your logfiles to see the output during boot?  They should tell you why it's failing.

---

### Post by JoeGoalie on 2011-12-23
> **rubylaser said:**
> If you've made the script executable, and added it to the runlevels, and the paths you've setup are in your /etc/init.d/sickbeard file are valid, it should start on boot.  I don't use the bundled script from Sickbeard. I'm using [Ainer's]("http://www.ainer.org/sick-beard-install-setup-configuration-guide-for-ubuntu-linux-mint/4") startup script.


Sickbeard's bundled script should work as well as all if all of the path's and permissions are correct.  Have you checked your logfiles to see the output during boot?  They should tell you why it's failing.

That's the script I tried first.  

Permissions, I can launch it manually so I don't think there are any issues there.  Where are the logs so I can check them?

---

### Post by JoeGoalie on 2011-12-23
Well, this just happened:
```
root@ubuntu:/etc/init.d# /etc/init.d/sickbeard start
Starting SickBeard
Unable to create datadir '/root/.sickbeard'
```

Is it maybe trying to run as root and can't create the directory?

---

### Post by JoeGoalie on 2011-12-23
Ok, I fixed the data directory by changing the script to have /home/joseph/.sickbeard as the data dir instead of ~/.sickbeard

I found the daemon.log file and grep'ed it for sickbeard, does this mean anything to you?  Status 2?
```
Dec 20 20:30:09 ubuntu init: sickbeard pre-start process (1348) terminated with status 2
Dec 20 20:36:36 ubuntu init: sickbeard pre-start process (1392) terminated with status 2
Dec 20 21:46:38 ubuntu init: sickbeard pre-start process (1389) terminated with status 2
```

Nvm, I didn't even notice that those are all from 3 days ago...  Not sure where else to look.

---

### Post by rubylaser on 2011-12-23
It sounds like you ran Sickbeard as root at some point and hosed the permissions.  I'd delete your Sickbeard folder and start at the beginning following Ainer's directions.

---

### Post by JoeGoalie on 2011-12-23
> **rubylaser said:**
> It sounds like you ran Sickbeard as root at some point and hosed the permissions.  I'd delete your Sickbeard folder and start at the beginning following Ainer's directions.

Damn, I've done that before.  It doesn't take long to install though.  I'll try it again.

---

### Post by JoeGoalie on 2011-12-23
> **rubylaser said:**
> It sounds like you ran Sickbeard as root at some point and hosed the permissions.  I'd delete your Sickbeard folder and start at the beginning following Ainer's directions.

Ok, so I deleted ~/.sickbeard and then unpacked and copy pasted in the contents from it back into a new folder called .sickbeard again.  Same as it was in before ```
/etc/init.d/sickbeard start
```
Works but it doesn't start at boot.

---

### Post by rubylaser on 2011-12-23
I'm setting Sickbeard up in a base Server install of Ubuntu on Virtualbox right now to make sure I'm not forgetting a step.  Are you running 10.04?

---

### Post by JoeGoalie on 2011-12-23
> **rubylaser said:**
> I'm setting Sickbeard up in a base Server install of Ubuntu on Virtualbox right now to make sure I'm not forgetting a step.  Are you running 10.04?

That's exactly what I'm doing.  I currently have WHS 2011 and  I'm using uTorrent.  I want to switch to Ubuntu Server and usenet.  Anyway, I'm using Virtualbox and 10.04.

---

### Post by rubylaser on 2011-12-23
I didn't setup the autoprocessTV script, but here's what I did and it's starting up at boot just fine. Here's what I did...

```
sudo -i
```
```
apt-get update && apt-get dist-upgrade -y
```
```
apt-get install ssh git-core build-essential screen -y
```
```
exit
```
```
cd
```

```
git clone https://github.com/midgetspy/Sick-Beard.git .sickbeard
```

```
nano /etc/init.d/sickbeard
```

paste this...
```
#! /bin/sh

# Author: daemox
# Basis: Parts of the script based on and inspired by work from
#		tret (sabnzbd.org), beckstown (xbmc.org),
#		and midgetspy (sickbeard.com).
# Fixes: Alek (ainer.org), James (ainer.org), Tophicles (ainer.org),
#		croontje (sickbeard.com)
# Contact: http://www.ainer.org
# Version: 3.1

### BEGIN INIT INFO
# Provides:          sickbeard
# Required-Start:    $all
# Required-Stop:     $all
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: starts and stops sick beard
# Description:       Sick Beard is an Usenet PVR. For more information see:
#			http://www.sickbeard.com
### END INIT INFO
 
#Required -- Must Be Changed!
USER="rubylaser" #Set Linux Mint, Ubuntu, or Debian user name here.
 
#Required -- Defaults Provided (only change if you know you need to).
HOST="127.0.0.1" #Set Sick Beard address here.
PORT="8081" #Set Sick Beard port here.
 
#Optional -- Unneeded unless you have added a user name and password to Sick Beard.
SBUSR="" #Set Sick Beard user name (if you use one) here.
SBPWD="" #Set Sick Beard password (if you use one) here.
 
#Script -- No changes needed below.
case "$1" in
start)
#Start Sick Beard and send all messages to /dev/null.
cd /home/$USER/.sickbeard
echo "Starting Sick Beard"
sudo -u $USER -EH nohup python /home/$USER/.sickbeard/SickBeard.py -q > /dev/null 2>&1 &
;;
stop)
#Shutdown Sick Beard and delete the index.html files that wget generates.
echo "Stopping Sick Beard"
wget -q --user=$SBUSR --password=$SBPWD "http://$HOST:$PORT/home/shutdown/" --delete-after
sleep 6s
;;
*)
echo "Usage: $0 {start|stop}"
exit 1
esac
 
exit 0
```

```
sudo chmod +x /etc/init.d/sickbeard
```

```
sudo update-rc.d sickbeard defaults
```

```
reboot
```

And, it's working :)


```
rubylaser@ubuntu:~$ ps aux | grep SickBeard
root       798  0.0  0.3  20924  1172 ?        S    15:46   0:00 sudo -u rubylaser -EH nohup python /home/rubylaser/.sickbeard/SickBeard.py -q
rubylaser       805  2.2  9.4 317732 35832 ?        Sl   15:46   0:01 python /home/rubylaser/.sickbeard/SickBeard.py -q
rubylaser       898  0.0  0.2   7548   856 pts/0    S+   15:47   0:00 grep SickBeard
```

---

### Post by JoeGoalie on 2011-12-23
Ok, I'll revert to an earlier snapshot and see if I follow this, if it works for me. :)

---

### Post by JoeGoalie on 2011-12-23
Wtf, that didn't work for me.  I of course changed the username in the script.  Also, I had to write the script using sudo because I didn't have write permissions if I just typed nano /etc/init.d/sickbeard

---

### Post by rubylaser on 2011-12-24
You need to install python-cheetah

```
sudo apt-get install python-cheetah
```

---

### Post by rubylaser on 2011-12-24
Here's a Virtualbox appliance with it all autostarting. The username is joseph and the password is password.  It will be about 25 minutes from my posting time before it's available for download.

[Ubuntu 10.04 x86 Virtualbox Appliance]("http://shortlink.rubylaser.net/phmcb")

---

### Post by JoeGoalie on 2011-12-24
> **rubylaser said:**
> You need to install python-cheetah

```
sudo apt-get install python-cheetah
```

I did do this...  Let me try that virtualbox and see whats going on.

---

### Post by JoeGoalie on 2011-12-25
> **rubylaser said:**
> Here's a Virtualbox appliance with it all autostarting. The username is joseph and the password is password.  It will be about 25 minutes from my posting time before it's available for download.

[Ubuntu 10.04 x86 Virtualbox Appliance]("http://shortlink.rubylaser.net/phmcb")

This internet where I'm at is horrible and I can't get it to download the whole thing.  I'll have to try Wednesday.

---

### Post by rubylaser on 2011-12-25
Please let me know once you've downloaded it so I can delete it.  A 400+ MB file is a decent chunk of my Dropbox space :)

---

### Post by JoeGoalie on 2011-12-26
> **rubylaser said:**
> Please let me know once you've downloaded it so I can delete it.  A 400+ MB file is a decent chunk of my Dropbox space :)

I had the bright idea to VPN into my home server and start downloading from there.  It's finished now.  Thanks.

---

### Post by JoeGoalie on 2011-12-26
Dang, I don't see any difference between installs.  Maybe it's another program I installed?  I'm definitely at a loss still.

---

### Post by rubylaser on 2011-12-26
It's hard for me to guess what the difference is, but I literally followed the steps I posted, other than forgetting to add the download for python-cheetah, and it starts right up.

---

### Post by JoeGoalie on 2012-01-01
I just started my new server install and this is the first thing I setup.  It works perfectly so far...  I wonder if it's one of the other packages I install that breaks it, or if it is just going to work now.  I guess we'll find out.

---

### Post by rubylaser on 2012-01-01
Great, glad to hear it's working for you now.  Sickbeard and Couchpotato are both very nice to have :)

---

### Post by gjlopeman on 2012-06-16
#Required -- Must Be Changed!
USER="CHANGEME" #Set Linux Mint, Ubuntu, or Debian user name here.


It is right there in the very first config file that is posted. I did the same thing just now. "USER="CHANGEME"" you need to put your use name in here for the script to run fully.

---

