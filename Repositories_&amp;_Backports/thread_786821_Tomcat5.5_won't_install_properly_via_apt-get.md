---
title: "Tomcat5.5 won't install properly via apt-get"
date: 2008-05-08
forum: Repositories &amp; Backports
---

### Post by aidave on 2008-05-08
I've tried installing tomcat5.5 from hardy repository but this is becoming a nightmare.  I have no clue why it will not accept the JAVA_HOME, I even bought a book on Tomcat and it wont work.  Just installing it causes a crash report!

So I set JAVA_HOME with both openjdk-6 and sun-java-6, but neither will take.  I used both root account and user account to set JAVA_HOME, like so:

#JAVA_HOME=/path/to/java
#export JAVA_HOME

Yet the JAVA_HOME is never recognized by tomcat or saved after console is closed.

---

### Post by aidave on 2008-05-08
For sun java 6 I used this:
JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.06 


..
Setting up tomcat5.5 (5.5.25-5ubuntu1) ...
 * Starting Tomcat servlet engine tomcat5.5                                     
Cannot locate Java Home
invoke-rc.d: initscript tomcat5.5, action "start" failed.

---

### Post by PaulHuygen on 2008-05-21
> **aidave said:**
> 

I used both root account and user account to set JAVA_HOME, like so:

#JAVA_HOME=/path/to/java
#export JAVA_HOME

Yet the JAVA_HOME is never recognized by tomcat or saved after console is closed.

Maybe writing JAVA_HOME in /etc/default/tomcat5.5 helps.

---

