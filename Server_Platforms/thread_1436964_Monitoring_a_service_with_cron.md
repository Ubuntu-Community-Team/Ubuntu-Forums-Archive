---
title: "Monitoring a service with cron"
date: 2010-03-23
forum: Server Platforms
---

### Post by malarie on 2010-03-23
Good day,

I have  webserver (jboss) running on my server,  I would like to monitor this service every 5 mins,  if it goes down, i wanna know right away.  I am familiar with the cron syntax, but im  not sure how i can monitor a  service/PID or a process name..

Example:
I want to monitor this process and restart it if it goes down:
#ps -ef | grep -i jboss



root      3817  3778  3 10:33 pts/0    00:01:43 java -Dprogram.name=run.sh -Xms128m -Xmx512m -Dsun.rmi.dgc.client.gcInterval=3600000 -Dsun.rmi.dgc.server.gcInterval=3600000 -XX:MaxPermSize=256m -Dfile.encoding=UTF-8 -Djava.net.preferIPv4Stack=true -Djava.endorsed.dirs=/var/www/nuxeo/nuxeo-5.3/lib/endorsed -classpath /var/www/nuxeo/nuxeo-5.3/bin/run.jar org.jboss.Main -b 0.0.0.0

Any help is welcome.

---

### Post by malarie on 2010-03-23
I found this script:

#!/bin/bash
PROCESS=smb
if ps aux | grep "$PROCESS" | grep -v grep >/dev/null ; then
        echo Process $PROCESS is running
else
        echo Process $PROCESS is stopped  Restarting it ...
        /etc/rc.d/init.d/smb start >/dev/null
fi



source: [http://www.nongnu.org/lpi-manuals/lpi-201/html/ch07s05.html](http://www.nongnu.org/lpi-manuals/lpi-201/html/ch07s05.html)

---

### Post by KB1JWQ on 2010-03-23
Heh, this is what Nagios was built for.

If you don't want a full Nagios install, you can install the plugins and call the check_process plugin from cron.  

Don't reinvent the wheel if you don't have to. :-)

---

### Post by kelt65 on 2010-03-23
Look into the [FONT="Courier New"]ps-watcher[/FONT] program; you could probably just incorporate it in your jboss startup script. Nagios is a total bear and overkill just for this.

---

### Post by yota on 2010-03-23
let me introduce my most faithful employee: [monit]("http://mmonit.com/monit/")

It kindly monitors all the daemons that I told him to (by pid, port or anything else) and recovers them if something went wrong.
Not to mention that I get an email for each event if I like, and that I can double check the status through a web page when I'm off-site.

It's in the repo, it asks 0 wage... you have to hire him!

Hope this helps!

---

### Post by malarie on 2010-03-23
thanks for the replies.  Those programs are coomand line only?  I do not have any GUI on my server.  Thanks.

---

