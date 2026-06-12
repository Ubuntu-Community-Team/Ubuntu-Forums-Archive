---
title: "Bug in Nagios systemd start script."
date: 2024-05-09
forum: Ubuntu Development Version
---

### Post by mmirek on 2024-05-09
Ubuntu 20.04. and  previos version (Nagios 4 nad 3)

There is a bug in the "restart" function in the /etc/init.d/nagios4 systemd script that causes the restart to fail.

if [ -z "$?" -o "$?" = "0" ] - second use -o "$?" should check the stop function, but check the result -z "$?"
To resolve this issue, perform the following modification.

@@ -223,11 +223,13 @@
   ;;
   restart)
     log_daemon_msg "Restarting $DESC" "$NAME"
-    stop
-    if [ -z "$?" -o "$?" = "0" ]; then
+ stop
+    STOP_STATUS=$?
+    if [ "$STOP_STATUS" -eq 0 ]; then
       start
+      START_STATUS=$?
     fi
-    log_end_msg $?
+    log_end_msg $START_STATUS
   ;;
   reload|force-reload)
     log_daemon_msg "Reloading $DESC configuration files" "$NAME"

(I don't know if this thread is the right place :) )

---

