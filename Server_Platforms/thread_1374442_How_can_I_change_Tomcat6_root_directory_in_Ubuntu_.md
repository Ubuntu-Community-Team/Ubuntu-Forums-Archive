---
title: "How can I change Tomcat6 root directory in Ubuntu server 9.10 ?"
date: 2010-01-06
forum: Server Platforms
---

### Post by yu xintian on 2010-01-06
Hello,all ! I have newly installed Ubuntu server 9.10 in my server machine.And it has tomcat6 in itself.My friend have built a Java software in Fedora ,and he wants to move it to the new server.But problem is the directory structure is different between two systems.He has to either change his directory setting in his software or change the default tomcat6 ROOT directory. But I have not find any configuration file can do this job(change the tomcat default ROOT directory ).Does anybody know how to do it ? Thank you !:)

---

### Post by slakkie on 2010-01-06
You need to export the CATALINA_BASE environment variable:

export CATALINA_BASE=/path/to/webapps/dir/ 

and then start tomcat.

---

### Post by yu xintian on 2010-01-06
Thank you for you help ,slakkie ! Yes,I have changed the CATALINA_BASE
> $ echo $CATALINA_BASE
/var/lib/tomcat6/webappsBut Tomcat6 still takes /var/lib/tomcat6/webapps/ROOT/  as it default directory. How about make a symbol link between these two directories,I think it's an ugly idea  :)

---

### Post by jensse on 2011-08-09
For others with the same problem:
I believe you want to look in the file /etc/default/tomcat6 here:


# Directory for per-instance configuration files and webapps. It contains the
# directories conf, logs, webapps, work and temp. See RUNNING.txt for details.
# Default: /var/lib/tomcat6
#CATALINA_BASE=/var/lib/$NAME

---

