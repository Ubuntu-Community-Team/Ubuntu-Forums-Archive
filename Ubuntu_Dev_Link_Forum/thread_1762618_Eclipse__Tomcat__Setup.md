---
title: "Eclipse / Tomcat  Setup"
date: 2011-05-19
forum: Ubuntu Dev Link Forum
---

### Post by xannen on 2011-05-19
Hi

I'm still new to Ubuntu and Linux and would like some guidance, but hopefully some step by step instruction on how to setup a JSP web development environment.

I do have understanding of computing and programming in general.  I came from the .NET stream, and was previously working with ASP.NET MVC 3 with SQL Server.  I have had a look at mono, but it is not update with the version of technology I want to use.  I thought learning some Java and JSP in the mix makes for good experience.

One of the problems with Linux is the distribution and their variation of the installation mechanism, which makes it hard for someone to provide a "catch-all" instruction for installing and administering e.g. Tomcat and/or Eclipse.  And I want to use the linux specific installation mechanism, as I do not fully understand the linux system and its directory setup.

So far I've simply use the synaptic package manager to install all my software, from pdf, email, messenger, to Tomcat, Eclipse, and Postgresql.  So I type in search for tomcat and eclipse in synatic manager; and select the latest available version of each software and proceed to install.  And that is as far as I can get to.

(I can verify Tomcat is installed correctly with: localhost:8080.  In Eclipse, I went to the plugin section and install the JSP plugin, to help develop servlet and JSP.)

I suppose my actual question is how to correctly configure these software to work in coordination.

An example with the classic Hello World for Tomcat and Eclipse would be appreciated.

Edit 20 May 2011:

After some more googling I found this thread: [http://ubuntuforums.org/showthread.php?p=8541057](http://ubuntuforums.org/showthread.php?p=8541057)

I followed instructions in post #5 and #10.  What do I do next?  I am simply after enough step by step instructions via a complete example, even if it is just HelloWorld.jsp.  At least it gives me some idea as to how Eclipse and Tomcat operates in Ubuntu.

Also to note, I have my project under ~/workspace/HelloWorld.  Do I need to move this project to the webapps directory in Tomcat?  Is symbolic linking sufficient?

---

### Post by anshulmeena on 2011-10-14
When it come to setup Eclipse, Tomcat and Java there are many things that can go wrong. In this case Ubuntu 11.04 is providing Eclipse 3.5 (Galileo) and Tomcat6 as standard edition through Software Center or Synaptic pkg. or Aptitude. Therefor I was installing Eclipse and Tomcat as they were provided on Ubuntu standard repo. For some reason the Environment variables on Ubuntu were not setting properly so I tried and fixed the variable by placing those variable in system bash file and assigning them values manually:

vi ~/.bashrc

Using CATALINA_BASE: /usr/local/tomcat-6 dir

Using CATALINA_HOME: /usr/local/tomcat-6 dir

Using JRE_HOME: /usr/lib/j2sdk1.6-sun/


this is one way to do it or you can export these variable like in cmd line:

in bash: export JAVA_HOME=/path_to_j2sdk

(e.g. export JAVA_HOME=/usr/local/java/j2sdk similarly for Catalina variable's)

  

In My case above solution was not working even though I invested couple of days it. 
I decided to purge (remove completely) the existing Tomcat6 and Eclispe3.5 and then installed I followed [AskUbuntu]("http://askubuntu.com/questions/37822/how-do-i-install-apache-tomcat-7") and did same with Eclipse3.6. 

1. Download Eclipse3.6 from [eclipse.org]("http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/indigo/SR1/eclipse-jee-indigo-SR1-linux-gtk-x86_64.tar.gz") remember to download J2EE not JAVA for JSP.

2. tar -xzvf filename.tar.gz

3. I placed Tomcat7 and eclipse in the same folder /usr/local/java

   sudo mv Directory_Name(Extracted eg.eclipse /usr/local/java)

4.Check for ROOT Folder in org.eclipse.wst.server.core, Make sure that you replace (or rm -rf old ROOT then cp the new ROOT folder) this ROOT folder created by tomcat6 with new ROOT from tomcat7 because some time ubuntu11.04 do not replace this file by itself and this error will take lot of time to solve so follow these cmd in terminal make sure that you are sudo: 

/home/local/workspace/.metadata/.plugins/org.eclipse.wst.server.core/tmp0/wtpwebapps/ROOT

with /usr/local/java/apache-tomcat-7.0.22-src/webapps/ROOT

From here you can simply click on "eclipse" executable file in  /usr/local/java/eclipse and follow this [link]("http://www.eclipse.org/webtools/community/education/web/t320/Configuring_an_Application_Server_in_Eclipse.pdf") it is based on Tomcat5.5 but tomcat7 server setup in eclipse3.6 is exactly similar to this.  

:guitar:

---

