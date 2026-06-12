---
title: "Ubuntu 16.04 server  error installing Alfresco community edition"
date: 2017-03-14
forum: Server Platforms
---

### Post by deepakdeshp on 2017-03-14
I downloaded  the installer file and it gives me following error.Some or all of the libraries needed to support **LibreOffice were not found on your system: fontconfig libSM libICE libXrender libXext libcups libGLU libcairo2 libgl1-mesa-glx. **Since it is a server Libre office isnt installed on it.


Then I go ahead and I get following errors for Tomcat
Tomcat Port Configuration
Enter your Tomcat configuration parameters.
Web Server Domain: [127.0.0.1]:
Tomcat Server Port: [8080]:
Tomcat Shutdown Port: [8005]:
Tomcat SSL Port: [8443]:
Tomcat AJP Port: [8009]:
Warning: Unable to bind to the given port number. This port is already in use by 
the java process. Select another Tomcat Server Port.
Press [Enter] to continue:
Warning: Couldn’t bind to the given port number. Select another Tomcat Shutdown 
Port.
Press [Enter] to continue:


I have installed Tomcat and can see the Tomcat page  at :8080 also , 
server,xml has following entry
```
  -->
<Server port="8005" shutdown="SHUTDOWN">
  <Listener className="org.apache.catalina.startup.VersionLoggerListener" />
  <!-- Security listener. Documentation at /docs/config/listeners.html
  <Listener className="org.apache.catalina.security.SecurityListener" />
  -->
  <!--APR library loader. Documentation at /docs/apr.html -->
  <!--
  <Listener className="org.apache.catalina.core.AprLifecycleListener" SSLEngine="on" />
  -->
  <!--Initialize Jasper prior to webapps are loaded. Documentation at /docs/jasper-howto.html -->
  <Listener className="org.apache.catalina.core.JasperListener" />
  <!-- Prevent memory leaks due to use of particular java/javax APIs-->
  <Listener className="org.apache.catalina.core.JreMemoryLeakPreventionListener" />
  <Listener className="org.apache.catalina.mbeans.GlobalResourcesLifecycleListener" />
  <Listener className="org.apache.catalina.core.ThreadLocalLeakPreventionListener" />


  <!-- Global JNDI resources
       Documentation at /docs/jndi-resources-howto.html
  -->
 
```
yet I get the errors mentioned above.
I will be thankful for any clues for successfully installing Alfresco.

---

### Post by TheFu on 2017-03-14
A little background, we used to run Alfresco, but dropped it about 5 yrs ago when a migration wasn't possible from a beta release branch to the new supported branch. Our company wasn't using it correctly and it was just more hassle than it was worth, for us.  It is an amazing solution provided that folks use it as a true DMS, document management system.  BTW, I worked in electronic publishing and documentation for about 5 yrs and I selected Alfresco for the company's use.

With all that, I remember that LibreOffice was used to convert documents to different formats at the request of the different filters. It is convenient to upload a docx and have that converted to an ODF or PDF for publishing automatically.  I do remember alfresco logs always having multiple complaints, most turned out not to be important.  I thought alfresco installed the version of tomcat they wanted, so another install would get in the way of theirs.  Not certain about that. My memory isn't clear.

Found this warning: 
> NOTE: 16.04 user must manually edit the ams.sh script before use to use the correct shutdown method. 
More install steps: [https://docs.alfresco.com/community/tasks/simpleinstall-community-lin.html](https://docs.alfresco.com/community/tasks/simpleinstall-community-lin.html)
and this script: [https://github.com/loftuxab/alfresco-ubuntu-install](https://github.com/loftuxab/alfresco-ubuntu-install) can clarify some things that the alfresco-centric people may forget. After all, for an install script to work, it has to handle the details.

For any more help, I suspect you'll need to visit the alfresco support forums.

BTW, please make certain your apache and tomcat are patched. There's a nasty bug that was announced last week about those tools when used together.

---

### Post by deepakdeshp on 2017-03-15
Thank you Thefu for your detailed reply. I am installing Alfresco just for the sake of learning. I found the github script and installed many things which it prompted, Some of the things I should not have installed , like it prompted for Tomcat 8 , which I soudnt have as tomcat 7 was already installed, Nginx, I shouldnt have installed as Apache2 was running well.

I was getting the Tomcat page server:8080 and was able to see it.But in trying the script , I have blundered and can not see the Tomcat page now at server:8080. The error is **connection refused**

---

### Post by deepakdeshp on 2017-03-20
I am trying to install Alfresco using the script at [https://github.com/loftuxab/alfresco-ubuntu-install/blob/master/alfinstall.sh](https://github.com/loftuxab/alfresco-ubuntu-install/blob/master/alfinstall.sh)
I opened a thread at Alfresco community but have no clue hiw do I see the threads I opened.Any clues please?
 [https://community.alfresco.com/discussion/create.jspa?question=true&containerType=14&containerID=2007&subject=](https://community.alfresco.com/discussion/create.jspa?question=true&containerType=14&containerID=2007&subject=)

I have nginx and Apache both installed. When I start nginx and stop apache  I get the page Alfresco is under maintenance on the browser. On the browser whatever applcations I open like phpmyadmin, I get the same page.
When I start Apache , stopping nginx, I can see other pages like phpmyadmin. Both times tomcat7 does not start. [COLOR=#58595B][FONT=monospace]${catalina.base} and [/FONT][/COLOR][COLOR=#58595B][FONT=&quot] [/FONT][/COLOR][COLOR=#58595B][FONT=&quot]<TOMCAT_HOME> arent set by the system .
/opt/alfresco/tomcat/conf/catalina.properties
/opt/alfresco/tomcat/apache-tomcat-8.0.38/conf/catalina.properties folders.


I have 
[/FONT][/COLOR][COLOR=#58595B][FONT=monospace] [/FONT][/COLOR]

---

