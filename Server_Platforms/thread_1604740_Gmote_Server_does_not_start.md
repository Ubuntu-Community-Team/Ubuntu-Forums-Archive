---
title: "Gmote Server does not start"
date: 2010-10-24
forum: Server Platforms
---

### Post by fabalicious on 2010-10-24
When I start the Gmote Server in the shell (./GmoteServer.sh), I get the following error:
[COLOR=Blue]
$ ./GmoteServer.sh
Starting GmoteServer 2.0 ... 
GmoteServer started.
./GmoteServer.sh: line 2: java: command not found[/COLOR]

[COLOR=Black]VLC's installed. The problem seems to be Java-related. I couldn't find any information on Java prerequirements and how to install/update them.

Any ideas anyone? Thanks a lot in advance.
[/COLOR]

---

### Post by eric_1982 on 2010-10-26
This is what I did to get it working.


sudo aptitude install sun-java6-bin sun-java6-jdk sun-java6-jre vlc  
sudo update-java-alternatives -s java-6-sun

---

