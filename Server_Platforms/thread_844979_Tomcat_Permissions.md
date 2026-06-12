---
title: "Tomcat Permissions"
date: 2008-06-30
forum: Server Platforms
---

### Post by leg on 2008-06-30
I seem to be having some problems with permissions using the Tomcat server. I am on 8.04 and have installed the version of Tomcat from synaptic. Some, not all, of the apps I have do not run and I keep finding permission denied errors on log files and class files. I use startup.sh from a console but I think I may be running this as my user, can't remember will have to check when I get home. Should I be starting this process as root (dubious) or should I have a user and group set up just for tomcat to use. There is a tomcat55 user but seems to be assignned to nogroup or something similar.

Just to add salt to the wound I have brought the app into work this morning and put it all in the windows set up I have and it all works nicely :( so this convinces me that I have my Tomcat set up at home wrong rather than anything else.

Any help appreciated.

---

### Post by lazy74 on 2008-06-30
Hello,
All the Permission-related problems with Tomcat are related to java policies. 

See the files in /etc/tomcat5.5/policy.d/

Basically Debian (the distrib ubuntu is based on) has some twisted security settings. You usually end-up giving all permissions everywhere wich probably kills the purpose of security in the first place (yes I'm quite pissed off after another day spent fiddling with the policy files)

You may check the tomcat doc on the subject, however remember that Debian added their own implementation of this. I'll add links as I find theim...

[http://tomcat.apache.org/tomcat-5.5-doc/security-manager-howto.html](http://tomcat.apache.org/tomcat-5.5-doc/security-manager-howto.html)

---

### Post by leg on 2008-06-30
Thanks looks a pain.

---

### Post by leg on 2008-07-01
Unfortunately I still need some help with this as I can't seem to get it right. What I don't understand is why some of the apps (all the ones that come by default and one I have installed from another developer) seem to work no problem. Even some of my own apps seem to work but not all. I am pretty sure that I have my web.xml file correct I will post just in case.
```

<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://java.sun.com/xml/ns/j2ee"
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation="http://java.sun.com/xml/ns/j2ee http://java.sun.com/xml/ns/j2ee/web-app_2_4.xsd" 
   version="2.4">
 <display-name>JForum Application</display-name>
 
 <servlet>
 	<servlet-name>jforum</servlet-name>
 	<servlet-class>uk.co.glasys.JForumApp</servlet-class>
 	
 	<servlet-mapping>
   		<servlet-name>jforum</servlet-name>
   		<url-pattern>/index.html</url-pattern>
 	</servlet-mapping> 	
 </servlet>
 
 <listener>
   	<listener-class>uk.co.glasys.JForumApp</listener-class>
 </listener>
 
 <context-param>
   	<description>The JDBC driver class.</description>
   	<param-name>jdbcDriver</param-name>
   	<param-value>com.mysql.jdbc.Driver</param-value>
 </context-param>
 <context-param>
   	<description>The JDBC connection string.</description>
   	<param-name>jdbcConnectionString</param-name>
   	<param-value>jdbc:mysql://localhost/jforum?user=user&amp;password=pass</param-value>
 </context-param>

</web-app>

```but I get this error every time:
```
type Status report

message /jforum/

description The requested resource (/jforum/) is not available.
```
Other apps do work but not with a db yet. Do you think I have a specific problem with accessing the database? Which location are the logs I should be trawling for errors and clues?

Any ideas/tutorials/resources would be appreciated.

I have found [this link]("http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/") what do you think about what it says about Ubuntus version of Tomcat? Does he have a point and would it be beneficial to install it manually?

[edit]I am pretty sure that my main problem is permission to access the database here. Off to find out how to change.

---

### Post by rax_m on 2008-07-04
Hi 

Did you manage to resolve this problem yet? I think I'm having something similar. 
Still busy reading all the links posted on this thread. 

Thanks
Rax

---

### Post by rax_m on 2008-07-04
This link might be useful as well:
[http://blixtra.org/blog/2006/07/14/setting-up-tomcat-5-on-ubuntu-606/](http://blixtra.org/blog/2006/07/14/setting-up-tomcat-5-on-ubuntu-606/)

---

### Post by leg on 2008-07-04
> **rax_m said:**
> Hi 

Did you manage to resolve this problem yet? I think I'm having something similar. 
Still busy reading all the links posted on this thread. 

Thanks
Rax

Not yet but I have read the thread you posted and that was a problem I had before this one. I solved that problem by changing the ownership of the log file so that my user had access. I think I should have changed the groups so that my users group was a member of the tomcat55 group. I think my only problem now is that I have not granted permission for my Driver.class to access the socket which I am currently looking into understanding.

Thanks for the link you posted all info is welcome.

[edit]
After reading some of your article I have seen the command etc/init.d/tomcat5.start and I don't start tomcat that way. I use startup.sh as my user. Maybe this is my problem.

---

