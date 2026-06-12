---
title: "Central logging on 12.04 LTS quick question"
date: 2013-03-06
forum: Server Platforms
---

### Post by xkaliburx on 2013-03-06
Morning all, today's project is to start moving all our server logs to one box.  I don't mind doing the reading, just wanted to see if there is any changes over the years.  I am looking at this thread [http://ubuntuforums.org/showthread.php?t=1349753](http://ubuntuforums.org/showthread.php?t=1349753) which is pretty straight forward, but that is regarding version 9 which is a bit outdated, so before I started playing, wanted to make sure not much has changed regarding this.

Tnx

---

### Post by koenn on 2013-03-06
yeah, that looks about right

I did something similar last summer, 
you can have a look at my notes here

[http://users.telenet.be/mydotcom/howto/linux/syslogserver.html](http://users.telenet.be/mydotcom/howto/linux/syslogserver.html)


setting up a remote logging server isn't at all difficult. Organising the (central) logs otoh might require some thought / experimenting, but the basic mechanisms are fairly straightforward.

---

### Post by xkaliburx on 2013-03-07
> **koenn said:**
> yeah, that looks about right

I did something similar last summer, 
you can have a look at my notes here

[http://users.telenet.be/mydotcom/howto/linux/syslogserver.html](http://users.telenet.be/mydotcom/howto/linux/syslogserver.html)


setting up a remote logging server isn't at all difficult. Organising the (central) logs otoh might require some thought / experimenting, but the basic mechanisms are fairly straightforward.

Thanks.   Was pretty straight forward, but have 2 other issues which I will have to do some research on.

1.  The central server is not getting the test *.* logs from the client server, but they are coming throught like this;
Mar  6 21:30:04 localhost snmpd[1181]: Connection from UDP: [127.0.0.1]:48445->[127.0.0.1]
Now that's is naturally an snmpd check, but it says localhost as opposed to the server name.  Actually I would rather them goto a different file altogether, so believe thats more the template / rule thing, but that's #1.

2.  I need other logs, such as glassfish/tomcat logs which don't use syslog, as well as apache (which I saw a how-to), but going to focus on glassfish right now.

So those are my next 2 steps.

Thanks for getting me on right path.

---

