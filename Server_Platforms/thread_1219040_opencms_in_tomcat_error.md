---
title: "opencms in tomcat error"
date: 2009-07-21
forum: Server Platforms
---

### Post by adza on 2009-07-21
Hi There, i'm trying to deploy the opencms war file to a tomcat server, however i keep getting this error in the logs... 
> 21/07/2009 11:30:06 PM org.apache.catalina.startup.HostConfig deployWAR
INFO: Deploying web application archive opencms.war
21/07/2009 11:30:07 PM org.apache.catalina.core.StandardContext start
SEVERE: Error listenerStart
21/07/2009 11:30:07 PM org.apache.catalina.core.StandardContext start
SEVERE: Context [/opencms] startup failed due to previous errors
I'm no java guru at all, can someone please help me where this might not be going to plan? I am at my wits end here? 

Cheers :P

---

### Post by adza on 2009-07-22
*bump*

---

### Post by dragos2 on 2009-07-22
> **adza said:**
> Hi There, i'm trying to deploy the opencms war file to a tomcat server, however i keep getting this error in the logs... 
I'm no java guru at all, can someone please help me where this might not be going to plan? I am at my wits end here? 

Cheers :P

You did a hot deploy ? (copy paste into tomcat webapps)

---

### Post by adza on 2009-07-23
Hi Dragos, thanks for the response. I've fixed this issue now :) Seems that tomcat6, java5 and opencms 7.5 don't play nicely together. Downgraded to tomcat 5.5 and all is humming :)

---

