---
title: "WebSphere 6.1 on Ubuntu 8.10 Server?"
date: 2009-04-08
forum: Server Platforms
---

### Post by f1lite on 2009-04-08
Hi, I'm trying to install WebSphere Application Server v6.1 on Ubuntu Server v8.10, and I'm having no luck getting the install to run.
I've tried the known issues with bash/dash fix, and I've tried using a couple different versions of Java (including IBMs version). Usually with WAS on AIX/Solaris/RHES I simply export my display to my workstations X server and run the ./install script and the installer starts, but with Ubuntu it pauses and returns to a prompt. 
Has anyone successfully installed WAS6.1 on Ubuntu Server at RL2 (no GUI)?

---

### Post by f1lite on 2009-04-22
Nobody has installed WAS on an Ubuntu server?!?

---

### Post by doogy2004 on 2009-04-22
[http://www.google.com/search?q=ubuntu+websphere](http://www.google.com/search?q=ubuntu+websphere)

Second Google result - [http://www-1.ibm.com/support/docview.wss?rs=2359&uid=swg27009332](http://www-1.ibm.com/support/docview.wss?rs=2359&uid=swg27009332)

---

### Post by f1lite on 2009-04-22
Those are all WebSphere Community Edition or Ubuntu workstation installs.

---

### Post by doogy2004 on 2009-04-22
there is no difference between ubuntu server and ubuntu desktop except the kernels are compiled with different options and the desktop has a gui while the server is typically run without a desktop gui.

---

### Post by f1lite on 2009-04-22
I've read all that google has to offer, none were helpful. As I said, the only thing listed on those articles is Community edition installs. Not WAS Network Deployment, and none on 8.10 Ubuntu Server.

---

### Post by doogy2004 on 2009-04-22
you should be able to apply the same concepts of installing the software.  Ubuntu server is essentiall the same as ubuntu desktop.  the version of the operating system does not change the needs of the software that you are attempting to install.  There for the instructions for Desktop should work the same if you are using server.

---

### Post by HDave on 2009-06-09
@f1lite -- How did you make out?  I am interested in getting WAS up and running on Ubuntu as well.

---

### Post by edster99 on 2009-10-07
I have just installed V6 demo version of WAS on 9.04 desktop, no problems.  Run the install, which fails on the profile creation (the final step).  Only thing to note is to run the profile creator with :  sudo /opt/IBM/WebSphere/AppServer/bin/ProfileCreator/pctLinux.bin  which is different from other posts that I have seen.  Now its time to create my new MVC based Enigma emulator...

Having said that, I am now having problems with not being able to find the server configuration which doesnt seem to have been written to the appropriate xml file... so nothing much will start.

---

