---
title: "OpenVPN ALS (Adito) SSL install problem on Ubuntu 10.04 Server"
date: 2010-09-12
forum: Server Platforms
---

### Post by TaBaScO77 on 2010-09-12
I'm doing a clean install of Ubuntu Server 10.04.  During the install I only choose OpenSSH as one of the install options.  I'm trying to build this server as a dedicated SSL VPN server.

I've read numerous articles on the net, but they all refer to older versions of Ubuntu, other distributions, or older versions of SSL Explorer/Adito/OpenVPN ALS.

These are the steps I follow immediately after installing the OS, and from everything I've read these seem to be correct, but obviously I'm missing something.

sudo -s
apt-get install python-software-properties
add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner" > This is in order to get Sun's version of Java
apt-get update
apt-get upgrade
apt-get install sun-java6-bin sun-java6-jdk ant

At this point I scp the adito-0.9.1-bin.tar.gz to the server.

tar xfvz adito-0.9.1-bin.tar.gz
mv adito-0.9.1 /opt
cd /opt
mv adito-0.9.1 openvpn-als

java -version
> Note: Ensure this is Sun's version of Java.
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) 64-Bit Server VM (build 16.3-b01, mixed mode)

cd /opt/openvpn-als
ant install

When prompted go to [http://(IP](http://(IP) address to server):28080.  This part works just fine.

ant install-service
> Installing the service is also successful, and files are placed under /etc/init.d

service adito start

At this point the server fails to start.  I've tried doing this on both the 32-bit and 64-bit versions of Ubuntu Server, and every time I ultimately get the same errors.  I've been pulling my hair out on this one...

A log is being written at /opt/openvpn-als/wrapper.log that is telling me what the failure is, but I don't understand what it means.  Can anyone help???
FYI -- I've tried openjdk as well with no luck.

Thanks!!!


cat /opt/openvpn-als/wrapper.log
STATUS | wrapper  | 2010/09/12 20:52:19 | --> Wrapper Started as Daemon
STATUS | wrapper  | 2010/09/12 20:52:19 | Launching a JVM...
INFO   | jvm 1    | 2010/09/12 20:52:19 | Exception in thread "main" java.lang.NoClassDefFoundError: Main
INFO   | jvm 1    | 2010/09/12 20:52:19 | Caused by: java.lang.ClassNotFoundException: Main
INFO   | jvm 1    | 2010/09/12 20:52:19 |       at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
INFO   | jvm 1    | 2010/09/12 20:52:19 |       at java.security.AccessController.doPrivileged(Native Method)
INFO   | jvm 1    | 2010/09/12 20:52:19 |       at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
INFO   | jvm 1    | 2010/09/12 20:52:19 |       at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
INFO   | jvm 1    | 2010/09/12 20:52:19 |       at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
INFO   | jvm 1    | 2010/09/12 20:52:19 |       at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
INFO   | jvm 1    | 2010/09/12 20:52:19 | Could not find the main class: Main.  Program will exit.
ERROR  | wrapper  | 2010/09/12 20:52:19 | JVM exited while loading the application.
STATUS | wrapper  | 2010/09/12 20:52:23 | Launching a JVM...
INFO   | jvm 2    | 2010/09/12 20:52:23 | Exception in thread "main" java.lang.NoClassDefFoundError: Main
INFO   | jvm 2    | 2010/09/12 20:52:23 | Caused by: java.lang.ClassNotFoundException: Main
INFO   | jvm 2    | 2010/09/12 20:52:23 |       at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
INFO   | jvm 2    | 2010/09/12 20:52:23 |       at java.security.AccessController.doPrivileged(Native Method)
INFO   | jvm 2    | 2010/09/12 20:52:23 |       at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
INFO   | jvm 2    | 2010/09/12 20:52:23 |       at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
INFO   | jvm 2    | 2010/09/12 20:52:23 |       at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
INFO   | jvm 2    | 2010/09/12 20:52:23 |       at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
INFO   | jvm 2    | 2010/09/12 20:52:23 | Could not find the main class: Main.  Program will exit.
ERROR  | wrapper  | 2010/09/12 20:52:23 | JVM exited while loading the application.
STATUS | wrapper  | 2010/09/12 20:52:27 | Launching a JVM...
INFO   | jvm 3    | 2010/09/12 20:52:28 | Exception in thread "main" java.lang.NoClassDefFoundError: Main
INFO   | jvm 3    | 2010/09/12 20:52:28 | Caused by: java.lang.ClassNotFoundException: Main
INFO   | jvm 3    | 2010/09/12 20:52:28 |       at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
INFO   | jvm 3    | 2010/09/12 20:52:28 |       at java.security.AccessController.doPrivileged(Native Method)
INFO   | jvm 3    | 2010/09/12 20:52:28 |       at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
INFO   | jvm 3    | 2010/09/12 20:52:28 |       at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
INFO   | jvm 3    | 2010/09/12 20:52:28 |       at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
INFO   | jvm 3    | 2010/09/12 20:52:28 |       at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
INFO   | jvm 3    | 2010/09/12 20:52:28 | Could not find the main class: Main.  Program will exit.
ERROR  | wrapper  | 2010/09/12 20:52:28 | JVM exited while loading the application.
STATUS | wrapper  | 2010/09/12 20:52:32 | Launching a JVM...
INFO   | jvm 4    | 2010/09/12 20:52:32 | Exception in thread "main" java.lang.NoClassDefFoundError: Main
INFO   | jvm 4    | 2010/09/12 20:52:32 | Caused by: java.lang.ClassNotFoundException: Main
INFO   | jvm 4    | 2010/09/12 20:52:32 |       at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
INFO   | jvm 4    | 2010/09/12 20:52:32 |       at java.security.AccessController.doPrivileged(Native Method)
INFO   | jvm 4    | 2010/09/12 20:52:32 |       at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
INFO   | jvm 4    | 2010/09/12 20:52:32 |       at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
INFO   | jvm 4    | 2010/09/12 20:52:32 |       at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
INFO   | jvm 4    | 2010/09/12 20:52:32 |       at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
INFO   | jvm 4    | 2010/09/12 20:52:32 | Could not find the main class: Main.  Program will exit.
ERROR  | wrapper  | 2010/09/12 20:52:32 | JVM exited while loading the application.

---

### Post by TaBaScO77 on 2010-09-12
Also, FYI -- I've tried these environment variables as well, and it still fails with the same errors.  The paths are valid.

  export JAVA_HOME=/usr/lib/jvm/java-6-sun
  export PATH=$PATH:$JAVA_HOME/bin

---

### Post by TaBaScO77 on 2010-09-18
Crickets....


I just tried it with Ubuntu 9, and it still comes back with the same errors.  Has anyone had this issue???

Thanks!

---

### Post by BiL0 on 2010-09-22
Hello,

had same problem, tried several things and version but nothing

then I found this post
[http://www.757.org/~joat/wiki/index.php/Installing_OpenVPN-ALS_on_Ubuntu](http://www.757.org/~joat/wiki/index.php/Installing_OpenVPN-ALS_on_Ubuntu)

and as you can see there is a step that we both were missing.
starting the first time via ant

so try this 
"ant start" 
from the adito install directory 
and if you get the same as the post then it will work ;)

hope it helps

B

---

### Post by TaBaScO77 on 2010-09-22
I kept meaning to come back to this post and post the same thing.  Doing an 'ant start' finally fixed it for me too.

Thanks!

---

### Post by charlie0440 on 2010-10-12
In case anyone is still having problems / interested. I wrote a guide on how to install Adito on ubuntu sever 10.04 It can be found [here]("http://www.charliemarshall.com/2011/03/installing-adito-openvpn-als-on-ubuntu.html")

---

### Post by TaBaScO77 on 2010-10-12
Nice post.  Ultimately on the server I set it up on it always gives the users a 404 error when first going to the OpenVPN/Adito login page.  Refreshing the pages fixes it, but it happens every time no matter what computer, OS, or browser the end user is accessing it from.  It never happened when I was testing it in VMs.  Very strange... has anyone else seen this?

---

### Post by greavette on 2010-12-08
I haven't had a problem with 404 errors, but I was having trouble with an Invalid Credential error every time my server was restarted. 

To fix this I created a small script to run at startup that restarts Adito.  So far this has been working for me...hopefully it will help you (and others) as well.  Here is what I did...

Create a new file in /etc/init.d (I called me aditoboot):
```
sudo nano /etc/init.d/aditoboot 
```

Paste the following into your new file:
```
#!/bin/sh 
sleep 5
service adito restart
exit 0
```Save your file: 
CTRL X to save file
Press Y to accept 
CTRL Z to close

Make this file executable:
```
sudo chmod +x /etc/init.d/aditoboot
```

Do this to make your script run on boot:
```
sudo update-rc.d aditoboot defaults
```

I have Adito running on a headless Ubuntu 10.04 server so I installed BUM and used Putty (with X11 forwarding enabled) to view the Bootup Manager window to confirm that my script was set to run at startup just to be sure.

I can now restart my server and log back into Adito.  Hopefully this works for you as well!

charlie0440...I tried adding the above instructions as a comment to your excellent guide you wrote, but it wouldn't let me add it.

---

### Post by paped on 2011-02-21
May have a fix for this (worked for me at least) please see this post - [http://ubuntuforums.org/showthread.php?p=10481506#post10481506](http://ubuntuforums.org/showthread.php?p=10481506#post10481506)

---

### Post by Hutch77 on 2011-06-08
Ok this thread has been helpful but here is the problem I have and hope someone might be able to help... 
When I edit .bashrc as shown here:
3) Edit the .bashrc file:
sudo nano .bashrc
export JAVA_HOME=/usr/lib/jvm/java-6-openjdk
export PATH=$PATH:$JAVA_HOME/bin
java -version

It fails to run through the install with Java errors, I remove it and I can do the install and access the configuration page.  I run through the configuratoin everything passes and hen i do the service install and the start

At this point the page is no longer available.  I have disabled the firewall completely I try localhost on the machine and I try the ip form other machines all get page cannot be displayed.  I tried both FF and IE just to make sure as well.  Apache is running as if I go to the ip address I get the site is working page.

---

### Post by Hutch77 on 2011-06-08
I will add I am doing another clean install just to make sure I did not hose the install on my last try.

---

### Post by Hutch77 on 2011-06-08
so I think I found the problem.  Just unsure how to fix without going to X86

exec: 370: install/platforms/linux/x86/wrapper: not found

This is now coming up when I do the start ant start

---

### Post by TaBaScO77 on 2011-06-08
I wouldn't work for me when I used openjdk.  Try using Oracle's (Sun's) version of Java instead.  Ubuntu makes openjdk the default now, but it seems to have a lot of compatibility issues.

---

### Post by Hutch77 on 2011-06-08
I found the problem, and it was confirmed as I looked a little further at the error,
There is an issue with the script on startup for this.  It tries to default to x86 which does nto exist in a 64 bit, and I saw some people were hard coding to get around, which is way over my head and many that I saw, so I grabbed a 32 bit and voila it worked.

---

