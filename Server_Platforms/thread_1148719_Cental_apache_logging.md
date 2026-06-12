---
title: "Cental apache logging"
date: 2009-05-04
forum: Server Platforms
---

### Post by xkaliburx on 2009-05-04
Afternoon, rolling out our new platform using ubuntu, coldFusion8 and php and looking to see what method(s) people are using for central web logging.

Previously using CentOS I was experimenting with syslog-ng, never got it working, but as I use this new OS, I am wondering does Ubuntu have something specific or should I stick with installing/trying to configure syslog-ng?

Thanks

Lr

---

### Post by ejschaefer on 2009-05-04
Hello, 

You have a couple of options:

1. You can send your Apache logs to syslog and have a central syslog server to receive the logs

2. You could also just setup a NFS share, mount it on each web server, and change the log path to point to a folder on the mounted share. 

This might actually be the best option for you. Using a NFS share you can also centralize the various CF logs.

syslog/syslog-ng references
[http://www.cert-in.org.in/knowledgebase/guidelines/CISG-2004-03.pdf](http://www.cert-in.org.in/knowledgebase/guidelines/CISG-2004-03.pdf)

[http://www.oreillynet.com/pub/a/sysadmin/2006/10/12/httpd-syslog.html](http://www.oreillynet.com/pub/a/sysadmin/2006/10/12/httpd-syslog.html)


HOWTO: NFS Server/Client
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by xkaliburx on 2009-05-05
Thanks for the reply.  I am well aware of setting up an NFS mount, as well as using syslog, my question was more OS specific.  If I currently have syslog-ng running with a few issues and converting the other 6 webservers to Ubuntu-server, I wanted to see what people were doing.  

If I nfs mount, Ithen you are dealing with extra overhead of another mount, if the mount is down your now writing local,etc.  I really want a simple log server;
/var/logs/server1 -> domain1.com, domain2.com, /var/logs/server2/domain1.com, domain2.com


Thanks

---

