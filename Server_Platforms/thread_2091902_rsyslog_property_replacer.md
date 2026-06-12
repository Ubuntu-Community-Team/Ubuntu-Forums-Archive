---
title: "rsyslog property replacer"
date: 2012-12-06
forum: Server Platforms
---

### Post by kdzida on 2012-12-06
Hello
 

 I' am trying to configure a simple network rsyslog server. The problem is that rsyslog refuses to use property replacer. I managed to configure a working network rsyslog server which redirects all rsyslog traffic to /tmp/sth-all.log with new (custom) config file for network traffic - /etc/rsyslog.d/40-remote.conf
 

 ```

 root@XXXX:~# cat /etc/rsyslog.d/40-remote.conf  
 

 *.* /tmp/sth-all.log  
 

 root@XXXX:~#service rsyslog restart
 & ~  
 

 
``` The rsyslog works flawlessly. The trouble starts when I try to separate the log between days:
 

 ```

 root@XXXX:~# cat /etc/rsyslog.d/40-remote.conf  
 

 *.* "/tmp/sth-%$NOW%.log"
 & ~  
 

 root@XXXX:~#service rsyslog restart
 
``` or hosts:
 

 ```

 root@XXXX:~# cat /etc/rsyslog.d/40-remote.conf  
 

 *.* "/tmp/sth-%HOSTNAME%.log"
 & ~  
 

 root@XXXX:~#service rsyslog restart
 
``` Non of them works, no files are made, logs go to nowhere. Can you help me?

---

### Post by koenn on 2012-12-06
Judging by the examples you give, it's not property replacer you're talking about, its dynamic files.

You need tu define a template in order to do that sort of logging


there's an example in the OP of this thread 
[http://ubuntuforums.org/showthread.php?t=2091573](http://ubuntuforums.org/showthread.php?t=2091573)

or here
[http://www.rsyslog.com/doc/rsyslog_conf_actions.html](http://www.rsyslog.com/doc/rsyslog_conf_actions.html)
and 
[http://wiki.rsyslog.com/index.php/Log_Router_syslog_with_Dynamic_File_Names](http://wiki.rsyslog.com/index.php/Log_Router_syslog_with_Dynamic_File_Names)

---

### Post by kdzida on 2012-12-10
Actually I tried templates already but with no luck. Strangely the template shown by M[ainemojo]("http://ubuntuforums.org/member.php?u=1762752") worked for me! It will need some tweaking, but I take it from here. Thanks !

---

