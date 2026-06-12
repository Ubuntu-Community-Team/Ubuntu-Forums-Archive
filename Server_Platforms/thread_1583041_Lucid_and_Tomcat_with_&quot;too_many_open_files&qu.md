---
title: "Lucid and Tomcat with &quot;too many open files&quot;"
date: 2010-09-27
forum: Server Platforms
---

### Post by brettermeier01 on 2010-09-27
Hi all,

our tomcat is running into problem while open files (connections)

the catalina.out logs "too many open files" after some minutes with high traffic load on the application.

a look with "lsof | grep tomcat6 | wc -l" shows "only" 1040 to 1080 open files with tomcat6

I have configured the parameters in "/etc/security/limits.conf":

```

 56 tomcat6 soft    nofile  400000
 57 tomcat6 hard    nofile  500000
 58
 59 *       soft    nofile  49152
 60 *       hard    nofile  65535

```as well as the "/etc/pam.d/common-session(-noninteractive)":

 ```
15 session required pam_limits.so
```An "ulimit -Ha shows for the user "tomcat6":

```

core file size          (blocks, -c) unlimited
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 20
file size               (blocks, -f) unlimited
pending signals                 (-i) 16382
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 500000
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) unlimited
cpu time               (seconds, -t) unlimited
max user processes              (-u) unlimited
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

```I dont have an idea, where the limit is set. Is there a limit in the ubuntu tomcat?

some additional infos:

```

dpkg -l | grep tomcat6
ii  libtomcat6-java                  6.0.24-2ubuntu1.2                 Servlet and JSP engine -- core libraries
ii  tomcat6                          6.0.24-2ubuntu1.2                 Servlet and JSP engine
ii  tomcat6-admin                    6.0.24-2ubuntu1.2                 Servlet and JSP engine -- admin web applicat
ii  tomcat6-common                   6.0.24-2ubuntu1.2                 Servlet and JSP engine -- common files
ii  tomcat6-docs                     6.0.24-2ubuntu1.2                 Servlet and JSP engine -- documentation
ii  tomcat6-examples                 6.0.24-2ubuntu1.2                 Servlet and JSP engine -- example web applic

``````

 uname -a
Linux web2 2.6.32-24-server #39-Ubuntu SMP Wed Jul 28 06:21:40 UTC 2010 x86_64 GNU/Linux

```Thanks 
Christian

---

### Post by BOK on 2010-12-20
Any news on this, since we have the same issue..?
Tomcat6 is ignoring the entries in limits.conf (set to 4096 for all users):


```

 ps wwwaux | grep tomcat6
tomcat6  **[COLOR="Red"]16258[/COLOR]** 35.8 22.2 5191168 1823964 ?     Sl   10:39 216:31 /usr/lib/jvm/java-6-sun/bin/java -Djava.util.logging.config.file=/var/lib/tomcat6/conf/logging.properties -Djava.awt.headless=true -Xms256M -Xmx4096M -XX:MaxPermSize=256M -XX:+UseConcMarkSweepGC -XX:+CMSIncrementalMode -DjvmRoute=xy2 -Djava.io.tmpdir=/var/tmp -Drepo.upgrade=false -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Xms256M -Xmx4096M -XX:MaxPermSize=256M -Djava.endorsed.dirs=/usr/share/tomcat6/endorsed -classpath /usr/share/tomcat6/bin/bootstrap.jar -Dcatalina.base=/var/lib/tomcat6 -Dcatalina.home=/usr/share/tomcat6 -Djava.io.tmpdir=/var/tmp/tomcat6-temp org.apache.catalina.startup.Bootstrap start

# cat /proc/**[COLOR="Red"]16258[/COLOR]**/limits 
Limit                     Soft Limit           Hard Limit           Units     
Max cpu time              unlimited            unlimited            seconds   
Max file size             unlimited            unlimited            bytes     
Max data size             unlimited            unlimited            bytes     
Max stack size            8388608              unlimited            bytes     
Max core file size        0                    unlimited            bytes     
Max resident set          unlimited            unlimited            bytes     
Max processes             unlimited            unlimited            processes 
**[COLOR="Red"]Max open files            1024                 1024                 files[/COLOR]**     
Max locked memory         65536                65536                bytes     
Max address space         unlimited            unlimited            bytes     
Max file locks            unlimited            unlimited            locks     
Max pending signals       16382                16382                signals   
Max msgqueue size         819200               819200               bytes     
Max nice priority         20                   20                   
Max realtime priority     0                    0                    
Max realtime timeout      unlimited            unlimited            us

```

Seems that Gentoo is suffering from the same "bug":
[http://forums.gentoo.org/viewtopic-t-821751-start-0.html](http://forums.gentoo.org/viewtopic-t-821751-start-0.html)

---

### Post by BOK on 2010-12-27
The above issue is all "start-stop-daemon" related...
There seems to be a patch waiting for at least 5 years now:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=302079](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=302079)

In "the meantime" a workaround / hack for us was to add these lines in /etc/init.d/tomcat6:

[FONT="Courier New"]ulimit -Hn 16384
ulimit -Sn 16384[/FONT]

---

