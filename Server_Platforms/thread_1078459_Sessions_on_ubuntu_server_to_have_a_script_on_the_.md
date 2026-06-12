---
title: "Sessions on ubuntu server to have a script on the start up"
date: 2009-02-23
forum: Server Platforms
---

### Post by any.linux12 on 2009-02-23
Hi!

I need to put a script that I wrote in the start up, such that, if I have to restart the server it will execute the script alone.

I know that in desktop versions is in system -> preferences -> sessions, but in ubuntu server I have no idea

---

### Post by lykwydchykyn on 2009-02-23
Typically you'd put it in /etc/rc.local.  Does it need to run as root or a specific user?

---

### Post by TurboRush on 2009-02-23
Do the following...

```
sudo cp /script/location/script_name /etc/init.d
sudo update-rc.d script_name defaults
```

Please note, this assumes its ok for the script to be run as root and using default run levels. Additionally, this script will get called on start up and shutdown so you may want to look at some basic examples of how to incorporate logic (if you haven't already), e.g.,

```

# MediaTomb auto-start
#
# description: Auto-starts MediaTomb
# processname: mediatomb

case $1 in
start)
       echo Starting MediaTomb
       mediatomb -i192.168.1.100 -d
       ;;
stop)
        echo Stopping MediaTomb... doing nothing.

       ;;
restart)
        echo Restarting MediaTomb
        mediatomb -i192.168.1.100 -d
       ;;
esac
exit 0

```

---

