---
title: "sun-java5-bin install issue on 6.06LTS Server"
date: 2008-05-05
forum: Server Platforms
---

### Post by jbjoret on 2008-05-05
I am trying to setup Sun Java JRE.

I come to the licence terms etc ... I scroll down, do OK, accept the licence on the next screen. NO matter how many time I do this I get the following.

Setting up sun-java5-bin (1.5.0-06-1) ...
Could not create the Java virtual machine.
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java5-bin

From this point Java runs OK, and I cannot see ay java issue. But everytime I use apt-get upgrade or install, I get this same error message with sun-java5-bin not correctly configured. Synaptic is not an option since I am on a server on a VZ. When I call dpkg -l, the sun-java5-bin package is marked "iF" instead of "ii".

Help would be very much appreciated.

---

### Post by jbjoret on 2008-05-05
Ok, I have found a way around this issue, but it looks like the packages from multiverse are not useable unless you use Synaptic.

Here is what I did: install sun-java5-jre then update like this:
Navigate to [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) 
Choose "Java Runtime Environment (JRE) 5.0 Update 15" and click on "Download"
Accept License Agreement 
Download the "Linux self-extracting file"
Install the required tool : 
sudo apt-get install java-package
Create the Ubuntu package : 
fakeroot make-jpkg jre-1_5_0_10-linux-i586.bin
Install the resulting package : 
sudo dpkg -i sun-j2re1.5_1.5.0+update10_i386.deb
sudo update-alternatives --config java select the new java updated package and then ...
sudo apt-get –purge remove sun-java5-jre

if you call "java -version" you will get:

java version "1.5.0_15"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_15-b04)
Java HotSpot(TM) Client VM (build 1.5.0_15-b04, mixed mode)

And all theother dpkg and apt-get issues are gone. But what a trick !

---

