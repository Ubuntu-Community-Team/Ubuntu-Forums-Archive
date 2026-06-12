---
title: "syslog stops writing in log"
date: 2010-09-12
forum: Security
---

### Post by doru001 on 2010-09-12
syslog stops writing immediately after log rotation, after I start the  system (but not after reboot), and at some other times, into my fast cgi  application's log. It starts working after /etc/init.d/sysklogd restart.  Please give me any hint.
 
**[SIZE=2]Configuration: [/SIZE]**   

I am using Ubuntu 8.04 lts server, Apache web server. 

My (fast cgi) application uses: 
```

#include <syslog.h> 
syslog(LOG_LOCAL6|LOG_INFO, "new n= %d;\n", count); 
```to log some activity messages. 
At the end of /etc/syslog.conf I added:  
```

local6.=info -/var/log/apache2/myapp.log
```In /etc/syslog.conf I added to each selector which contained "myapp.log":  
```

;local6.!=info
```like this: ```

*.*;auth,authpriv.none;local6.!=info            -/var/log/syslog
```and:  
```

*.=info;*.=notice;*.=warn;\
         auth,authpriv.none;\
         cron,daemon.none;\
         mail,news.none;local6.!=info            -/var/log/messages 
```

---

### Post by doru001 on 2010-09-16
It seems that syslog ceases to function when syslogd is restarted automatically.  This happens when I start or reboot the computer and when logs are rotated. After I: 
```

/etc/init.d/sysklogd restart
```it all goes well. This is true for my fcgi  application only, other system pre-configured logs work fine. 

fflush(NULL); and closelog(); do not seem to make any difference. 

I was amazed today to discover that: 
```

wget localhost/myapp.fcgi?some%20data
```issued locally as root is logged well after I started the system, but access requests from other locations were not logged unless I did /etc/init.d/sysklogd restart. 

And this is also a BUMP. 

Doru

---

### Post by doru001 on 2010-09-17
I continue this low quality soap opera here: 
[http://www.linuxquestions.org/questions/linux-server-73/syslog-stops-writing-in-log-831833/](http://www.linuxquestions.org/questions/linux-server-73/syslog-stops-writing-in-log-831833/)

Doru

---

