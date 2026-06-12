---
title: "Where to set JAVA_HOME on GeoServer"
date: 2009-03-14
forum: Server Platforms
---

### Post by R.Bucky on 2009-03-14
Has anyone installed Geoserver? I host my own Ubuntu Server LAMP and have absolutely pulled my hair out trying to set the JAVA_HOME variable. When I use the startup.sh, and the JAVA_HOME variable request is thrown at me. What file does this variable need to be set?

---

### Post by windependence on 2009-03-15
It gets set in /etc/environment. Here is a quick way to do it, but use your path to your Java, not the one I have here:

```
sudo bash -c "echo JAVA_HOME=/usr/lib/jvm/java-6-sun/ >> /etc/environment"
```

This is the cleanest way to do it.

-Tim

---

### Post by R.Bucky on 2009-03-15
I have set the variable in the /etc/environment file with no success. After reboot, here is what I receive in terminal 
```
The JAVA_HOME environment variable is not defined
This environment variable is needed to run this program
```
Here is the content for my Java in the /etc/envrionment file
```
JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.07"
export JAVA_HOME
```

Again, this is for use in Geoserver if that makes a difference.

---

### Post by alberto_colon on 2009-05-02
Mark,

I guess you want to change the JVM for tomcat, so GeoServer runs with that specified JVM.  If so, then it depends on the ubuntu and tomcat versions you are using.  If you are running tomcat6 from the repositories on ubuntu 8.10, then you need to change the JAVA_HOME parameter on /etc/default/tomcat6.

Once updated, start and stop tomcat for the changes to take effect.

This is the way I have made GeoServer run on an Ubuntu 8.10 server.

This should also work with Ubuntu 9.04, but I have not tested it yet.

You can take a look [here]("https://help.ubuntu.com/8.10/serverguide/C/tomcat.html") for more details.

-Albertico

---

### Post by John Cheng on 2009-05-02
> **R.Bucky said:**
> I have set the variable in the /etc/environment file with no success. After reboot, here is what I receive in terminal 
```
The JAVA_HOME environment variable is not defined
This environment variable is needed to run this program
```
Here is the content for my Java in the /etc/envrionment file
```
JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.07"
export JAVA_HOME
```

Again, this is for use in Geoserver if that makes a difference.

Another thing you can try is to set the JAVA_HOME environment variable in the "profile" file for that user account.

For example, I want to run the RedHat JBoss application server. In this example, I created a user named "jboss" to run it

/etc/passwd
```
jboss:x:302:302:,,,:/home/jboss:/bin/bash

```

Note that its login shell is bash and its home directory is /home/jboss.

Then in /home/jboss/.profile, I have

```

JAVA_HOME=<path to java>
export JAVA_HOME

```

When the system logs in the jboss user, the "$HOME/.profile" file is loaded, and the JAVA_HOME environment is automatically set.

---

