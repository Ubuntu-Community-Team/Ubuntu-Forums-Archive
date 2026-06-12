---
title: "Help configuring Monit to Monitor mySQLd on 14.0"
date: 2015-03-05
forum: Server Platforms
---

### Post by ravingmad on 2015-03-05
I hope someone can help me as I have pulled my hair out with this already.

I simply cannot get monit to monitor mysql on Ubuntu 14.0

Here is my section of my monit file but when monit runs it goes crazy and actually shuts down mysql after a few minutes and then I am unable to start it again without a reboot.

# check process mysql with pidfile /var/run/mysqld/mysqld.pid
# group mysql
# start program = "/etc/init.d/mysql start"
# stop program = "/etc/init.d/mysql stop"
# if failed host 127.0.0.1 port 3306 then restart
# if 5 restarts within 5 cycles then timeout

When first trying to get this to work I noticed there was no PID file for mysqld so I changed my my.cnf file to create the PID and added the appropriate permissions and it now creates a PID file.

Here is that section of my.cnf

user = mysql
socket = /var/run/mysqld/mysqld.sock
pid-file = /var/run/mysqld/mysqld.pid



Can anyone help me with this? I am stumped.

---

