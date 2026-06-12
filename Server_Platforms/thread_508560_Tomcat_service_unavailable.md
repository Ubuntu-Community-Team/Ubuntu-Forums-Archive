---
title: "Tomcat service unavailable"
date: 2007-07-24
forum: Server Platforms
---

### Post by asmweb on 2007-07-24
Hi there, 

i run into some problems with Tomcat5.5 server. I am trying to make it work as a service of apache2 but I get an error message when i go to the jsp-examples page:
Service Unavailable

I did install the j2se through the java web site and installed the tomcat5.5 and libapache2-mod_jk through synaptic. I pu the java environment in /opt/java and set the right java_home. Though I see some other java dirs at /usr/lib/jvm/java-1-6-0-sun 

I did dig through the other posts in these forum but i could not get any hint. 

Any help, would be appreciated

---

### Post by meatpan on 2007-07-24
Just for do-diligence, can you verify that both services are running?  

Take a look at the output of the command 'pstree'.  You should see entries for tomcat and apache (although the names might be slightly different, such as 'apache2').

If these are *not* running, start them up, via apachectl, and the tomcat startup script (I forgot what this is called, but it serves a similar purpose as apachectl).   Wait a few seconds, then try running the command 'netstat -Cvaetpu'.   Once again you should see both tomcat and apache, but this time you can observe the services and associated ports to which they are bound.  If everything looks good, wait a few seconds and try your demo.

At this point, if the problem persists, you will most likely need to make some configuration adjustments.

---

### Post by asmweb on 2007-07-24
Am afraid I need some configuration adjustment but I can not determine where...
 well I do not have problems with apache it starts normale as theorically tomact. When I type /etc/init.d/tomcat5.5 start the output is tomcat started [ok] 
but I do not see it at the netstat output on the other hand i didn't tried yet pstree

---

### Post by ilcavero on 2007-07-24
try reading this

[http://ubuntuforums.org/showthread.php?t=215693](http://ubuntuforums.org/showthread.php?t=215693)

---

### Post by asmweb on 2007-07-25
Well the strange thing is that when I do

/usr/share/tomcat5.5/bin/catalina.sh run (which makes it run in the current window)

it works really well but on the other hand when I do either

/usr/share/tomcat5.5/bin/catalina.sh start (which makes it run in a different window)

/usr/share/tomcat5.5/bin/start.sh

it does not make the apache start... how come

---

