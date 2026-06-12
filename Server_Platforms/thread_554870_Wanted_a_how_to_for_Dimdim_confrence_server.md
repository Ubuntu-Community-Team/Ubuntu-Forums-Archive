---
title: "Wanted: a how to for Dimdim confrence server"
date: 2007-09-19
forum: Server Platforms
---

### Post by amoore on 2007-09-19
[Dimdim]("http://www.dimdim.com/")  is the Open Source web conferencing company. With Dimdim you can show Presentations, Applications and Desktops to any other person over the internet. You can chat, show your webcam and talk with others in the meeting.   

Dimdim requires a sever set up. I have a Xubutnu 7.04 LAMP server but, I would like to find some instructions for installing Dimdim on a Ubuntu server. I believe that Dimdim also needs Tomcat as well.  

Does anyone knows about a Dimdim server how to  for Ubuntu?

---

### Post by amoore on 2008-03-11
installing dimdim on ubuntu linux: From [http://www.subvs.co.uk/install_dimdim_on_ubuntu](http://www.subvs.co.uk/install_dimdim_on_ubuntu)

Dimdim is a cool new open source meeting service that lets you share your desktop, presentations, audio and video. Its also web based, and needs no installing. On top of all this, it works on Mac, Linux and even Windows! Its still alpha at the moment, but definately useable. Heres how to install it on Ubuntu server 6.06 or {insert your distro here}. The readme that comes with the tarball is very good, so have a look at that as well, but here are the basics:


Install Ubuntu base system

Just boot the ubuntu server cd and choose INSTALL TO HARD DISK. 
Install java
```

sudo aptitude install sun-java5-jre
```

Download dimdim from [http://sourceforge.net/project/showfiles.php?group_id=176809](http://sourceforge.net/project/showfiles.php?group_id=176809) and move it to /usr/local/dimdim 
```

tar zxvf dimdim_160_Alpha_080307.tar.gz 
```The version number is likely to be different
```
sudo mv dimdim /usr/local/
```
Configure dimdim

```
cd /usr/local/dimdim
```
Edit server.xml 

```
vi server.xml
```

Edit the port definition, 80 is probably the easiest, but change it to taste

 ```
<!-- Define a non-SSL HTTP/1.1 Connector on port 8080 -->
    <Connector port="DIMDIM_PORT_NUMBER" maxHttpHeaderSize="8192"
               maxThreads="1500" minSpareThreads="250" maxSpareThreads="750"
               enableLookups="false" redirectPort="8443" acceptCount="100"
               connectionTimeout="20000" disableUploadTimeout="true" />
    <!-- Note : To disable connection timeouts, set connectionTimeout value
     to 0 -->

```
Change to

 ```
<!-- Define a non-SSL HTTP/1.1 Connector on port 8080 -->
    <Connector port="80" maxHttpHeaderSize="8192"
               maxThreads="1500" minSpareThreads="250" maxSpareThreads="750"
               enableLookups="false" redirectPort="8443" acceptCount="100"
               connectionTimeout="20000" disableUploadTimeout="true" />
    <!-- Note : To disable connection timeouts, set connectionTimeout value
     to 0 -->
```

Edit dimdim.properties 

Edit the following parameters:

```
vi dimdim.properties 
```

```
dimdim.serverAddress # should be your server url, ie dimdim.mydomain.com
dimdim.serverPortNumber=80 # change if you use a different port
```

and lastly the email config 

```
email.server=<smtp server address> 
email.user=<smtp user name>
email.password=<smtp user password>
email.sender=<full email address of the above user> 
email.PORT=<smtp port number>

```

Now edit the wrapper.conf for the java path:

```
vi ConferenceServer/apache-tomcat-5.5.17/conf/wrapper.conf
```

```
 # Java Application
#wrapper.java.command=DIMDIM_JAVA_HOME/bin/java
wrapper.java.command=/usr/bin/java # add this line for ubuntu, or change according to where java is on your system
```

All done, now just start the beast

```
sudo /usr/local/dimdim/dimdim start
```

If that all works, you can now go to [http://your.server.address](http://your.server.address) and start using dimdim
Add service links

dimdim comes with a service wrapper, which makes it pretty easy to put into your *nix system. First we add a soft link to /etc/init.d/, then make sure it starts up when the server reboots. 

```
sudo ln -s /usr/local/dimdim/ConferenceServer/apache-tomcat-5.5.17/bin/dimdim /etc/init.d/
```
```
sudo update-rc.d dimdim defaults
Restrict presenter access
```

You may want to restrict the users that can start a presentation. At the moment, there is a very basic way to do this:

Edit  /usr/local/dimdim/ConferenceServer/apache-tomcat-5.5.17/webapps/dimdim/WEB-INF/dimdimPresenters.txt and add the email addresses allowed to start a presentation. No, theres no authentication.

Edit  /usr/local/dimdim/dimdim.properties and set dimdim.authenticationPolicy=CHECK_EMAIL

Restart dimdim 

Obviously this is not an ideal way to restrict it, but it seems to be being worked on.

---

