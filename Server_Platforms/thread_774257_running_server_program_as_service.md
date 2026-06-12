---
title: "running server program as service"
date: 2008-04-29
forum: Server Platforms
---

### Post by skrag on 2008-04-29
hi, im trying to run a (ut3) server as a service, i found this example script but it is for redhat, i was wondering what i had to change for it to run smooth in unbutu 8.04, anysuggestions would be greatly appriciated!


heres the example script 


#!/bin/bash
#
# Run-level Startup script for ut3-bin
#
# chkconfig: 345 91 19
# description: Starts and stops unreal dedicated server binary

ut3_home="/home/unreal/ut3-dedicated/Binaries/"
ut3_ownr="unreal"

# if the executables do not exist -- display error

if [ ! -f $ut3_home/startserver.sh -o ! -d $ut3_home ]
then
echo "Unreal 3 Server: cannot start"
exit 1
fi

# depending on parameter -- startup, shutdown, restart
# of the instance and listener or usage display

case "$1" in
start)
# UT3 basic start script or command can be called here. For my purposes I placed the entire command line a shell script called startserver.sh
echo -n "Starting UT3 Server: "
su - $ut3_ownr -c "cd $ut3_home && ./startserver.sh &"
touch /var/lock/subsys/unreal
echo "OK"
;;
stop)
# UT3 kill-shutdown
echo -n "Shutdown UT3 Server: "
su - $ut3_ownr -c "killall ut3-bin"
rm -f /var/lock/subsys/unreal
echo "OK"
;;
reload|restart)
$0 stop
$0 start
;;
*)
echo "Usage: $0 start|stop|restart|reload"
exit 1
esac
exit 0











this may work as-is, any comments?

---

### Post by bluefrog on 2008-04-29
try it and tell us if it works

---

### Post by larka06 on 2008-08-16
The chkconfig will not work. I think the rest of it should work fine. I stopped by looking for what Ubuntu uses instead of chkconfig.

---

