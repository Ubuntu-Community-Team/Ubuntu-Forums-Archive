---
title: "Lucid: Starting tomcat6 on well-known ports"
date: 2010-08-04
forum: Server Platforms
---

### Post by do-U-boon-2 on 2010-08-04
Hi,

I've installed Sun Java, tomcat6 and tomcat6-admin on 10.04 server 64-bit.  By default, tomcat is configured to run as the tomcat6 user.  Everything runs just fine on tcp/8080 as initially configured.  Modifying the connector port in /etc/tomcat6/server.xml to anything below 1024 (e.g. port 80) results in:

SEVERE: Error starting endpoint
java.net.BindException: Permission denied <null>:80
...

This all begs the question... do you *really* have to run tomcat as root to bind to a well-known port?  I.e. is there really no way for tomcat to start as root, bind to a privileged port and then drop privs?

TIA!

---

### Post by arrrghhh on 2010-08-04
You seem like you know what you're doing, but I'm still going to ask the obvious question...

Are you stopping the service, making the change, and then starting the service back up?  Or at least making the change and restarting the service?

---

### Post by do-U-boon-2 on 2010-08-04
Yep, restarting tomcat following each change... I set the connector port to 1025 (worked), 1024 (worked), 1023 (failed), and of course at port 80 (failed).  The error message clearly indicates insufficient privileges to bind to the port.

For now, I'm running on tcp/8080 (which I prefer over running tomcat as root), but it would be nice to be able to run as non-root on tcp/80.

TIA!

---

### Post by arrrghhh on 2010-08-04
Hmmmmm... 

Are you running tomcat as a service (init script or otherwise), or just by hand?

I feel like I'm missing something obvious, but nothing is jumping at me yet.

---

### Post by do-U-boon-2 on 2010-08-05
Running tomcat as a service (init script).  I don't know if it was obvious, but the solution is straightforward.

A process needs superuser privilege to bind to a well-known port (<1024).  Many daemons provide for running as an unprivileged user, but typically start as root, bind, and then drop privileges, e.g. bind aka named.  An apparently recent addition to Debian/Ubuntu tomcat6 package provides for the use of authbind(1), which allows ports, addresses or UIDs to be "registered" (look under /etc/authbind for the various directories).  The tomcat6 package does this for the tomcat6 user (during package installation), but the AUTHBIND variable in /etc/default/tomcat6 *must* be set to 'yes' or this ability will not be enabled.  Mystery solved.

More details at [http://blogs.mulesoft.org/a-better-tomcat-for-ubuntu-and-debian/](http://blogs.mulesoft.org/a-better-tomcat-for-ubuntu-and-debian/)

---

### Post by arrrghhh on 2010-08-05
Excellent!

Please use the "Thread Tools" drop down to mark this topic as [SOLVED]! :D

---

### Post by peely on 2010-11-26
For anyone else tearing their hair out, by default only 0.0.0.0 is granted to the uuid of the tomcat6 user.

If you bind tomcat to a specific IP address in server.xml you will need to add this address to /etc/authbind/byuuid/{tomcat6 uuid}, one entry for each IP you listen on.

---

