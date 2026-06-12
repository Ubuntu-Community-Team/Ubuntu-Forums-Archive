---
title: "Tomcat6 package installation: logs are not being written"
date: 2009-09-21
forum: Server Platforms
---

### Post by shuetrim on 2009-09-21
Tomcat is failing to start my web application and I am having trouble diagnosing the problem because no log files appear to be getting generated.  Can someone tell me where they should be or how to ensure that detailed logging is done to show what is going wrong when tomcat tries to start various web applications.

My setup is as follows.

I am running Ubuntu 9.04
Kernel: Linus 2.6.28-15-generic
GNOME 2.26.1

I am using the sun-java6-jdk.
I have installed the following tomcat packages:
tomcat6 
tomcat6-common 
libtomcat6-java 
tomcat6-admin 
tomcat6-docs 
tomcat6-examples

Tomcat installs into /usr/share/tomcat6

Catalina base appears to be /var/lib/tomcat6

I have installed the web application that I want to run as:
/var/lib/tomcat6/webapps/myapp.war

Tomcat tries to deploy it, as evidenced by it being unpacked when Tomcat6 is restarted using: ```
sudo /etc/init.d/tomcat6 restart
```

Deployment fails however.  I determine this via the tomcat6 administration web interface where the relevant application is shown with a running status of false.  When I try to use the tomcat web application manager to start the web application the message is:

> FAIL - Application at context path ... could not be started

When I look in /var/log/tomcat6 to see details of why it could not be started, I find that the directory is empty.

Any suggestions about how to get tomcat6 to record the relevant logs and where they should be recorded would be very helpful at this stage.

FWIW: I did spend some time fiddling around with the /var/lib/tomcat6/conf/logging.properties file but to no avail.

Regards

Geoff

---

### Post by shuetrim on 2009-09-22
For what it is worth, I am accessing tomcat through Apache using mod_jk.  The Apache logs are being written out fine in the /var/log/apache2 directory.

---

### Post by fadishei on 2009-09-28
I had the same problem and found where the problem lies by running the tomcat server in foreground and tracing the logger exceptions. It is an issue related to the tomcat policies.

After I changed the file policy.d/03catalina.policy from: 

```

grant codeBase "file:${catalina.home}/bin/tomcat-juli.jar" {
    permission java.security.AllPermission;
    permission java.util.PropertyPermission "java.util.logging.config.class", "read";
    permission java.util.PropertyPermission "java.util.logging.config.file", "read";
    permission java.lang.RuntimePermission "shutdownHooks";
    permission java.io.FilePermission "${catalina.base}${file.separator}conf${file.separator}logging.properties", "read";
    permission java.util.PropertyPermission "catalina.base", "read";
    permission java.util.logging.LoggingPermission "control";
    permission java.io.FilePermission "${catalina.base}${file.separator}logs", "read, write";
    permission java.io.FilePermission "${catalina.base}${file.separator}logs${file.separator}*", "read, write";
    permission java.lang.RuntimePermission "getClassLoader";
    ....

```

to:

```

grant codeBase "file:${catalina.home}/bin/tomcat-juli.jar" {
    permission java.security.AllPermission;
};

```

the logging problem disappeared and log file generation started in /var/log/tomcat6.

Regards
Fadishei

---

### Post by shuetrim on 2009-09-28
Thanks for the suggestion.  I will give it a try.

Regards

Geoff

---

