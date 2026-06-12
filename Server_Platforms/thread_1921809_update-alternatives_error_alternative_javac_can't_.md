---
title: "update-alternatives: error: alternative javac can't be a slave of java..."
date: 2012-02-07
forum: Server Platforms
---

### Post by Kurtosis on 2012-02-07
Hello, I'm trying to install Oracle JDK 1.6.0_30 on Ubuntu Server 11.10.  OpenJDK 6 and OpenJDK 7 are already installed, and I'm setting up OracleJDK using update-alternatives.

I've done this with no problems on my Ubuntu Desktop 11.10 workstation, but the same process is resulting in this error on the server:

```
update-alternatives: error: alternative javac can't be a slave of java: it is a master alternative.
```

The setup process is:

1.  Download, extract, and copy the extracted jdk1.6.0_30 to usr/lib/jvm/jdk1.6.0_30.

2.  Setup default-jvm soft link and $JAVA_HOME:
```
ln -s /usr/lib/jvm/jdk1.6.0_30 /usr/lib/jvm/default-java
```
Add $JAVA_HOME to .profile:
```
export $JAVA_HOME='/usr/lib/jvm/default-java'
``` 

3.  Use [this script]("https://raw.github.com/byrongibson/scripts/master/install/java/java-alt-install-oraclejdk6-server-allslave.sh") to add jdk1.6.0_30 to the update-alternatives java list.

The error occurs at #3 when I use the script.  I can slave javac to java on Ubuntu Desktop, but not on Ubuntu Server.  Any idea why?

---

### Post by hawkmage on 2012-02-07
Yes the sad thing is that the way that alternatives is configured for java it doesn't place all of the JDK/JRE commands in a single alternative as slave commands it adds some of them individually.  

This is an issue because if you "fix" this you break the updates because future updates will try add any new javac as its own alternative and it will fail causing the update to fail.  

I had created a great little script that updated the alternatives for all of the Java commands all you needed to do is supply the JDK/JRE directory and it set all of that versions command as slaves for the java alternative.  Then I ran into this issue and had to remove my custom alternatives.

---

### Post by Kurtosis on 2012-02-07
Ok, thanks.  In your script, did you try separating out javac from the java part?  I'll try that in mine and repost the results.

Also, strange that this isn't a problem on Ubuntu Desktop, just Server, same version and everything.

---

### Post by hawkmage on 2012-02-07
I thought about separating the alternatives for java and javac so that java got the JRE stuff and the javac got the JDK but I really did not feel like working around what I considered a broken implementation.  

It is odd that you did not run into this on the Desktop edition because that is where I had me issue.  

On server I don't use the standard Tomcat/Apache installs I have my own location for them and I have different accounts for different application and I set the JAVA_HOME and PATH in the users profile for the JRE/JDK for that application user.

---

### Post by Kurtosis on 2012-02-07
> **hawkmage said:**
> On server I don't use the standard Tomcat/Apache installs I have my own location for them and I have different accounts for different application and I set the JAVA_HOME and PATH in the users profile for the JRE/JDK for that application user.
I've been thinking about doing that too lately.  I already install all the rest of the app stack in /opt, may as well put JDK in there as well, and just use JAVA_HOME and PATH to point to it.

---

### Post by hawkmage on 2012-02-07
I actually create a separate volume mounted on /apps and put all of the application related stuff there.  

I also separate the binary files of Tomcat and Apache from the applications config through the use of CATALINA_HOME, CATALINA_BASE and APACHE_HOME.  This way I have one copy of the binaries of the versions of Tomcat/Java/Apache I use making patching easier.  I use a few scripts to set the environment variables and define symlinks that connects the application environment with the needed binaries.

This may be more than you want to get into but it really helps when you are hosting dozens of applications that are using differnet versions of Tomcat/Java/Apache.  

(I can not share the scripts since the company I work for owns them but the concept is mine)

---

