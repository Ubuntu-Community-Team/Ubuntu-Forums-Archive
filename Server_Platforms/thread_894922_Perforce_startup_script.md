---
title: "Perforce startup script"
date: 2008-08-19
forum: Server Platforms
---

### Post by eirland on 2008-08-19
Hey guys,
I've just installed the latest version of Ubuntu Server and am trying to get a perforce server running on it.

Here's the script I'm using:

```
#!/bi/nsh -e
rt P4JOURNAL=/var/log/perforce/journal
export P4LOG=/var/log/perforce/p4err
export P4ROOT=/home/perforce
export P4PORT=1666

PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"

. /lib/lsb/init-functions

p4start="p4d -d"
p4stop="p4 admin stop"
p4user=perforce

case "$1" in
start)
log_action_begin_msg "Script: Starting Perforce Server..."
daemon -u $p4user $p4start;
;;

stop)
log_action_begin_msg "Script: Stopping Perforce Server..."
daemon -u $p4user $p4stop;
;;

restart)
stop
start
;;

*)
 echo "Usage: /etc/init.d/perforce (start|stop|restart)"
 exit 1
 ;;

esac

exit 0
```

It appears that running "./perforce start" works correctly.  However, running "./perforce stop" doesn't seem to actually shut down the perforce server.

Anyone have any suggestions?
Thanks!

---

### Post by misiu_mp on 2008-12-02
Mybe thats not of much help, but did you test the command "p4 admin stop" maually? This way you could narrow the casue or error a little bit.

---

### Post by jsack777 on 2009-08-29
Does user 'perforce' have admin rights?  Double check your p4 protections.

---

### Post by TimeDoctor on 2009-09-21
Perforce won't shut down if it doesn't have the $P4PASSWD and a $P4USER set, you can do these things in the command line along with the shutdown, in a ~/.p4config, or in the environment variables.

---

