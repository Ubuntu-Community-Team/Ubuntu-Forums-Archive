---
title: "HOWTO:Configure synaptic installed tomcat to work with netbeans"
date: 2009-09-01
forum: Server Platforms
---

### Post by shivain22 on 2009-09-01
Very simple

create a file named anything.sh and keep it in the /usr/share/tomcat<your version >/bin

paste this code there
#!/bin/sh
if [ -s /var/run/tomcat6.pid ]
then
gksudo /etc/init.d/tomcat6 stop
else
gksudo /etc/init.d/tomcat6 start
fi


and point your netbean to start tomcat with anything.sh
thats it
you are done

bingo!!!!!!!!!!!!!!!!1

---

