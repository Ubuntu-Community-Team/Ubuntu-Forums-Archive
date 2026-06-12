---
title: "Installing java6-jre on headless 10.04 LTS"
date: 2012-04-06
forum: Server Platforms
---

### Post by TechSupportx86 on 2012-04-06
I am trying to setup my new server to run minecraft. The wiki has outdated information and so-far i haven't gotten very far. As you may or may not know, java has been removed from ubuntu because of some license/security hoohockey, so simply adding the source and updating apt no longer works. I tried installing it off of their website, but that didn't work either.

I am trying to install java6-jre, running ubuntu server 10.04 LTS, fresh install. 

Any help would be VERY much appreciated. Once i get it up and running i'll even edit the wiki for all to see :)

---

### Post by Cheesemill on 2012-04-06
```
sudo apt-get install python-software-properties
sudo apt-add-repository ppa:flexiondotorg/java
sudo apt-get update
sudo apt-get install sun-java6-jre
```
Edit - No longer works, Java has been removed from the PPA

Use the following method instead (taken from [http://blog.flexion.org/2012/01/16/install-sun-java-6-jre-jdk-from-deb-packages/](http://blog.flexion.org/2012/01/16/install-sun-java-6-jre-jdk-from-deb-packages/))
By running this script to download Java you acknowledge that you have read and accepted the terms of the Oracle end user license agreement.
[http://www.oracle.com/technetwork/java/javase/terms/license/index.html](http://www.oracle.com/technetwork/java/javase/terms/license/index.html)
```
cd ~/
wget https://raw.github.com/flexiondotorg/oab-java6/master/oab-java6.sh -O oab-java6.sh
chmod +x oab-java6.sh
sudo ./oab-java6.sh
sudo apt-get update
sudo apt-get install sun-java6-jre

```

---

### Post by hawkmage on 2012-04-06
The way Java gets handled in most linux distros package manager bugs me.  For the most part I do not worry about the package managers Java.  I just install the one I want and make sure that it's bin directory is in the path first and that I set the JAVA_HOME environment variable to its location.  

My biggest pet peeve is the way that alternatives is set up for Java.  It is set up for a few of the JRE/JDK command individually.  So if you have multiple versions installed and you want to switch your JRE/JDK you have to do each one.  The JRE commands should be slaves to the java alternative and the JDK commands should be a slave of the javac alternative.

---

