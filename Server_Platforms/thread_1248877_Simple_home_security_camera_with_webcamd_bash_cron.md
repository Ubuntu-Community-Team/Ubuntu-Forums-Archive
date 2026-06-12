---
title: "Simple home security camera with webcamd bash cron"
date: 2009-08-24
forum: Server Platforms
---

### Post by akhilles on 2009-08-24
**Background**: I was looking for a security camera solution for Ubuntu server, and tried out a few applications. However, they are either too simple or too complicated. webcamd is the one I'm using and it just captures an image from a web cam to a file every 30 seconds. However, I need to store multiple images in order for them to be useful. And have them deleted after a period of time. So I came up with a bash script & cron job.

**Module/driver**: Plug a Logitech USB webcam in your server, install the module/driver.

```
sudo apt-get install gspca-source
```

Load the module.

```
sudo modprobe gspca_main
```

**webcamd**: Install the daemon.

```
sudo apt-get install webcamd
```

Then create a simple startup script.

```
sudo vi /etc/init.d/webcamd
```

```
#!/bin/sh

SERVERBIN=webcamd

start() {
$SERVERBIN start > /dev/null 2>&1
}

stop() {
$SERVERBIN stop > /dev/null 2>&1
}

restart() {
$SERVERBIN restart > /dev/null 2>&1
}

case "$1" in
start)
start
;;
stop)
stop
;;
restart)
restart
;;
*)
echo "Usage: $0 {start|stop|restart}"
esac

exit 0
```

Make it executable.

```
sudo chmod +x /etc/init.d/webcamd
```

And turn it into autostart.

```
sudo update-rc.d webcamd defaults
```

And start it up without restarting server.

```
sudo /etc/init.d/webcamd start
```

Set up the save directory under the home of your currently logged in user. ~/.webcamd

```
webcamd-setup
```

**bash**: Write a script for backing up the one & only captured image to a file with date & time as filename elsewhere. Replace /home/akhilles/ & /Volume_1/captures (should be public or on Samba) with your directories.

```
sudo vi /usr/bin/savecaptures.sh
```

```
#!/bin/sh
INPUTDIR=[COLOR="Red"]/home/akhilles/[/COLOR].webcamd
OUTPUTDIR=[COLOR="Red"]/Volume_1/captures[/COLOR]
FILE=$INPUTDIR/pre-webcam.jpg

if [ -f $FILE ]; then
  mv "$FILE" $OUTPUTDIR/`date '+%m-%d-%Y_%I.%M.%S%p'`.jpg
fi

exit 0
```

**cron**: Finally, add 2 cron jobs for running the script & deleting the images at 00:00 AM every day. If you don't delete the images, they'll fill up your server. Each image is about 6KB.  1 per minute. A day's worth of images is about 9GB. You may want to adjust the schedules to suit your needs.

```
sudo crontab -e
```

```
# m h  dom mon dow   command
* * * * * /usr/bin/savecaptures.sh > /dev/null 2>&1
0 0 * * * rm -f /Volume_1/captures/* > /dev/null 2>&1
```

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

**Notes**: > /dev/null 2>&1 can be omitted from all of the above, but output/error messages may fill up your terminal. You can fine-tune the scripts to store the messages to /var/log. Also, I'm not gonna spend hours complicating the scripts. These are the basics that should get the job done.

---

### Post by HermanAB on 2009-08-24
Uhmm, 'motion' would likely be better, since it only uploads a pic when something changed.

---

