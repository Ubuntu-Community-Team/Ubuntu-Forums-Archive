---
title: "New to the command line"
date: 2008-05-20
forum: Server Platforms
---

### Post by MarioFromBelgium on 2008-05-20
Hi,

first experiences with server commandline.
I want to work with TOMCAT on ubuntu server. So I bought the book "apache tomcat 6"

The third chapter is about installing on linux and starts with :
download a suitable java distribution from [http://java.sun.com](http://java.sun.com)

Can anybody explain me how I do this from the command-line?

Thx

---

### Post by Lod on 2008-05-20
You can take a look at the wiki page of [Tomcat5](https://help.ubuntu.com/community/ApacheTomcat5) installation. Instead of the java 5 you can install java 6 (perhaps take a look in synaptic?).
I've a script at home which installs the complete java6 suite for me. Unfortunately this is on my backup disk and I'm, ahem, at work.

edit: I just remembered I had this link:
[http://www.coreservlets.com/Apache-Tomcat-Tutorial/](http://www.coreservlets.com/Apache-Tomcat-Tutorial/)

I had to program Javaservlets for my study a few years ago. I used this for my installation, it worked like a charm for me.

---

### Post by 505 on 2008-05-20
You could just use "sudo aptitude install sun-java6-bin" With the command you can also install the development kit if needed (sun-java6-jdk)

---

### Post by bobblehat on 2008-05-20
Yep - it's much easier if you do this via one of the available packages.

If you need to you can also set the default java with update-java-alternatives, e.g.

sudo update-java-alternatives -s java-6-sun

---

### Post by MarioFromBelgium on 2008-05-21
Hi guys,

first of all many thanks for the quick reply. 
I have just succesfully installed JAVA.
Nice...but that was not realy my question.
I was hoping to learn how I can download a gzip or tar-file when I'm at the command-line.

Not that I want to install java (and next tomcat) this way, I like the apt-get install command. The problem is this book I'm having which instructs to download the file. It explains the installation for Linux in general. (is apt-get  ubuntu-specific?)

thx

---

### Post by Dr Small on 2008-05-21
Apt-get is debian specific. Ubuntu is based off Debian, so yes, in a sense. The book explains how to compile the programs from source, which basically explains it for any distro.

Just use apt-get to install the needed packages. Don't worry about downloading and compiling the applications if they are already in Ubuntu's repository.

Skip the compiling and installing part in the book, and jump up to configuring the application, once you have installed it from apt-get :)

Good luck,
Dr Small

---

### Post by molotov00 on 2008-05-21
To download a file over HTTP you can use the wget command. Let us know if that's what you were looking for.

---

### Post by MarioFromBelgium on 2008-05-26
Hi,

Like I said, I like the apt-get way of working but what when the program you need to install isn't in )the apt-cache.
I need to setup tomcat 6 (not 5 or earlier) it has to be 6 and guess what ... it is not in the apt-cache.

In another post I mentioned this already in this same forum to make sure I wasen't doing anything wrong. Unfortunately nobody answered so far. So I guess tomcat6 cannot be installed (for the time being) from apt-get.

This means I need to follow the guidelines from my book anyway.
I will need to try this when I'm back home although I don't realy understand how.

see you later!

---

### Post by windependence on 2008-05-26
```
sudo wget http://www.ip97.com/apache.org/tomcat/tomcat-6/v6.0.16/bin/apache-tomcat-6.0.16.zip

sudo wget http://www.ip97.com/apache.org/tomcat/tomcat-6/v6.0.16/bin/apache-tomcat-6.0.16-deployer.zip
```

The first one is the binary package for the core and the second is the deployer package. Make sure you are in the directory you want to download them in before issuing the wget command.


After you have downloaded them you need to:



```
gunzip apache-tomcat-6.0.16.zip


and

gunzip apache-tomcat-6.0.16-deployer.zip
```

There should be instructions in the readme file for installing the binaries. Open the readme file in a text editor.

HTH

-Tim

---

### Post by MarioFromBelgium on 2008-06-04
Hi guys,

Maybe your still following this thread? 
I have succesfully installed Tomcat6
I have set the JAVA_HOME varialble in the ~/.bashrc file.
After closing the session and reopening another again the command echo $JAVA_HOME actually returns a correct path.

Nevertheless when I startup tomcat by means of sh startup.sh from within the bin-folder of the tomcat-tree I get the message that either JAVA_HOME or JRE_HOME is not set......?????

I trying for more than two weeks now starting tomcat. I choose LAMP installation at installation of UBUNTU-server, could that cause a problem?

Mario

---

