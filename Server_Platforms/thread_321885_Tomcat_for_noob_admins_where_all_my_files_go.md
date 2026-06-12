---
title: "Tomcat for noob admins: where all my files go?"
date: 2006-12-19
forum: Server Platforms
---

### Post by pmasiar on 2006-12-19
Can someone from the gurus to point me to a guide how to install Tomcat for Edgy? I found plenty of guides, but none specific to Ubuntu. 

I have general idea how CGI works, wrote couple CGI programs in perl and python, can do simple Linux admin tasks. I understand how to set up apache2 web server - but now I need to get up tp speed with java/Tomcat, quickly. 

I plan to use java, Eclipse, Tomcat, Struts - versions in Edgy. Should I stick with Dapper? I use also Sysdeo Tomcat plugin for eclipse - does it make sense? My windows friends use it. I intend to develop using local Tomcat server (I can start/stop it as needed - it's mine only), then deploy my app to big Linux server.

I read many articles, but I am still not any wiser. here are good (AFAICT) links I found:

[LIST]
[*][Tomcat tutorial for complete fools]("http://www.keyboardsamurais.de/mt/archives/000053.html")
[*][Eclipse Web Tools]("https://help.ubuntu.com/community/EclipseWebTools") - help.ubuntu.com
[*][Top Ten Tomcat Configuration Tips]("http://www.onjava.com/pub/a/onjava/2003/06/25/tomcat_tips.html") - onjava.com
[*][ CATALINA_HOME - Ubuntu - Eclipse]("http://ubuntuforums.org/showthread.php?t=309546") - ubuntuforums
[*][  Servlet / Web app on Tomcat on Linux tutorial]("http://ubuntuforums.org/showthread.php?t=172897") - ubuntuforums

[/LIST]

Guides I found suggest manual install - but we have Synaptic for that, right? But... with synaptic, I have no idea where my files are placed. and what is my Tomcat Home etc.

So I ask for advice, what to do after Synaptic installed tomcat, tomcat-admin, tomcat-webapps, and how to run some kind of "hello world" to make sure it is installed properly. 

[LIST]
[*](1) Where are my tomcat config files? What is 'Tomcat Home" for sysdeo plugin? In Sysdeo is not used, what I need to config in Eclipse? Is Tomcat different from CATALINA files?
[*](2) Do I need to setup some environment variables? In my own .bashrc? Somewhere in Tomcat config files? How environment is set for web browser user (== tomcat)?
[*](3) I assume to test that Tomcat is configured and running, in Ubuntu I go to port [http://localhost:8180/](http://localhost:8180/)  -- nothing is runnig there now. 
[*](4) How access tomcat-webmin and webapps ? I some examples in  /var/lib/tomcat5.5/webapps/jsp-examples - how to run them?
[*](5) I suspect, after I compiled my java classes, I need to place them somewhere so Tomcat can find them. Where? Just copy them, or soem neat trick to make it easier? Can I configure Tomcat to run classes from my home subdirectory, so I don't have to shuffle files around? Like I did in python: edit, save, refresh.
[/LIST]

I can follow the guides, RTFM, but so far did not found the good ubuntu-specific docs.

Any help, links is greatly appreciated.

---

### Post by pmasiar on 2006-12-19
self - help. reading again [https://help.ubuntu.com/community/EclipseWebTools](https://help.ubuntu.com/community/EclipseWebTools) - they "sudo mv apache-tomcat-5.5.15 /opt/" - where it came from? I have tomcat5.5, not apache-tomcat . Is it same thing? I found my tomcat-users.xml there, must be the same! Why to move tomcat to /opt?

They also use fakeroot. And don't use synaptic/apt-get. confused.

---

### Post by pmasiar on 2006-12-20
Pretty please? Are there any tomcat experts in ubuntu forums?

---

### Post by firebadger on 2006-12-20
Right, I don't know of any guides, but this is what I would recommend...  Very quickly jotted down.

Installing Tomcat:

Assuming as a starting point you have the Sun Java 1.5 SDK installed.  You next need to ensure that the environment variable JAVA_HOME points to this installation.  I used the sun-java5-jdk package from the repositories and I think this results in JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.08.  Anyway I'd stick this in the /etc/bash.bashrc file.

Now, download the latest stable Tomcat 5.5.whatever from tomcat.apache.org (the core distribution) and to install you just extract somewhere.  That's all!  You don't really need to set TOMCAT_HOME or CATALINA_HOME as tomcat can work this out for itself.

To test, go to the bin directory in the tomcat directory tree and run ./startup.sh.  Once started up you should be able to visit [http://localhost:8080](http://localhost:8080) (8080 is the default port not 8180!)in your browser and see it running.  There are sample webapps installed by default that you can look at too.

Sysdeo plugin is ok - or it was when I last used it a couple of years ago.  The TOMCAT_HOME (as is CATALINA_HOME) environment variables, if you hear them referred to, should just be the path to the directory that tomcat has extracted to.

There is a manager app, but you don't really need to use it especially on a dev box.  However, if you replace the tomcat-users.xml file in the conf directory with this one, you will be able to use it...  Change the password though!

```
<?xml version='1.0' encoding='utf-8'?>
<tomcat-users>
  <role rolename="manager"/>
  <user username="manager" password="password" roles="manager"/>
</tomcat-users>

```

You'll have to google for info about how to build a simple webapp as I am getting bored of typing.  I'll try to answer any questions you might have though.

---

### Post by phossal on 2007-01-02
I've installed and used Java/Tomcat/Eclipse on a variety of platforms. I can configure them in my sleep. I would be happy to help you, but you absolutely have to stop responding to my posts "out and about" with idiotic comments. It's getting annoying.

---

