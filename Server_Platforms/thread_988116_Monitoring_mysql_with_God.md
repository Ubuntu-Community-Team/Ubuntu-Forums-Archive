---
title: "Monitoring mysql with God"
date: 2008-11-20
forum: Server Platforms
---

### Post by vanderkerkoff on 2008-11-20
Here's the problem

If I add code to watch my mysql install to my god config file, and remove the normal mysql startup script from defaults, and add the god init script I've written which should boot god on reboot, which should start all the things I'm watching with god, this happens.

E [2008-11-20 12:20:10] ERROR: PID file directory '/var/run/mysqld' does not exist

I suspect that this directory is created by the mysql start script.  I've just checked that by running

sudo /etc/init.d/mysql start

Mysql starts, and the mysqld directory is created.  But that is exactly the same script I'm running in the w.start section of my god config file

w.start = "cd /etc/init.d && ./mysql start" 

Does anyone have any ideas how to get around this issue?

---

### Post by vanderkerkoff on 2008-11-20
OK, I"ve had an idea

In my god init script prior to starting god I'm creating that folder that is needed and giving it the same permissions as the folder that is created when I run the sudo /etc/init.d/mysql start command from the terminal

/bin/mkdir /var/run/mysqld
/bin/chown mysql:root /var/run/mysqld

Now on rebooting the machine I'm getting a different error in the god.log file

W [2008-11-20 13:32:39]  WARN: mysql start command exited with non-zero code = 1

The folder is being created, and it has the right permissions, but there is no PID or sock file in it.

Starting to drive me nuts :-)

---

