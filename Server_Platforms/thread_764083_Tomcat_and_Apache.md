---
title: "Tomcat and Apache"
date: 2008-04-23
forum: Server Platforms
---

### Post by daveklein on 2008-04-23
I would like to set up tomcat and apache on an Ubuntu server. I want to set it up so that [www.mydomain.com](www.mydomain.com) hits my webapp (hosted by tomcat) directly. I am a completely newbie webadmin, so I am not sure where to start. 

I am also open to using tomcat on it's own (without apache), but I don't want ":8080/mywebapp" showing up on the address bar...

I found a few tutorials but they all seemed pretty outdated

---

### Post by HermanAB on 2008-04-23
You need a Tomcat Connector.  Here is another guide for you: [http://aeronetworks.ca/tomcat-howto.html](http://aeronetworks.ca/tomcat-howto.html)

Cheers,

Herman

---

### Post by Atomsmasher on 2008-04-23
Hey daveklein,

to elaborate on HermanAB's response, here is a link from another poster a few months ago.

[http://ubuntuforums.org/showthread.php?t=219985&highlight=Apache+Tomcat+mod_jk](http://ubuntuforums.org/showthread.php?t=219985&highlight=Apache+Tomcat+mod_jk)

I've been battling this setup for a few days myself and have yet to find the answer.

My first step is just to get Tomcat going through Apache, so [http://localhost/servlet](http://localhost/servlet) actually hits my Tomcat server.

I manually installed Tomcat6, downloaded the mod_jk binary myself, and followed all of the Apache documentation, to no avail.  Here's the Apache link:
[http://tomcat.apache.org/connectors-doc/webserver_howto/apache.html](http://tomcat.apache.org/connectors-doc/webserver_howto/apache.html)

If you have success at all, do you mind posting back?  I'll do the same if I get this working.  I plan on going back to battle this evening.

---

### Post by daveklein on 2008-04-24
I'll check out the links you gave me. And yes, I'll be sure to post here if I get it to work.

---

### Post by Atomsmasher on 2008-04-30
Hi Dave, I think I've got it working.

I couldn't use the auto-generated mod-jk.conf from Tomcat, so I created a static one.  Follow these steps and let me know how it goes.

If you've not already done so, install the libmod-jk library using your Package Manager.
You should now have a file mod_jk.so installed (mine is at /usr/lib/apache2/modules)

Below is my configuration file for mod-jk (located at $TOMCAT_INSTALL/conf/jk/mod-jk.conf)

# Load mod_jk module
# Update this path to match your modules location
# Leave this commented out too.  It's already loaded somehow
# and this throws a warning
#LoadModule    jk_module  /usr/lib/apache2/modules/mod_jk.so

# Where to find workers.properties
JkWorkersFile $TOMCAT_INSTALL/conf/jk/workers.properties

# Where to put jk shared memory
JkShmFile     /var/log/apache2/mod_jk.shm

# Where to put jk logs
JkLogFile     /var/log/apache2/mod_jk.log

# Set the jk log level [debug/error/info]
JkLogLevel    info

# Select the timestamp log format
JkLogStampFormat "[%a %b %d %H:%M:%S %Y] "


Now here is the line I added to my apache2.conf file

#For Tomcat
Include /opt/tomcat/conf/jk/mod-jk.conf

Lastly, I created a file as Apache suggested to restart my apps in the right order:

#!/bin/bash

apache2ctl -k stop
$TOMCAT_INSTALL/bin/shutdown.sh
$TOMCAT_INSTALL/bin/startup.sh
apache2ctl -k start


I hit [http://localhost/examples/servlets](http://localhost/examples/servlets) and it worked!

NOTE: Don't forget to replace $TOMCAT_INSTALL with your install path.  Don't try to create an environment variable named TOMCAT_INSTALL.

Good luck!

---

### Post by datajelly on 2008-08-12
You should be able to setup Tomcat as a stand-alone server running on port 80. However, if you are looking to use Apache as a front-end and have it proxy requests to Tomcat, that is the same setup that I have used.

We originally set this up on Windows, but have since migrated over to Ubuntu and have been much happier. We have a tutorial written on our blog if you are interested:

[http://blog.datajelly.com/2007/12/using-apache-for-ssl-offloading-and.html]("http://blog.datajelly.com/2007/12/using-apache-for-ssl-offloading-and.html")

---

