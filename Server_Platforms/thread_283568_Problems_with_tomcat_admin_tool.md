---
title: "Problems with tomcat admin tool"
date: 2006-10-24
forum: Server Platforms
---

### Post by frank05 on 2006-10-24
I've installed tomcat and the assicated webapps and manager application from the ubuntu repos with apt-get. I changed the tomcat-users.xml files to include tomcat,role1,admin and manager roles ( I would have thought role1, and tomcat would have been included by default, but it appears not). I also assigned tomcat the role of admin and manager.

I am then able to login to the administration tool (logged in as tomcat). However, there are things missing from the side menu and when I click on one of them I getting interal server errors such as the following:

```

(After clicking on Databases)

ava.lang.IllegalStateException: Cannot forward after response has been committed
	java.security.AccessController.doPrivileged(Native Method)
	org.apache.struts.action.RequestProcessor.doForward(RequestProcessor.java:1085)
	org.apache.struts.action.RequestProcessor.processForwardConfig(RequestProcessor.java:398)
	org.apache.struts.action.RequestProcessor.process(RequestProcessor.java:241)
	org.apache.struts.action.ActionServlet.process(ActionServlet.java:1196)
	org.apache.struts.action.ActionServlet.doGet(ActionServlet.java:414)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:689)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	sun.reflect.GeneratedMethodAccessor53.invoke(Unknown Source)
	sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	java.lang.reflect.Method.invoke(Method.java:585)
	org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:243)
	java.security.AccessController.doPrivileged(Native Method)
	javax.security.auth.Subject.doAsPrivileged(Subject.java:517)
	org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:272)
	org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:161)
	java.security.AccessController.doPrivileged(Native Method)
	org.apache.webapp.admin.filters.SetCharacterEncodingFilter.doFilter(SetCharacterEncodingFilter.java:123)
	sun.reflect.GeneratedMethodAccessor54.invoke(Unknown Source)
	sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	java.lang.reflect.Method.invoke(Method.java:585)
	org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:243)
	java.security.AccessController.doPrivileged(Native Method)
	javax.security.auth.Subject.doAsPrivileged(Subject.java:517)
	org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:272)
	org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:217)


```

This may of course point to a more general problem than just the admin tool. Any ideas where to start with fixing this?


Thanks,

---

### Post by frank05 on 2006-10-24
Just realised there's another guy with the same problem as me
[http://ubuntuforums.org/showthread.php?t=227982](http://ubuntuforums.org/showthread.php?t=227982)

sorry for adding another thread!

As I say I'm pretty sure I've configured the users correctly, and this guy seems to have aswell.

edit: corrected link

---

### Post by Dr. Falken on 2006-10-25
> **frank05 said:**
> Just realised there's another guy with the same problem as me
[http://ubuntuforums.org/showthread.php?t=283568&highlight=tomcat](http://ubuntuforums.org/showthread.php?t=283568&highlight=tomcat)

sorry for adding another thread!

As I say I'm pretty sure I've configured the users correctly, and this guy seems to have aswell.
plz, correct the URL, 'cause that URL points to THIS thread.

---

### Post by frank05 on 2006-10-26
oops sorry. I've corrected that now.

---

