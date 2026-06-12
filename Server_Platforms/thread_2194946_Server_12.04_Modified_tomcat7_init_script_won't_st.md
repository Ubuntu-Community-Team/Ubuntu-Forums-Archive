---
title: "Server 12.04: Modified tomcat7 init script won't start at boot."
date: 2013-12-21
forum: Server Platforms
---

### Post by 1clue on 2013-12-21
Hi,

I have Ubuntu Server 12.04 with tomcat7, oracle java and apache2.  I'm trying to get it PCI certified, and one CVE is not yet fixed on the distro version.

What I did is download the latest from tomcat.apache.org, set it up in /opt/tomcat7/ and modified the existing tomcat7 init script from ubuntu.  I gave the new one different ports, and modified things so (hopefully) I can use the same init script on multiple tomcats later.

The service starts fine manually (service 8081 start) but when I reboot the 8081 service does not start.

Here's the diff on the init script:
```
diff tomcat7 8081
27c27
< NAME=tomcat7
---
> NAME=`echo "$0" | sed 's/\/etc\/init.d\///'`
92c92
< CATALINA_HOME=/usr/share/$NAME
---
> CATALINA_HOME=/opt/tomcat7/$NAME
95c95
< CATALINA_BASE=/var/lib/$NAME
---
> CATALINA_BASE=$CATALINA_HOME

```

Here's my /etc/rc.d config:
```
ls /etc/rc?.d/ | egrep -i '(8081|tomcat)' | sort
K078081
K078081
K078081
K08tomcat7
K08tomcat7
K08tomcat7
K08tomcat7
K08tomcat7
K08tomcat7
K08tomcat7
S938081
S938081
S938081
S938081

```

As you can see, I put the 8081 service right next to the stock tomcat7.

Does anyone have any idea why this isn't working?

Thanks.

---

### Post by 1clue on 2013-12-21
Found the answer.  This line works in bash, but not sh:
```
NAME=`echo "$0" | sed 's/\/etc\/init.d\///'`
```

---

