---
title: "Ventrilo on boot (or anything for that matter"
date: 2010-06-22
forum: Server Platforms
---

### Post by darkenvy6 on 2010-06-22
Its driving me crazy! I have scoured the internet!!!

this is my file in /init.d/ directory:
**[COLOR=blue][FONT=Times New Roman]#!/bin/bash[/FONT][/COLOR]**
**[COLOR=blue][FONT=Times New Roman]# chkconfig: 235 19  08[/FONT][/COLOR]**
**[COLOR=blue][FONT=Times New Roman]# description:  Starting the Ventrilo Server[/FONT][/COLOR]**
**[COLOR=blue][FONT=Times New Roman]# This server will  run as root[/FONT][/COLOR]**
**[COLOR=blue][FONT=Times New Roman]#[/FONT][/COLOR]**
**[COLOR=blue][FONT=Times New Roman]# Variables are  better than hard-coded values.[/FONT][/COLOR]**
**[COLOR=blue][FONT=Times New Roman]VENT_DIR=/etc/init.d[/FONT][/COLOR]**
**[COLOR=blue][FONT=Times New Roman]cd $VENT_DIR[/FONT][/COLOR]**
**[COLOR=blue][FONT=Times New Roman]./ventrilo_srv –d[/FONT][/COLOR]**
**[COLOR=blue][FONT=Times New Roman]echo “The Ventrillo  Server has started…”[/FONT][/COLOR]**
[B][COLOR=blue][FONT=Times New Roman]exit

[/FONT][/COLOR][/B]Yes me typing "/etc/init.d/ventrilo_start start" DOES start the server and my permissions are set to 666 (both by "chmod 777" and "chown root:root"). Why won't this server start on boot?! I think it might be this upstart thing but wow can I not find anything documented on upstart. Can we just toggle the old way of using runlevels? why switch? Sorry if I seem all over the place but I just can't figure it out. Thanks in advance! Also note I have no GUI installed and this is ubuntu server 10.04 ^^

~RM

---

### Post by Nolam on 2010-06-22
I'll try to scratch your back if you scratch mine.

I have Ubuntu Server, and I installed Ventrilo Server onto it, but IDK how to start up the server!!! Help me PLEASE D:

---

### Post by darkenvy6 on 2010-06-29
Sorry for the late reply but yes the above post (my initial thread starter) IS the working solution! a simple PS AUX will show you the server is running but takes about 30-60 seconds for a client to be able to connect. I guess it has a little slow startup process. Okay if you can't get it working I'll help you out a bit more in detail. Chow :)

---

### Post by littlegreiger on 2010-06-30
Did you move your ventrilo server files to the init.d directory? 
Generally that isn't a very good idea. You should consider moving the ventrilo files somewhere else and then you should be able to use the init script that I'm using
```
#!/bin/sh

VENT_DIR="/home/ventrilo/ventsrv/"
USER="ventrilo"
VENT_BIN="ventrilo_srv"

. /lib/lsb/init-functions
case "$1" in

start)
log_begin_msg "Starting Ventrilo server..."
su $USER -c "$VENT_DIR/$VENT_BIN -f$VENT_DIR/$VENT_BIN -d" || log_end_msg 1
log_end_msg 0
;;

stop)
log_begin_msg "Stopping Ventrilo server..."
killall ventrilo_srv || log_end_msg 1
log_end_msg 0
;;
*)
log_success_msg "Usage: /etc/init.d/ventrilo {start|stop}"
exit 1
esac
exit 0

```

You only need to modify the path to the ventrilo files and change the user to whoever you want to run the server under.

I can't tell you how long it takes from boot for clients to be able to connect but it shouldn't be too long once networking starts.

---

### Post by darkenvy6 on 2010-07-02
sorry for the late reply, Ventrillo is isntalled at /usr/reno/installed/ventrillo/ventrillo_srv or something very similar. I start Ventrilo via a command I put into /etc/init.d witch is sudo /etc/init.d/ventrilo_start start and that seems to work now. Thanks for your help guys!

---

