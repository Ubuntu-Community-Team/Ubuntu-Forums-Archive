---
title: "Tomcat"
date: 2005-04-01
forum: Repositories &amp; Backports
---

### Post by thoms on 2005-04-01
Want to install tomcat but it's not in the repositories, any suggestions?

---

### Post by bihe on 2005-04-01
[QUOTE=thoms]Want to install tomcat but it's not in the repositories, any suggestions?[/QUOTE]

you just need to install the j2sdk [http://ubuntuguide.org/index.html#jre](http://ubuntuguide.org/index.html#jre) 
then download tomcat from [http://jakarta.apache.org/tomcat/index.html](http://jakarta.apache.org/tomcat/index.html) 
untar it somewhere (/usr/local/tomcat, ...) 
goto $TOMCAT_HOME/bin and run startup.sh

---

### Post by thoms on 2005-04-02
Thanks, done that, when I run the binary, I get:

Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program

---

### Post by bihe on 2005-04-02
[QUOTE=thoms]...Neither the JAVA_HOME nor the JRE_HOME environment variable is defined...
[/QUOTE]

do so:

in bash: export JAVA_HOME=/path_to_j2sdk 
(e.g. export JAVA_HOME=/usr/local/java/j2sdk)

this only works in the current console. to make a permanent entry open ~/.bashrc or
~/.bash_profile and add the entry 'export JAVA_HOME=/path_to_j2sdk '

after that logout/login and check if the value is set. open a shell,
echo $JAVA_HOME 
if the path is displayed correctly, tomcat should work ;)

---

### Post by thoms on 2005-04-02
[QUOTE=bihe]do so:

in bash: export JAVA_HOME=/path_to_j2sdk 
(e.g. export JAVA_HOME=/usr/local/java/j2sdk)

this only works in the current console. to make a permanent entry open ~/.bashrc or
~/.bash_profile and add the entry 'export JAVA_HOME=/path_to_j2sdk '

after that logout/login and check if the value is set. open a shell,
echo $JAVA_HOME 
if the path is displayed correctly, tomcat should work ;)[/QUOTE]
 Now I get:

Using CATALINA_BASE:   /usr/local/jakarta-tomcat-5.5.9
Using CATALINA_HOME:   /usr/local/jakarta-tomcat-5.5.9
Using CATALINA_TMPDIR: /usr/local/jakarta-tomcat-5.5.9/temp
Using JRE_HOME:       /usr/lib/j2sdk1.5-sun/

---

### Post by bihe on 2005-04-03
[QUOTE=thoms]Now I get:

Using CATALINA_BASE:   /usr/local/jakarta-tomcat-5.5.9
Using CATALINA_HOME:   /usr/local/jakarta-tomcat-5.5.9
Using CATALINA_TMPDIR: /usr/local/jakarta-tomcat-5.5.9/temp
Using JRE_HOME:       /usr/lib/j2sdk1.5-sun/[/QUOTE]

yep, this is the desired output. tomcat listens on :8080

---

### Post by refux on 2005-04-16
Just want to say I found this thread very useful.
I just have one slight problem, its to do with permissions.

I changed the owner of tomcat to root and then I try running it by:
sudo startup.sh

However tomcat doesn't have permissing to create the log dir....
touch: cannot touch `/usr/java/jakarta-tomcat-5.5.9/logs/catalina.out': No such file or directory

I tried a chmod -R a=rwx jakarta-tomcat-5.5.9
And everything runs fine.
However I'd rather now leave it wide open like that.

Any help much appreciated!

---

### Post by RastaMahata on 2005-04-17
maybe this should be posted as a howto

---

### Post by Urusai on 2005-04-18
WTH is Tomcat logging to /usr and not /var ??

---

### Post by bihe on 2005-04-18
the log path is defined in $CATALINA_HOME/bin/catalina.sh
```
... >> "$CATALINA_BASE"/logs/catalina.out 2>&1
```

---

### Post by nortoncillo on 2005-05-02
i've read this thread...
done what you have said to do...

but...

tomcat still wont work in my ubuntu...

i get the 
Using CATALINA_BASE:   /usr/java/jakarta-tomcat-5.5.9
Using CATALINA_HOME:   /usr/java/jakarta-tomcat-5.5.9
Using CATALINA_TMPDIR: /usr/java/jakarta-tomcat-5.5.9/temp
Using JRE_HOME:       usr/lib/j2sdk1.4.2/

then go to  [http://myadress.mydomain:8080](http://myadress.mydomain:8080)

and nothing.... :neutral:

---

### Post by bihe on 2005-05-03
henrik@aragorn:~/jakarta-tomcat-5.0.28/bin$ ./startup.sh

Using CATALINA_BASE:   /home/henrik/jakarta-tomcat-5.0.28
Using CATALINA_HOME:   /home/henrik/jakarta-tomcat-5.0.28
Using CATALINA_TMPDIR: /home/henrik/jakarta-tomcat-5.0.28/temp
Using JAVA_HOME:       /usr/java/jdk1.5.0_01

--> goto [http://localhost:8080/](http://localhost:8080/)
and there it is ... the tomcat startpage

for errors goto %CATALINA_HOME%/logs 

the listener configuration ist done in %CATALINA_HOME%/conf/server.xml

default is a http 1.1 listener at 8080. check if tomcat is listening on port
8080.

henrik@aragorn:~/jakarta-tomcat-5.0.28/bin$ netstat -an | grep 8080
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN

---

### Post by goofrider on 2005-05-06
[QUOTE=nortoncillo]i've read this thread...
done what you have said to do...

but...

tomcat still wont work in my ubuntu...

i get the 
Using CATALINA_BASE:   /usr/java/jakarta-tomcat-5.5.9
Using CATALINA_HOME:   /usr/java/jakarta-tomcat-5.5.9
Using CATALINA_TMPDIR: /usr/java/jakarta-tomcat-5.5.9/temp
Using JRE_HOME:       usr/lib/j2sdk1.4.2/

then go to  [http://myadress.mydomain:8080](http://myadress.mydomain:8080)

and nothing.... :neutral:[/QUOTE]


If you're using the full JDK (as your path /usr/lib/j2sdk-1.4.2/ indicates), you should set **JAVA_HOME**=/usr/lib/j2sdk-1.4.2/, rathan than JRE_HOME.


Also, IIRC, Tomcat 5.5.x requires JDK 1.5.0+, so you either need to downgrade to Tomcat 5.0.x or install the *sun-j2sdk1.5* package: you can apt-get sun's JDK 1.5.0  from Hoary Backport (it was there last time I looked. It's a breach of Sun's license to redistribute it though so don't count on it being there forever) or make your own using the "*java-package*" package.

---

### Post by goofrider on 2005-05-06
Oh maybe I should add that I think it's pretty important that Ubuntu supplies Java server/devtool packages. Sun's licensing issue has been beaten to death so I won't repeat it here. Though it's pretty ridiculous that we have to go through all this trouble just to get Tomcat running.

---

### Post by mtrompeta on 2005-06-17
Hello, noob here.  Been searching google, fedora forums, gentoo forums, everywhere for answers but couldn't find any.

Anyways, have Ubuntu Hoary installed.  Apache2, Java SDK 1.5, PHP, MySQL, all successfully installed.  Configured my environment JAVA_HOME in /etc/environment.  Dl'd the Tomcat binaries, unzipped to /usr/local/bin/jakarta... configured the env var CATALINA_HOME in /etc/environment.  Was able to startup Tomcat successfully by running:
```

# sudo $CATALINA_HOME/bin/startup.sh
Using CATALINA_BASE:   /usr/local/bin/tomcat
Using CATALINA_HOME:   /usr/local/bin/tomcat
Using CATALINA_TMPDIR:   /usr/local/bin/temp
Using JRE_HOME:   /usr/lib/j2sdk1.5-sun/bin/java

```

But when I try to connect to [http://localhost:8080/](http://localhost:8080/) in Firefox, I get the message

***The connection was refused when attempting to contact localhost:8080.***

I don't know if it's my server.xml file, because in the fedora forums ([http://forums.fedoraforum.org/showthread.php?t=20030](http://forums.fedoraforum.org/showthread.php?t=20030)) someone suggested that it was not configured to respond to browsers.  I don't know how or where to check for that, but I highly doubt that's the problem, especially since I'm using the binaries straigh from [http://jakarta.apache.org/site/downloads/downloads_tomcat-5.cgi](http://jakarta.apache.org/site/downloads/downloads_tomcat-5.cgi).

I'm out of ideas of how to get Tomcat started (even tried stopping apache and just running tomcat alone) so any help would be appreciated.

Thanks.

---

### Post by bihe on 2005-06-20
if tomcat runs - does tomcat listen?
> henrik@aragorn:~/jakarta-tomcat-5.0.28/bin$ netstat -an | grep 8080
> tcp 0 0 0.0.0.0:8080 0.0.0.0:* LISTEN

are there any errors in the tomcat logs or in /var/log/messages
> for errors goto $CATALINA_HOME/logs

---

### Post by noodle on 2005-07-19
This might be a bit late, but I wrote a [HOWTO](http://www.ubuntuforums.org/showthread.php?p=226828#post226828)  on installing tomcat.

 ;-)

---

### Post by theQmaster on 2005-07-31
Anyone succesfulyl started  tomcat with jsvc as a service in behalf of a low privilegde user ? That would be the way to go...

---

### Post by bmuni on 2006-02-18
I am also experiencing the same issues. I am trying to switch tomcat to run on port 80. So the non-SSL entry in the server.xml file on my server was switched to 80 instead of 8080. When I run [http://localhost/](http://localhost/), I get the "The connection was refused when attempting to contact localhost".  It will work on port 8080, but not 80.   Hmmmm ....kinda confusing  :confused:  . I have done this so many times in the past and it has worked before.  Must be a port mapping problem of some sort.  I am on an amd 64 machine with breezy 5.10. Any luck out there! The only thing I can think of is if my DSL gateway router is doing something strange. Does running this on DHCP as compared to giving my machine a static ip affect the server? I don't really know. I might experiment further and get back. But any feedback at this point would be greatly appreciated.

thanks beau

---

### Post by bihe on 2006-02-18
only privileged user are "allowed" to open ports below 1024.
[google]("http://www.google.com/search?q=privileged+ports&start=0")

---

### Post by rock_pec on 2006-02-20
To run tomcat on port 80, the ideal way is to integrate it with apache. dont ask me how coz i am still stuck with it.

:)

---

### Post by pmasiar on 2006-12-19
answer posted: [https://help.ubuntu.com/community/EclipseWebTools](https://help.ubuntu.com/community/EclipseWebTools)

---

### Post by pafortin on 2007-01-07
Most of the examples show to use [http://localhost:8080/](http://localhost:8080/) to get the Tomcat home page but that did not work for me I had to use: [http://192.168.0.102:8080/](http://192.168.0.102:8080/) which is the IP given by DHCP to my Ubuntu box.

Hope this helps as well!!!

Paul

---

