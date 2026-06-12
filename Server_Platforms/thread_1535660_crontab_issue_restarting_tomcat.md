---
title: "crontab issue restarting tomcat"
date: 2010-07-21
forum: Server Platforms
---

### Post by eradan on 2010-07-21
Hello,

I have this script:


```
$ cat /usr/local/bin/tomcat5.5 
#!/bin/bash

/usr/sbin/service tomcat5.5 stop

sleep 20

tomcat_PID=`ps -ef | grep java | grep -v grep | awk '{print $2}'`
if [ -n "$tomcat_PID" ]
then
  kill -n 9 $tomcat_PID
  sleep 2
fi

/usr/sbin/service tomcat5.5 start

```

it works fine but when I add it to my /etc/crontab this line:


```
45 11    * * *   root    /usr/local/bin/tomcat5.5  > /dev/null

```

something strange happens: the script runs fine but when it ends the process become zombie:

```

$ ps axf
 ...
 5630 ?        Ss     0:00 /usr/sbin/cron
32340 ?        S      0:00  \_ /USR/SBIN/CRON
32341 ?        Zs     0:00      \_ [sh] <defunct>

```

I can't understand why...
Any ideas?

Cheers, 
Ivan

---

### Post by sfr on 2010-07-21
Is there any additional information in the log files?

also, you might want to redirect all output to /dev/null, not only standard out

```
45 11    * * *   root    /usr/local/bin/tomcat5.5  2>&1 > /dev/null
```

---

### Post by eradan on 2010-07-22
Hello sfr,

thanks for your reply. My syslog seems ok to me:

```
Jul 22 09:00:22 ambrogio -- MARK --
Jul 22 09:09:01 ambrogio /usr/sbin/cron[5630]: (*system*) RELOAD (/etc/crontab)
Jul 22 09:09:01 ambrogio /USR/SBIN/CRON[9357]: (root) CMD (   /usr/local/bin/tomcat5.5  2>&1 > /dev/null)
Jul 22 09:09:01 ambrogio /USR/SBIN/CRON[9358]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jul 22 09:09:01 ambrogio jsvc.exec[7818]: 22-lug-2010 9.09.01 org.apache.coyote.http11.Http11BaseProtocol pause INFO: Pausing Coyote HTTP/1.1 on http-8180 
...
Jul 22 09:09:30 ambrogio jsvc.exec[9462]: 22-lug-2010 9.09.30 org.springframework.web.servlet.FrameworkServlet initServletBean INFO: FrameworkServlet 'compass': initialization completed in 734 ms 
Jul 22 09:09:30 ambrogio jsvc.exec[9462]: 22-lug-2010 9.09.30 org.apache.coyote.http11.Http11BaseProtocol start INFO: Starting Coyote HTTP/1.1 on http-8180 
Jul 22 09:09:30 ambrogio jsvc.exec[9462]: 22-lug-2010 9.09.30 org.apache.jk.common.ChannelSocket init INFO: JK: ajp13 listening on /0.0.0.0:8009 
Jul 22 09:09:30 ambrogio jsvc.exec[9462]: 22-lug-2010 9.09.30 org.apache.jk.server.JkMain start INFO: Jk running ID=0 time=0/18  config=null 
Jul 22 09:09:30 ambrogio jsvc.exec[9462]: 22-lug-2010 9.09.30 org.apache.catalina.storeconfig.StoreLoader load INFO: Find registry server-registry.xml at classpath resource 
Jul 22 09:09:30 ambrogio jsvc.exec[9462]: 22-lug-2010 9.09.30 org.apache.catalina.startup.Catalina start INFO: Server startup in 2703 ms 

```

As a matter of fact Tomcat is always restarted without any problems but the issue is on the script exiting: it hangs on exit. For this very reason I removed it from the cron.daily directory because it avoided any following script.

Anyway I'd like to understand what hangs it... :confused:

Thanks, :)
Ivan

---

### Post by sfr on 2010-07-22
The issue seems to be a confused one as far as i could find. This[ Stackoverflow discussion]("http://stackoverflow.com/questions/1506902/why-do-processes-spawned-by-cron-end-up-defunct")
is suggesting to use exec to separate the processes while [this]("http://unix.derkeiler.com/Mailing-Lists/FreeBSD/stable/2005-01/0514.html") post (albeit about freebsd) suggests redirecting the subprocesses output in the bin and putting them in the background so they don't keep crond waiting.

---

