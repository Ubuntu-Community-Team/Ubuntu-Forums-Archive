---
title: "startup script won't start at bootup"
date: 2010-12-06
forum: Server Platforms
---

### Post by senor_smile on 2010-12-06
I have a little script that pings 4.2.2.2 and increments a counter every 60 seconds.  If the internet is down >= 10 minutes, a reboot command is issued to the system.  The script works perfectly.  I put my script in /usr/sbin.  I can run it manually and see that it works.  I created an entry in /etc/init.d to start the script at startup.  I initialized it with update-rc.d wanwatchdogstart defaults.  I can see its entries under /etc/rc*.d.  However, the script doesn't appear to be running at all.  I have some echo's in the script as a test.  In other scripts these will appear in tty7.

Any ideas what would cause a startup script to just not run?

---

### Post by alienprdkt on 2010-12-06
Try this name your file starting with K99 and save it to /etc/rc0.d

don't know why but it worked for me...

and just a question why have it reboot instead of restarting your network service?

/etc/init.d/networking restart

---

### Post by matt_symes on 2010-12-06
Hi

The usual technique is to put the actual script itself into /etc/init.d and use update-rc.d to create links to the actual script and not any references to it.

Also, the scripts are run by root and, consequently,  don't have your user environment. So use full paths and set up things like displays.

Kind regards

---

### Post by brettg on 2010-12-07
Quick and simple answer is to put your script in /etc/rc.local

---

### Post by matt_symes on 2010-12-07
Hi

..or have it as a cron job and let that handle calling the script every 60 seconds :) You've got to love Linux. ;)

This will still apply though...

> Also, the scripts are run by root and, consequently,  don't have your user environment.

Kind regards

---

### Post by senor_smile on 2010-12-07
> **alienprdkt said:**
> Try this name your file starting with K99 and save it to /etc/rc0.d

don't know why but it worked for me...

and just a question why have it reboot instead of restarting your network service?

/etc/init.d/networking restart

Thanks for all of the suggestions thus far.  Firstly, this is a mini itx computer running shorewall as a router with a Verizon aircard as its WAN interface.  The problem that I've run into is that since they started rolling out the LTE network changes, all of the modems have started sporadically getting stuck in a state where they "think" they are connected, yet I can't get to their static I.P.'s and they can't get out to anyone on the internet.  The only way to fix this is to power cycle the aircard, which is most easily done by rebooting the machine. 

I tried renaming the rc2.d folder's symlink to my starter script and it has booted now.  Before it begin with S20, I believe.  Anyway, I will test that it's actually doing what it was designed to do and post back with all of my scripts for reference. 

Also, I decided to break the scripts out into two different places so that I could call the script manually if I wanted to, but it could also be started from within the init.d scripts.  So, my /etc/init.d/wanwatchdogstart follows the basic debian startup script rules(I think anyway) and can be called to startup, shutdown etc.  All of the actual coding and changes then are in my real script, /usr/sbin/wanwatchdog .

---

### Post by senor_smile on 2010-12-07
I have determined that my /etc/init.d/wanwatchdogstart script runs if another script I have is stopped.  This script, which I call usbmodemstart, automatically starts and manages the aircard using wvdial.  

Let me start from the beginning.  I have a script at /etc/init.d/usbmodemstart 

```
#! /bin/sh

APP_PATH=/usr/sbin/monusbmodem

# script name
NAME=usbmodemstart

# app name
DESC=usb modem startup script

#exit automatically if some variable isn't set
set -e


case "$1" in
  start)
        echo -n "Starting $DESC: "
        /usr/sbin/monusbmodem
	;;

  stop)
        echo -n "Stopping $DESC: "
        start-stop-daemon --stop --name sh monusbmodem
	;;

  restart|force-reload)
        echo -n "Restarting $DESC: "
	start-stop-daemon --stop --name sh monusmodem
	sleep 5
        /usr/sbin/monusbmodem
        ;;
  *)
        N=/etc/init.d/$NAME
        echo "Usage: $N {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

exit 0
```

I put this script as a startup item by running: 

```
sudo update-rc.d usbmodemstart defaults
```

That script calls the program /usr/sbin/monusbmodem

```
while [ 1 ] 
sleep 5
do
	running=`ps -C wvdial | grep wvdial`
	if [ -z $running ]; then
		echo "wvdial NOT working"
		sleep 30
		running2=`ps -C  wvdial | grep wvdial`
		if [ -z $running2 ]; then
			echo "starting wvdial now"
			killall wvdial
			/usr/sbin/usbmodem
		fi

	else 
		echo "wvdial working"
	fi

done
```

Which monitors for the wvdial process.  If it is running then it waits 5 seconds and runs again.  If it is not, it waits another 30 seconds and if it's still not running it kills any instances of wvdial just to be sure, and then starts the usbmodem script

```
eject /dev/sr0
wvdial &
sleep 10
route del default
route add default dev ppp0
shorewall start
```

This script ejects the aircards mountable disk if applicable, runs wvdial, and sets up the firewall so that everyone can access the internet through this machine.  These scripts have been doing their job for months without any real problems.  That is, until our aircards suddenly started getting into a state where they think they're connected, but no real WAN connectivity exists.  

When I stop the usbmodemstart, my wanwatchdog scripts starts.  I do notice that the monusbmodem and usbmodem scripts are still active in the processes.  Something is wrong, I'm just not sure what.

---

