---
title: "Feisty + Tomcat5.5 HowTo"
date: 2007-05-07
forum: Server Platforms
---

### Post by Emblem Parade on 2007-05-07
Argh. So, if you tried installing tomcat5.5 from the repositories, you may have noticed that it's broken. You get a configuration error about JAVA_HOME not being set. Actually, there are three problems! Here's what you can do to get it to work:

**1) Install**

```
sudo aptitude install sun-java6-jdk tomcat5.5
```

(Note that you absolutely need the JDK, not just the JRE.)

**2) Set Tomcat's default JAVA_HOME**

```
sudo gedit /etc/default/tomcat5.5
```

Uncomment the JAVA_HOME line and set it to your JDK path. For Java 6 installed from the repositories, it's as so:

```
JAVA_HOME=/usr/lib/jvm/java-6-sun
```

**3) Fix catalina.out**

Unfortunately, it seems that Tomcat's log file is set to be a pipe, but Tomcat can't seem to start with it. We'll recreate it as a regular file with the same security settings:

```
cd /var/log/tomcat5.5/
sudo rm catalina.out
sudo touch catalina.out
sudo chown tomcat55:nogroup catalina.out
sudo chmod uo-wrx catalina.out
```

Tomcat should work now as a daemon. Start it like this:

```
sudo /etc/init.d/tomcat5.5 start
```

And point your browser at [http://localhost:8180/]("http://localhost:8180/")

Hooray!

This may be good enough for you. However, if you want to try to run Tomcat *not* as a daemon, but from a development tool (in my case I was using [Sysdeo's Tomcat plugin for Eclipse]("http://www.sysdeo.com/eclipse/tomcatplugin")), you will find Tomcat announcing rather bizarre errors. So:

**4) Change permissions on Tomcat's work directory**

```
cd /var/cache
sudo chmod go+rwx tomcat5.5
```

(This is probably not the most secure solution, but it should be OK for development environments. For production environments, you really don't want anything to have access to Tomcat's work directory! Another solution may be to change the link to this directory from /usr/share/tomcat5.5/work, which is what Tomcat actually uses.)

Thanks to the many folk on Ubuntu Forums who struggled to make this work. I merely put their advice together into a howto. Good luck, and let's hope the tomcat5.5 package manager fixes these bugs!

---

### Post by garba on 2007-05-08
thanks a lot for these tips, tomcat has always been a source of trouble to no end in my experience

---

### Post by mkw87 on 2007-05-15
When I try the following command:

```
sudo chown tomcat55:nogroup catalina.out
```

I get an error saying that 'tomcat55:nogroup' : invalid user

I tried creating a user tomcat55 but that didn't help at all.  Any ideas?

Here is the output of my tomcat5.5 log:

```
Using CATALINA_BASE:   /var/lib/tomcat5.5
Using CATALINA_HOME:   /usr/share/tomcat5.5
Using CATALINA_TMPDIR: /var/lib/tomcat5.5/temp
Using JRE_HOME:       /usr/lib/jvm/java-6-sun
Using Security Manager
May 15, 2007 5:20:11 PM org.apache.catalina.core.AprLifecycleListener lifecycleEvent
INFO: The Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: /usr/lib/jvm/java- 6-sun-1.6.0.00/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/../lib/i386:/usr/java/packages/lib/i386:/lib:/usr/lib
May 15, 2007 5:20:11 PM org.apache.coyote.http11.Http11BaseProtocol init
SEVERE: Error initializing endpoint
java.net.BindException: Address already in use:8180
    at org.apache.tomcat.util.net.PoolTcpEndpoint.initEndpoint(PoolTcpEndpoint.java:297)
    at org.apache.coyote.http11.Http11BaseProtocol.init (Http11BaseProtocol.java:138)
    at org.apache.catalina.connector.Connector.initialize(Connector.java:1016)
    at org.apache.catalina.core.StandardService.initialize(StandardService.java:580)
    at org.apache.catalina.core.StandardServer.initialize (StandardServer.java:791)
    at org.apache.catalina.startup.Catalina.load(Catalina.java:503)
    at org.apache.catalina.startup.Catalina.load(Catalina.java:523)
    at sun.reflect.NativeMethodAccessorImpl.invoke0 (Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke (Method.java:597)
    at org.apache.catalina.startup.Bootstrap.load(Bootstrap.java:266)
    at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:431)
May 15, 2007 5:20:11 PM org.apache.catalina.startup.Catalina load
SEVERE: Catalina.start
LifecycleException:  Protocol handler initialization failed: java.net.BindException: Address already in use:8180
    at org.apache.catalina.connector.Connector.initialize(Connector.java :1018)
    at org.apache.catalina.core.StandardService.initialize(StandardService.java:580)
    at org.apache.catalina.core.StandardServer.initialize(StandardServer.java:791)
    at org.apache.catalina.startup.Catalina.load (Catalina.java:503)
    at org.apache.catalina.startup.Catalina.load(Catalina.java:523)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java :39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.apache.catalina.startup.Bootstrap.load(Bootstrap.java :266)
    at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:431)
May 15, 2007 5:20:11 PM org.apache.catalina.startup.Catalina load
INFO: Initialization processed in 1002 ms
May 15, 2007 5:20:11 PM org.apache.catalina.core.StandardService start
INFO: Starting service Catalina
May 15, 2007 5:20:11 PM org.apache.catalina.core.StandardEngine start
INFO: Starting Servlet Engine: Apache Tomcat/5.5
May 15, 2007 5:20:12 PM org.apache.catalina.core.StandardHost start
INFO: XML validation disabled
May 15, 2007 5:20:14 PM org.apache.catalina.startup.HostConfig deployDescriptor
WARNING: A docBase /usr/share/tomcat5.5/webapps/balancer inside the host appBase has been specified, and will be ignored
May 15, 2007 5:20:14 PM org.apache.catalina.core.ApplicationContext log
INFO: org.apache.webapp.balancer.BalancerFilter: init(): ruleChain: [org.apache.webapp.balancer.RuleChain: [org.apache.webapp.balancer.rules.URLStringMatchRule : Target string: News / Redirect URL: http://www.cnn.com], [org.apache.webapp.balancer.rules.RequestParameterRule: Target param name: paramName / Target param value: paramValue / Redirect URL: http://www.yahoo.com], [org.apache.webapp.balancer.rules.AcceptEverythingRule: Redirect URL: http://jakarta.apache.org]]
May 15, 2007 5:20:14 PM org.apache.catalina.startup.HostConfig deployDescriptor
WARNING: A docBase /usr/share/tomcat5.5/webapps/tomcat-docs inside the host appBase has been specified, and will be ignored
May 15, 2007 5:20:14 PM org.apache.catalina.startup.HostConfig deployWAR
INFO: Deploying web application archive subsonic.war
log4j:WARN No appenders could be found for logger (org.apache.commons.digester.Digester.sax).
log4j:WARN Please initialize the log4j system properly.
May 15, 2007 5:20:17 PM org.apache.catalina.core.StandardContext start
SEVERE: Error listenerStart
May 15, 2007 5:20:17 PM org.apache.catalina.core.StandardContext start
SEVERE: Context [/subsonic] startup failed due to previous errors
May 15, 2007 5:20:17 PM org.apache.catalina.core.ApplicationContext log
INFO: ContextListener: contextInitialized()
May 15, 2007 5:20:17 PM org.apache.catalina.core.ApplicationContext log
INFO: SessionListener: contextInitialized()
May 15, 2007 5:20:17 PM org.apache.catalina.core.ApplicationContext log
INFO: ContextListener: contextInitialized()
May 15, 2007 5:20:17 PM org.apache.catalina.core.ApplicationContext log
INFO: SessionListener: contextInitialized()
May 15, 2007 5:20:18 PM org.apache.coyote.http11.Http11BaseProtocol start
SEVERE: Error starting endpoint
java.net.BindException: Address already in use:8180
    at org.apache.tomcat.util.net.PoolTcpEndpoint.initEndpoint (PoolTcpEndpoint.java:297)
    at org.apache.tomcat.util.net.PoolTcpEndpoint.startEndpoint(PoolTcpEndpoint.java:312)
    at org.apache.coyote.http11.Http11BaseProtocol.start(Http11BaseProtocol.java:150)
    at org.apache.coyote.http11.Http11Protocol.start (Http11Protocol.java:75)
    at org.apache.catalina.connector.Connector.start(Connector.java:1089)
    at org.apache.catalina.core.StandardService.start(StandardService.java:459)
    at org.apache.catalina.core.StandardServer.start (StandardServer.java:709)
    at org.apache.catalina.startup.Catalina.start(Catalina.java:551)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke (NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.apache.catalina.startup.Bootstrap.start (Bootstrap.java:294)
    at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:432)
May 15, 2007 5:20:18 PM org.apache.catalina.startup.Catalina start
SEVERE: Catalina.start:
LifecycleException:  service.getName (): "Catalina";  Protocol handler start failed: java.net.BindException: Address already in use:8180
    at org.apache.catalina.connector.Connector.start(Connector.java:1096)
    at org.apache.catalina.core.StandardService.start (StandardService.java:459)
    at org.apache.catalina.core.StandardServer.start(StandardServer.java:709)
    at org.apache.catalina.startup.Catalina.start(Catalina.java:551)
    at sun.reflect.NativeMethodAccessorImpl.invoke0 (Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke (Method.java:597)
    at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:294)
    at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:432)
May 15, 2007 5:20:18 PM org.apache.catalina.startup.Catalina start
INFO: Server startup in 6278 ms
May 15, 2007 5:20:18 PM org.apache.catalina.core.StandardServer await
SEVERE: StandardServer.await: create[8005]:
java.net.BindException: Address already in use
    at java.net.PlainSocketImpl.socketBind(Native Method)
    at java.net.PlainSocketImpl.bind(PlainSocketImpl.java:359)
    at java.net.ServerSocket.bind(ServerSocket.java:319)
    at java.net.ServerSocket.<init>( ServerSocket.java:185)
    at org.apache.catalina.core.StandardServer.await(StandardServer.java:373)
    at org.apache.catalina.startup.Catalina.await(Catalina.java:615)
    at org.apache.catalina.startup.Catalina.start (Catalina.java:575)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke (DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:294)
    at org.apache.catalina.startup.Bootstrap.main (Bootstrap.java:432)
```

---

### Post by Emblem Parade on 2007-05-15
How strange! First of all, the log seems to show that there's already a version of Tomcat running on your system. Second, as for the catalina.out file, you can try to set all permissions for everybody and see if it works. (chmod a+rwx catalina.out)

Did you perhaps try to install Tomcat in a way other than using the tomcat5.5 package in the repositories? That might explain both problems.

---

### Post by mkw87 on 2007-05-16
> **Emblem Parade said:**
> How strange! First of all, the log seems to show that there's already a version of Tomcat running on your system. Second, as for the catalina.out file, you can try to set all permissions for everybody and see if it works. (chmod a+rwx catalina.out)

Did you perhaps try to install Tomcat in a way other than using the tomcat5.5 package in the repositories? That might explain both problems.

When I first installed tomcat I installed version 5 by accident not realizing I wanted 5.5.  I then removed 5 and installed 5.5.  For the record, I had it working at one point, but the program that I want tomcat to run wouldn't work (subsonic).  So I was fiddling around and broke it fairly quick trying to fix things.  I tried uninstalling all versions of tomcat, and just install 5.5 twice and it didn't work.  

So, I decided to install ampache instead of subsonic last night, got it configured but for some reason it can't access my music if it's outside my /var/www/ folder.  Soooooo I tried making a symlink to the music and putting it in my /var/www/ampache folder, that didn't work, so I threw the symlink in the trash and then when I emptied the trash it started deleted files that the symlink linked to - so I stopped touching things for the night b/c I have no good explanation of why that happened except I 'emptied' the trash from Windows via a Samba share and noticed it was taking a long time to empty the trash and saw that it was trying to delete GB of data. 

The really really odd part about that story was that it only deleted music I really didn't care about (ie: rap which I don't listen to anymore, left over from years ago).  Sorry for the rant, just thought I'd share the story.  If I can't get the folder permissions right for ampache I may try subsonic with tomcat again - but thanks for your help.

---

### Post by subnet_rx on 2007-05-23
I have tried doing this and it's just not working for me.  I fixed the config file and fixed catalina.out, but I still get the error about JAVA_HOME.  Echoing JAVA_HOME indicates it's set correctly.

---

### Post by vgillestad on 2007-05-24
I do not have this problem, but I have another one.

I want to install tomcat, and let root own and control the installation. 
But then I want to give some other users permissions to start/stop the server, and arrange it so that if they add for example a servlet file in a specific directory in their home-directory the files/projects will be deployed by tomcat.

I have heard that it can be done with sudo-scripts and by giving permissions trough visudo, but I am not sure how.

Can anybody give me some tips to how I can do this?

---

### Post by robbyc on 2007-05-30
Hi I followed you instructions and when I run 

```

sudo /etc/init.d/tomcat5.5 start

```
It tells me it has started ok, but then I try to browse to [http://127.0.0.1:8180](http://127.0.0.1:8180) and I get nothing.

I look in the catalina.out log and see the following
```

java.lang.ClassNotFoundException: org.apache.catalina.startup.Bootstrap
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at org.apache.commons.daemon.support.DaemonLoader.load(DaemonLoader.java:107)
30/05/2007 10:50:32 7166 jsvc.exec error: Cannot load daemon
30/05/2007 10:50:32 7165 jsvc.exec error: Service exit with a return value of 3

```

What does this mean?

Thanks in advance

---

### Post by kevinjones on 2007-06-06
> java.lang.ClassNotFoundException: org.apache.catalina.startup.Bootstrap

I just had this exact same problem.

For some reason (don't know why), the tomcat bootstrap files were uninstalled on my system. You need to re-install libtomcat5.5-java to re-install these files

Kevin

---

### Post by Kagoul on 2007-06-06
Hi, 

Me too I get the same problem, plus even if I set the JAVA_HOME correctly (ie ```
export JAVA_HOME=/usr/lib/jvm/java-1.6.0-sun-1.6.0.00
```) whenever I close the terminal and try to echo it, it simply not there !!!

---

### Post by Kagoul on 2007-06-07
hi, 

I tried reinstalling it , and go throughout these steps again but I get the following error 
```

$ sudo /etc/init.d/tomcat5.5 start
 * Starting Tomcat servlet engine tomcat5.5                                     07/06/2007 13:35:08 7351 jsvc error: Cannot locate Java Home
```

obviousley even if I set the JAVA_HOME as shown in tutorials the system still doesn't recognize it !!
any suggestions??
many thanx

---

### Post by soros on 2007-06-12
Hi,

I have a slightly different problem. [http://localhost:8180/](http://localhost:8180/) gives me a blank page :(

tomcat5.5 starts successfully (after applying the fix you suggested 1 & 2).
/var/log/tomcat5.5/catalina.out has no errors; except "INFO: The Apache Tomcat Native library which allows...." - this i believe is not the cause of my problem.
I have installed tomcat5.5 using Synaptic Package Manager.

Any ideas? BTW my first post in this forum ;)

thanks

---

### Post by soros on 2007-06-13
Hi,

Thanks to my work colleague Chuck I no longer get a blank page: [http://localhost:8180](http://localhost:8180). I had installed sun-java6-bin/jre but hadn't installed sun-java6-jdk. Again used Synaptic Package Manager to uninstall sun-java6-bin/jre and reinstalled sun-java6-jdk (which also installed bin & jre - novice)

Installing tomcat5.5 (Using Synaptic Package Manager):
Install sun-java6-jdk
Install tomcat5.5
Apply the fix as suggested by 'Emblem Parade' steps 1 & 2.
./tomcat5.5 start
firefox: [http://localhost:8180](http://localhost:8180) .....horray ;)

thank you all for your postings :))

---

### Post by Emblem Parade on 2007-06-13
Thanks, folk! I updated the my first post to include this important point.

---

### Post by nicolam on 2007-06-15
Hello everyone

I've tried installing tomcat using the procedure 'Emblem Parade' described, but I keep getting a blank page, even though I installed the JDK (and not just JRE ;))

...

help!

---

### Post by dupa on 2007-06-16
> **Emblem Parade said:**
> 

**2) Set Tomcat's default JAVA_HOME**

```
sudo gedit /etc/default/tomcat5.5
```

Uncomment the JAVA_HOME line and set it to your JDK path. For Java 6 installed from the repositories, it's as so:

```
JAVA_HOME=/usr/lib/jvm/java-6-sun
```



What is /etc/default/tomcat5.5 ?
When is it loaded?

I have looked into the file /etc/inid.d/tomcat55 and I have seen that he has inside a script to search for the JAVA_HOME and set correctly it.

For which reason do you edit  /etc/default/tomcat5.5 ? thanks

---

### Post by mnk0 on 2007-06-24
hmm i still getting tha tblank page [http://localhost:8180/](http://localhost:8180/) -- can't figure out what was missing from that walk thorugh that was posted.

---

### Post by arturodr on 2007-06-26
Have you tried going to [http://localhost:8180/admin/]("http://localhost:8180/admin/") ?

also if you install tomcat5.5-webapps you'll get the welcome page.

---

### Post by nicolam on 2007-06-27
> **arturodr said:**
> Have you tried going to [http://localhost:8180/admin/]("http://localhost:8180/admin/") ?

also if you install tomcat5.5-webapps you'll get the welcome page.

thanks :)

that solved the problem! :D

---

### Post by peppy.ch on 2007-08-24
Hooray! tomcat up and running  \\:D/
thanks

---

### Post by tiendn on 2007-08-25
Hey guys!!!
 I installed tomcat5.5 and sun-java-6 but I can't use tomcat server, and this is my problem:
 + I start tomcat with command :
   $/etc/init.d/tomcat5.5 start
 and I got :"Starting Tomcat 5 servlet engine using Java from /usr/lib/jvm/java-6-sun/jre/: tomcat5.5"
 + but  I can't start tomcat server from web browse (firefox)
 + I checked and process catalina.sh is running
 + I try stop tomcat : "/etc/init.d/tomcat5.5 stop" and I got :"Stopping Tomcat 5 servlet engine: (not running)"
 I can't  understand my problem, can you tell me...
                                              thanks!!!

---

### Post by tiendn on 2007-08-25
Hey!
I found my JAVA_HOME problem, and I fixed it by adding :
+ open file /etc/init.d/tomcat5.5
+ add this: "/usr/lib/jvm/java-6-sun" into JAVA_HOME
(I am using java 6 and ubuntu 6.10)

---

### Post by dbuschho on 2007-11-14
Hello,

I have a slight problem with the repo. install of tomcat5.5 .  I have installed tomcat,admin,webapp from the repository.  I then copy my cocoon build-webapp directory into 
/usr/share/tomcat5.5/webapps
and rename it cocoon.

Once this is done, tomcat seems to run fine, cocoon too, however when I attempt to follow a symbolic link in the cocoon directory, I get the message:
java.io.FileNotFoundException: /var/lib/tomcat5.5/webapps/cocoon/output2/sitemap.xmap (Permission denied)

If I copy the files at the terminus of the symbolic link to cocoon, the files behave as expected.

I have tried adding the '<context allowLink='true'>' attribute to /conf/context.xml but with no luck.  (I also have set the TOMCAT55_SECURITY=no).

I could just always work with my  files within the tree of /usr/share/tomcat5.5/webapps, but this setup worked from a manual install of tomcat5 and I'd just prefer not to keep moving my files around.

If someone could give me a tip on why/how tomcat 5.5 wouldnt follow a symbolic link outside its CATALINA directory or if Im being stupid about cocoon, please let me know,

Thanks,
Drew.

---

### Post by sgordon on 2007-11-18
Just a very quick thought before looking at this more closely. The error above is:
java.io.FileNotFoundException: /var/lib/tomcat5.5/webapps/cocoon/output2/sitemap. xmap (Permission denied)

note the space between 'sitemap' and '.xmap'

Is this a paste error from your terminal or is that actually how it is logged? If it's how the log shows it, I'd be suspicious of that!

  Si

---

### Post by sgordon on 2007-11-18
A further thought...

the attribute is

allowLinking="true"

(not allowLink)

as per [http://tomcat.apache.org/tomcat-5.5-doc/config/context.html](http://tomcat.apache.org/tomcat-5.5-doc/config/context.html)

Perhaps that's just a typo as you have entered the post and we can ignore, good to check though.

Anyhow, what do you think?

  Si

---

### Post by dbuschho on 2007-11-18
Yup, thanks for the ideas, but both are from my sloppyness posting, not errors in conf.

I'm sort of at a loss for what it could be, at this point Ive just moved my project directory into tomcat's path (/usr/share/tomcat5.5/webapps/) which 'fixes' the problem.

If you think of any other suggestions I'd be happy to hear them.

Thanks,
Drew.

---

### Post by sgordon on 2007-11-18
Hi there.

Ok, I just installed Tomcat 5.5 and JDK 1.6

I created a symbolic link into my home folder straight off and it works, no config change needed at all.

Just FYI, not trying to wind you up or anything!

Hm, wonder what it could be? File permissions on the link or destination file?
Note, I've been using /usr/share/tomcat5.5-webapps/ for my web applications and for the above test.

Just some extra info for you to try some options.

  Si

---

### Post by dbuschho on 2007-11-18
Thanks for all the help,

You doing that install actually helped a lot, now I know it's an error on my end, not some weird repository thing.  Which I should have assumed but it was working...anyway.

I tried making symbolic links in both the tomcat5.5-webapp/ and the tomcat5.5/webapps/ directories with no luck, permissions for both were tried at 775, and both root:root & tomcat55:nobody.

I also tried explicitly allowing 'follow symlink' in apache2's site specific configuration for the webapp directory and the /var/lib/ directory referenced in the error message. No luck.

In any case, it looks to be a configuration error on my end, not too surprising since Im inexperienced I suppose.  I can get the app to run, just not exactly where I want it, so I think I'll just let this go until I feel like reinstalling the whole stack.

Thanks for the help,
Drew.

---

### Post by chokas on 2008-02-05
THANK YOU !!! without the catalina fix some jsp's act strange

---

### Post by chokas on 2008-02-05
Does anybody know if it's possible to run php5 with Tomcat5.5 ??

I would like to know if its possible to do it, i've downloaded some packages from the repositories.

libapache2-mod-php5 
php5-cgi
php5-cli
php5-common

It runs well using apache2 but I'd like to know if there's a way to make it run as a normal tomcat 5.5 application... thank you.

---

### Post by AndrewTheArt on 2008-06-01
Chokas: No, not as far as I know, but you can check out my guide where I combine Apache and Tomcat using a module - 

[http://compsci.treycarroll.com/ubuntu_guide](http://compsci.treycarroll.com/ubuntu_guide)

Also, is the tomcat log file issue still a problem? I integrated your steps into my guide but I don't know if fixing the logfile is even necessary at this point.

---

### Post by AndrewTheArt on 2008-06-01
> **AndrewTheArt said:**
> Chokas: No, not as far as I know, but you can check out my guide where I combine Apache and Tomcat using a module - 

[http://compsci.treycarroll.com/ubuntu_guide](http://compsci.treycarroll.com/ubuntu_guide)

Also, is the tomcat log file issue still a problem? I integrated your steps into my guide but I don't know if fixing the logfile is even necessary at this point.

I determined that the logfile problem is now longer an issue in anything past Feisty (so Gusty/Hardy are OK, etc). However, it's still a a good idea to fix the JDK problem (although not necessarily critical)

---

### Post by tengil on 2008-06-19
I just tried installing tomcat5.5 and tomcat5.5-webapps. Everything seemed fine, I got the welcome page on port 8180. Then I moved the /usr/share/tomcat5.5-webapps directory to another partition and created a symlink to patch it up. I then got a blank page instead of the welcome page...

Whatever I try to do now (moving the directory back, reinstalling tomcat, etc) I always just get a blank page. No 404 errors for non-existing urls, no /admin (tomcat5.5-admin is installed), and nothing in the logs.

Ubuntu is 8.04. Java is sun 6.

Grateful for any help.

---

