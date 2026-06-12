---
title: "tomcat 5.5 loads a blank page"
date: 2008-06-23
forum: Server Platforms
---

### Post by cuco2772 on 2008-06-23
Hi,
I have vexing problem with tomcat5.5 installed from the repos that I'm
unable to get anywhere on.
I run tomcat using the startup script, for ex. /usr/share/tomcat5.5/bin startup.sh and everything startsup with no errors, ie:

Using CATALINA_BASE:   /usr/share/tomcat5.5
Using CATALINA_HOME:   /usr/share/tomcat5.5
Using CATALINA_TMPDIR: /usr/share/tomcat5.5/temp
Using JRE_HOME:       /usr/lib/jvm/java-6-sun

but if I go to localhost:8180 a blank page is displayed with no errors in catalina.out.
Here's the output from catalina.out when I startup tomcat as above:

root@coati:~# tail -f /usr/share/tomcat5.5/logs/catalina.out
Jun 23, 2008 5:56:50 PM org.apache.coyote.http11.Http11BaseProtocol start
INFO: Starting Coyote HTTP/1.1 on http-8180
Jun 23, 2008 5:56:50 PM org.apache.jk.common.ChannelSocket init
INFO: JK: ajp13 listening on /0.0.0.0:8009
Jun 23, 2008 5:56:50 PM org.apache.jk.server.JkMain start
INFO: Jk running ID=0 time=0/58  config=null
Jun 23, 2008 5:56:50 PM org.apache.catalina.storeconfig.StoreLoader load
INFO: Find registry server-registry.xml at classpath resource
Jun 23, 2008 5:56:50 PM org.apache.catalina.startup.Catalina start
INFO: Server startup in 599 ms

As I said I get the blank page when going to localhost:8180, and nothing added to catalina.out, so no help in figuring this problem out.

As a comparison, I get the normal index.html page displayed when I go to /usr/local/tomcat/apache-tomcat-6.0.14/bin and run the startup script there
and go to localhost:8080. (i have both tomcats installed. I'll explain more on this later)
I did a search and there is actually no index.html page in my tomcat5.5 installation. I installed this version from the ubuntu(gutsy)  repositories using apt-get.
The /usr/share/tomcat5.5/webapps directory is empty there whereas the other, /usr/local/tomcat/apache-tomcat-6.0.14/webapps/ROOT/index.html, isn't.
Not sure this matters, though.
It seems like the home directories for the 2 tomcat installations are set up a bit differently:

root@coati:~# ls /usr/share/tomcat5.5/
bin  common  conf  doc  logs  server  shared  temp  webapps  work

versus

root@coati:~# ls /usr/local/tomcat/apache-tomcat-6.0.14
bin   lib      logs    RELEASE-NOTES  temp     work
conf  LICENSE  NOTICE  RUNNING.txt    webapps

Now to the reason I'm using tomcat5.5 instead of the latest version.  I'm trying to do web development using eclipse. I had to install eclipse using apt-get also.
(After a week of trying to get the latest version of eclipse working from a manual download, I gave up)
So I have eclipse 3.2.2 WTP with tomcat5.5 and I have a sample webapp that I did using an eclipse tutorial, and everything seems to work,
 I can start tomcat server from eclipse with no errors, but the same thing happens. When I go to load the jsp it's blank.
I am totally clueless on this one, so any ideas would be greatly appreciated. Thanks,

                                                                                                                                  Adam Posner

---

### Post by praxis1949 on 2008-12-06
Don't know about the repo version, but the none-ubuntu version loads from the /usr/share/tomcat6/webapps directory", and if it aient't there, you aien't loading.

If I were you, I would do a clean install from an  Apache-Tomcat downlaod. The Ubuntu version loads  three or four different versions of various Tomcat files, causing inordinate confusion (in my opinion). I have a Apache-Tomcat version that is running fine.

Regards

John S

---

### Post by praxis1949 on 2008-12-06
Correction: The Ubuntu version works with an available "plug in" (via "Tools>plugin" Wotrth strolling through the forum. To install Tomcat from Apache-Tomcat, I recommend the followuing instructions

[URL="http://ubuntuforums.org/showthread.php?t=420034"]

http://ubuntuforums.org/showthread.php?t=420034 [/URL]

---

### Post by praxis1949 on 2008-12-06
A last point: Check out the "Properties">> "Permissions" on you Tomcat directories (use "Nautilus"). Just had a fight with Ubuntu's version of Netbeans because my Tomcat directories were owned by "root". and were not even visible to  external applications (i.e. Netbeans). Netbeans kept claiming that a key file to mount the Tomcat server, "server.xml", was "corrupted".  You could be fighting "Permissions" - related problems (some files are not even visible without the right permissions).

Permissions are the toughest part of Linux applications for us ex-Windows people.

John S

---

