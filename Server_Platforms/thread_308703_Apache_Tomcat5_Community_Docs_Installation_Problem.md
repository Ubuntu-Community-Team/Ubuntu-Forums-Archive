---
title: "Apache Tomcat5 Community Docs Installation Problem - cannot change port"
date: 2006-11-28
forum: Server Platforms
---

### Post by Jere Retzer on 2006-11-28
I'm installing Apache Tomcat5 on Edgy per the instructions at [https://help.ubuntu.com/community/ApacheTomcat5](https://help.ubuntu.com/community/ApacheTomcat5) - which work great except that I can't seem to change the port from 8180 to 80 by editing the /etc/tomcat5/server.xml file. When I do this and start or restart using etc/init.d/tomcat5 the I do not find the server working on either port. If I restore the server.xml to port 80 and restart it is fine. What is the problem here? Thanks!

I've found, btw for those puzzling about environment variables for JAVA_HOME and CATALINA_HOME that placing these in the etc/environment file seems to work well

---

### Post by Jere Retzer on 2006-11-28
I should have said when I restore the port to 8180 in server.xml it works fine but not when I change it to 80. I can start and stop using the init.d/tomcat5 file and it also starts when the server is started. Thanks

---

### Post by cypherphreak on 2006-11-28
you are trying to get tomkat to opperate on the same port as your webserver? This will not work hence the problem you are having. You need to keep your ports seperate for seperate processes.

---

### Post by Jere Retzer on 2006-11-28
No. There is no other web server installed. I want to run Tomcat as a standalone server - so there is no conflict.

---

### Post by Jere Retzer on 2006-11-28
Reviewing the log I find that it is a port conflict. I suspect the problem may be that Apache was installed but is no longer and ubuntu is allocating port 80. How can I get it freed up? Thanks

---

### Post by JimTDI on 2006-11-29
> **Jere Retzer said:**
> No. There is no other web server installed. I want to run Tomcat as a standalone server - so there is no conflict.

First - thanks for this "gem" you posted

"I've found, btw for those puzzling about environment variables for JAVA_HOME and CATALINA_HOME that placing these in the etc/environment file seems to work well".

Outstanding info!  Helped me alot!!

What log do you see the conflict in, and what is the logged error.  I thought there was something about lower port numbers being protected - maybe FireStarter would show you if port 80 is being blocked??

---

### Post by Jere Retzer on 2006-11-30
The log showing the conflict was /var/log/tomcat5

I've stopped and removed Apache2 in various ways but tomcat5 still does not want to use port 80. I tried it in fact on a clean install of a desktop that never had apache installed and tomcat still did not want to run on port 80 (but was happy on 8180) although the conflict stopped showing up in the log

A note of caution on using /etc/environment for java and catalina variables you could have a problem if you have programs that use different java versions or if you have more than one tomcat running (if you specify the catalina home). I think that might be why the Debian package that uses init.d to start and stop tomcat has you set the JAVA_HOME variable just before starting the daemon.

It's a lot of spaghetti. I'm currently looking into using mod_jk to hook tomcat and apache2

---

### Post by JimTDI on 2006-11-30
Thanks!  I'll be aware of the /etc/environment caution you pointed out above.

Have you tried installing the FireStarter package (firewall/manager) and seeing if port 80 is blocked?  It's very easy with FireStarter...

---

### Post by Jere Retzer on 2006-12-04
Yes, no it was not blocked. Apache uses it just fine when running.

---

### Post by az on 2006-12-04
> **Jere Retzer said:**
> Yes, no it was not blocked. Apache uses it just fine when running.

Doesn't Tomcat need apache?  You can make apache use a different port than 80 by editing the /etc/apache2/ports file and restarting (reloading) apache2.

---

### Post by az on 2006-12-04
> **JimTDI said:**
> Thanks!  I'll be aware of the /etc/environment caution you pointed out above.

Have you tried installing the FireStarter package (firewall/manager) and seeing if port 80 is blocked?  It's very easy with FireStarter...

1.  You are terribly rude.

2.  There is no reason why the port would be blocked by the kernel "just like that".  And if your ISP were blocking port 80, firestart would not know about it.

---

### Post by Jere Retzer on 2006-12-06
Interesting idea - having Apache use another port. I might give that a shot. Tomcat will function as a standalone web server if set up properly - you don't have to use Apache

---

