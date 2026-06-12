---
title: "Package installation fails with authentication error"
date: 2010-11-10
forum: Server Platforms
---

### Post by iglablues on 2010-11-10
Hi all. I have a server with the following specs:

Linux version 2.6.27-14-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Fri Jul 24 22:19:33 UTC 2009

Tomcat5.5

I am attempting to install Tomcat6 alongside it as a separate instance. I had tested this out on a test server prior to trying to deploy it to my production server. When I run **sudo apt-get install tomcat6** I get the following:

>  sudo apt-get install tomcat6
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libservlet2.5-java libtomcat6-java tomcat6-common
Suggested packages:
  tomcat6-docs tomcat6-admin tomcat6-examples
The following NEW packages will be installed:
  libservlet2.5-java libtomcat6-java tomcat6 tomcat6-common
0 upgraded, 4 newly installed, 0 to remove and 163 not upgraded.
Need to get 3216kB of archives.
After this operation, 3916kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  libservlet2.5-java libtomcat6-java tomcat6-common tomcat6
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main libservlet2.5-java 6.0.18-0ubuntu3.3
  404 Not Found [IP: 91.189.88.40 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main libservlet2.5-java 6.0.18-0ubuntu3.3
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main libtomcat6-java 6.0.18-0ubuntu3.3
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main tomcat6-common 6.0.18-0ubuntu3.3
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main tomcat6 6.0.18-0ubuntu3.3
  404 Not Found [IP: 91.189.88.37 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java_6.0.18-0ubuntu3.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java_6.0.18-0ubuntu3.3_all.deb)  404 Not Found [IP: 91.189.88.37 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libtomcat6-java_6.0.18-0ubuntu3.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libtomcat6-java_6.0.18-0ubuntu3.3_all.deb)  404 Not Found [IP: 91.189.88.37 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-common_6.0.18-0ubuntu3.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6-common_6.0.18-0ubuntu3.3_all.deb)  404 Not Found [IP: 91.189.88.37 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.18-0ubuntu3.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/tomcat6_6.0.18-0ubuntu3.3_all.deb)  404 Not Found [IP: 91.189.88.37 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


I tried **sudo apt-get update** and **sudo apt-key update** with no success. I checked the url being referenced above and I don't see the file it's looking for (it gets as far as tomcat6-common_6.0.18 but there is no 0ubuntu3.3_all.deb). I'm new-ish to Linux (and even newer to Ubuntu) so I'm not sure what I should be doing to fix this, even though the problem is clear. I just don't know why the file is missing and if I can do anything about it. Here's my /etc/apt/sources.list just in case:

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://ppa.launchpad.net/freenx-team/ppa/ubuntu](http://ppa.launchpad.net/freenx-team/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/freenx-team/ppa/ubuntu](http://ppa.launchpad.net/freenx-team/ppa/ubuntu) intrepid main


I did see this article ([http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/)) which seems to say I shouldn't install Tomcat6 like this anyway, but I wanted to check here first since the Tomcat6 install instructions at help.ubuntu.com are pretty straightforward and uses **apt-get**.  

Thanks in advance for your help and advice.

---

### Post by iglablues on 2010-11-10
Never mind. I was Googling the wrong error. I was looking up "WARNING: The following packages cannot be authenticated!" but as soon as I Googled the 404 error itself I found the answer, in this forum in fact: [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1615471]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1615471"). So, thanks!! Guess I need to update.

---

### Post by James78 on 2010-11-10
Ya, I was just about to tell you that Intrepid Ibex has already reached End of Life.

---

