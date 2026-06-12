---
title: "SSL Explorer Setup?"
date: 2006-11-08
forum: Server Platforms
---

### Post by sysop on 2006-11-08
Anyone have any experience setting up [SSL-Explorer]("http://sourceforge.net/projects/sslexplorer/") on Ubuntu Server (6.06 or newer)? :confused: 

Did it work and what were the steps involved to setup? Thanks to anyone with information.

---

### Post by DugieHowsa on 2007-09-26
They just released a new linux gui install.  It worked perfectly me for me on 7.04.  I had issues previously installing from source.

[http://sourceforge.net/project/showfiles.php?group_id=116065&package_id=125980](http://sourceforge.net/project/showfiles.php?group_id=116065&package_id=125980)

sslexplorer_linux_gui_1_0_0_RC1.zip

---

### Post by stinger30au on 2008-02-29
im having some dramas makeing this run and im sure its all my fault.

i went here
[http://sourceforge.net/project/showfiles.php?group_id=116065&package_id=125980](http://sourceforge.net/project/showfiles.php?group_id=116065&package_id=125980)

and i d/l this file
[http://downloads.sourceforge.net/sslexplorer/sslexplorer_linux_rpm_1_0_0_RC16.zip?modtime=1203624945&big_mirror=0](http://downloads.sourceforge.net/sslexplorer/sslexplorer_linux_rpm_1_0_0_RC16.zip?modtime=1203624945&big_mirror=0)

i have saved the file on one of my spare hard drives and extracted the file.

i started up shell and went in to the directory.
to be sure i could run the file i ran chmod inside the directory like this

 sudo chmod 777 -R *.*

and to save typing i renamed the file to 
sslexplorer_linux.sh

to start the program i typed in to shell

sudo ./sslexplorer_linux.sh


and i get this error
Starting Installer ...
java.lang.NoClassDefFoundError: javax.swing.JOptionPane
   at java.lang.Class.initializeClass(libgcj.so.81)
   at com.install4j.runtime.installer.Installer.reportExeption(Unknown Source)
   at com.install4j.runtime.installer.Installer.main(Unknown Source)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at com.exe4j.runtime.LauncherEngine.launch(Unknown Source)
   at com.install4j.runtime.Launcher.main(Unknown Source)



What have i done wrong???
Thanks

---

### Post by twistedneck on 2008-07-11
I too am having ssl explorer issues. :mad: i did make it past the install thank god..  however i just can't seem to get ant and sslexplorer running.

i've got the setup program configured for port 61000 and my router is also forwarding that port to my static ip.

followed these steps..

[http://www.debian-administration.org/users/jhabib/weblog/1](http://www.debian-administration.org/users/jhabib/weblog/1)

and

[http://smesmith.de/download/Howtos/howto-ssl-explorer.html](http://smesmith.de/download/Howtos/howto-ssl-explorer.html)

the web page installer seemed to work great

placed the extracted sslexplorer files in this path - it recommends 'opt' directory in the readme.

twistedneck@twistedubuntu-garage:/opt/sslexplorer-1.0.0_RC17/

Here is my wrapper.conf file 

(the #java application path is correct) - and i did a fresh install of java.

i've ran 'sudo ant run' and it says "build successfull" 

however i can't see ant or sslexplorer running in ps ax or top.

i also tried adding it as a service and it doesn't seem to start.

finally, when i try testing ssl explorer locally by going to addresss

[https://192.168.1.4:61000/](https://192.168.1.4:61000/) or [https://twistedubuntu-garage:61000/](https://twistedubuntu-garage:61000/) it has a page load error so either apache or sslexplorer or both are not running..  :confused:

btw, here is the error i get trying to start the service

twistedneck@twistedubuntu-garage:/opt/sslexplorer-1.0.0_RC17$ sudo /etc/init.d/sslexplorer start
Starting SSL-Explorer...
exec: 370: /opt/sslexplorer-1.0.0_RC17/sslexplorer/install/platforms/linux/x86/wrapper: Permission denied


```
#********************************************************************
# SSL-Explorer wrapper configuration
#********************************************************************

# Java Application
wrapper.java.command=/usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/bin/java

# Java Main class.
wrapper.java.mainclass=com.sslexplorer.boot.Bootstrap

# Java Classpath.
#
# THIS PROPERTY SHOULD NOT BE CHANGED. ANY CHANGES TO
# THE CLASSPATH SHOULD BE DONE THROUGH THE classpath.properties
# FILE THAT ALSO EXISTS IN THIS DIRECTORY

wrapper.java.classpath.1=build/boot
wrapper.java.classpath.2=lib/sslexplorer-boot.jar

# Jetty Paranoid setting
wrapper.java.additional.1=-Dorg.mortbay.http.Version.paranoid=true

# Java Library Path
# wrapper.java.library.path.1=lib

# Java Additional Parameters
#wrapper.java.additional.1=

# Initial Java Heap Size (in MB)
wrapper.java.initmemory=64

# Maximum Java Heap Size (in MB)
wrapper.java.maxmemory=512

# Application parameters.  Add parameters as needed starting from 1
#wrapper.app.parameter.1=

#********************************************************************
# Wrapper Logging Properties
#********************************************************************
# Format of output for the console.  (See docs for formats)
wrapper.console.format=PM

# Log Level for console output.  (See docs for log levels)
wrapper.console.loglevel=INFO

# Log file to use for wrapper output logging.
wrapper.logfile=logs/wrapper.log

# Format of output for the log file.  (See docs for formats)
wrapper.logfile.format=LPTM

# Log Level for log file output.  (See docs for log levels)
wrapper.logfile.loglevel=INFO

# Maximum size that the log file will be allowed to grow to before
#  the log is rolled. Size is specified in bytes.  The default value
#  of 0, disables log rolling.  May abbreviate with the 'k' (kb) or
#  'm' (mb) suffix.  For example: 10m = 10 megabytes.
wrapper.logfile.maxsize=0

# Maximum number of rolled log files which will be allowed before old
#  files are deleted.  The default value of 0 implies no limit.
wrapper.logfile.maxfiles=0

# Log Level for sys/event log output.  (See docs for log levels)
wrapper.syslog.loglevel=NONE

#********************************************************************
# Wrapper Windows Properties
#********************************************************************
# Title to use when running as a console
wrapper.console.title=SSL-Explorer

#********************************************************************
# Wrapper Windows NT/2000/XP Service Properties
#********************************************************************
# WARNING - Do not modify any of these properties when an application
#  using this configuration file has been installed as a service.
#  Please uninstall the service before modifying this section.  The
#  service can then be reinstalled.

# Name of the service
wrapper.ntservice.name=SSL-Explorer

# Display name of the service
wrapper.ntservice.displayname=SSL-Explorer

# Description of the service
wrapper.ntservice.description=SSL-Explorer SSL VPN

# Service dependencies.  Add dependencies as needed starting from 1
wrapper.ntservice.dependency.1=

# Mode in which the service is installed.  AUTO_START or DEMAND_START
wrapper.ntservice.starttype=AUTO_START

# Allow the service to interact with the desktop.
wrapper.ntservice.interactive=false

wrapper.working.dir=/opt/sslexplorer-1.0.0_RC17/sslexplorer
wrapper.java.library.path.1=/opt/sslexplorer-1.0.0_RC17/sslexplorer/install/platforms/linux/x86
```

---

### Post by twistedneck on 2008-07-11
> **stinger30au said:**
> im having some dramas makeing this run and im sure its all my fault.

i went here
[http://sourceforge.net/project/showfiles.php?group_id=116065&package_id=125980](http://sourceforge.net/project/showfiles.php?group_id=116065&package_id=125980)

and i d/l this file
[http://downloads.sourceforge.net/sslexplorer/sslexplorer_linux_rpm_1_0_0_RC16.zip?modtime=1203624945&big_mirror=0](http://downloads.sourceforge.net/sslexplorer/sslexplorer_linux_rpm_1_0_0_RC16.zip?modtime=1203624945&big_mirror=0)

i have saved the file on one of my spare hard drives and extracted the file.

i started up shell and went in to the directory.
to be sure i could run the file i ran chmod inside the directory like this

 sudo chmod 777 -R *.*

and to save typing i renamed the file to 
sslexplorer_linux.sh

to start the program i typed in to shell

sudo ./sslexplorer_linux.sh


and i get this error
Starting Installer ...
java.lang.NoClassDefFoundError: javax.swing.JOptionPane
   at java.lang.Class.initializeClass(libgcj.so.81)
   at com.install4j.runtime.installer.Installer.reportExeption(Unknown Source)
   at com.install4j.runtime.installer.Installer.main(Unknown Source)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at com.exe4j.runtime.LauncherEngine.launch(Unknown Source)
   at com.install4j.runtime.Launcher.main(Unknown Source)



What have i done wrong???
Thanks

did you install apache ant?  i realize this might be a trivial thing to some, but it was new to me.  i installed it via synaptec 'ant'

then just type 'ant install' from the sslexplorer directory.  the same directory you extracted the install file to.   then it runs and tells you what ip address to paste into explorer to finish up the config.  w/o ant and java installed, none of it works.

although, i get through the install just fine and i can't seem to get ant or sslexplorer even running!  :(

---

### Post by twistedneck on 2008-07-11
OK, another update.

i fixed the sslexplorer permission error by doing chmod 777 to that directory. now sslexplorer will start.  

HOWEVER,  i didn't even have apache installed.  i installed it in synaptec, along with the other files it needed.  i tried to run it and now get this error

"twistedneck@twistedubuntu-garage:/etc$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                  (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]"

then i did a netstat to find out what was running on port 80

"twistedneck@twistedubuntu-garage:/etc/apache2$ sudo netstat -lnp | grep '80'
tcp6       0      0 :::61000                :::*                    LISTEN      4880/java       
tcp6       0      0 :::80                   :::*                    LISTEN      4880/java  "

ok, turns out it shows port 80 is using 4880/java - what ever that means.  fyi port 61000 above is what i configured in sslexplorer install utility. strange.

I think once i can get apache2 started, since i can start sslexplorer fine it should work!

thank you all.

---

### Post by twistedneck on 2008-07-12
the reason i had a port conflict is becuase apache is not required to run sslexplorer - and it was conflicting on port 80 with sslexplorer. 

i uninstalled apache and then sslexplorer launched just fine.

now i have to figure out how to use ssl explorer in my ps3 to remote on ubuntu.. ideas? thanks for bearing with me - what an adventure i love ubuntu.   :guitar:

---

