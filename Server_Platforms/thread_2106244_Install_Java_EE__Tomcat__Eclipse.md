---
title: "Install Java EE / Tomcat / Eclipse"
date: 2013-01-18
forum: Server Platforms
---

### Post by WASHAD on 2013-01-18
First thing - yes, I know that I can do a G-Search and find tons of information on this subject, but that is the problem. There is so much information out there, and much of it takes different approaches. I'm simply too ignorant on the matter to extract the parts that I need. 

What I have: Virtual box and a brand-new install of Ubuntu GUI 32b. 

What I want: 
- To be able do develop a web page and/or a web service using Java, Tomcat, and Eclipse
- To do the development work on my virtual machine, and later export that to an AWS server

What I need: 
- A really good tutorial on getting me from nowhere to somewhere
- Help understanding which of the oh so many versions of Java that I should be downloading
- Maybe a link to a book that would address these specific topics. 

Thanks, 
SteveJ

---

### Post by hawkmage on 2013-01-18
First of all I avoid using the Eclipse, Java and Tomcat that come as a package with the linux distro I am using.  

What I do is in my home directory create a bin directory and in the bin directory I create the directories java and tomcat then I download and untar/expand the versions of Java and Tomcat I want to work with in those directories.  Then I download Eclipse and untar it in the bin directory under my home which should create a directory called eclipse.  

I create a launcher to execute to run ${HOME}/bin/eclipse/eclipse.

In the ${HOME}/bin/java directory I create a symbolic link called "current" to the java version I want to use.

Then I add the following to my .bash_profile, .bashrc or .profile, which every you prefer.  
```
export JAVA_HOME=${HOME}/bin/java/current
export ECLIPSE_HOME=${HOME}/bin/eclipse
export PATH=${HOME}/bin:${ECLIPSE_HOME}:${JAVA_HOME}/bin:${PATH}
```

In the server.xml file under config directory of the each tomcat version directory make sure that in the host element has the value autoDeploy="true".  This way when you place/update a WAR file in the webapps directory it will automatically deploy it with out having to stop and start tomcat.  

Once you run Eclipse you can add the directories in your ${HOME}/bin/java directory for the JDKs and under the ${HOME}/bin/tomcat for the tomcat servers to be used for development.  

THis will get you set up for using Eclipse to develop java apps for tomcat.  I do very little actual development so for learning haw to develop applications that I will let others chip in their recommendations.

---

### Post by WASHAD on 2013-01-19
Thank you for your reply -- a couple of follow up questions based on what I have learned since my post. 

- If I install Tomcat with apt-get, does it include the JRTE and JDK? 
- Will the configuration that I shooting for allow me to debug within eclipse without my having to create a war?

Thank you, 

SteveJ

---

### Post by WASHAD on 2013-01-21
Thank you so very much, Hawkmage for your help. Ultimately, this is the route that I have found to be the best. I'll update this when I get eclipse installed, but I at least have Java and Tomcat. I found the below tutorial to be most useful. It is for tomcat, but will point the reader to the Java install tutorial as well. 

[http://blog.eviac.com/2012/08/installing-tomcat-7-on-ubuntu-1204.html]("http://blog.eviac.com/2012/08/installing-tomcat-7-on-ubuntu-1204.html")

If I were good enough with Ubuntu, I would most certainly make a script to do this operation for me - man is there a lot of confusion out there about the subject. One would think that nobody develops web apps on Ubuntu. 

Cheers.

---

### Post by hawkmage on 2013-01-22
Part of the reason that it is so confusing is that there are many ways of doing this and the "best" way really depends on why you are doing it.  

Placing Java and Tomcat in a standard centralized location using the packages for your linux distribution is great for running a single version of Java and Tomcat but if you need to run multiple instances of different versions it becomes difficult.  

In trying to do development and have to deal with existing applications that are running under differing versions I have found that placing the Java and Tomcat in my home directory and encapsulating the development environment to be very helpful.  

There are ways to extend this method to be able to actually run combinations of different versions of Java, Tomcat and Apache HTTPD all on the same server all through the use of environment variables and symbolic links.

---

