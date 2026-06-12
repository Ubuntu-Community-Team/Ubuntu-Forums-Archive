---
title: "Application blocked by security settings - where are these settings?"
date: 2013-04-26
forum: Security
---

### Post by jcoles on 2013-04-26
When I try to run an OpenJDK demo applet (copied from /usr/share/doc/openjdk-7-jre-headless/demo/) in Firefox, I get a dialog that says 

> [SIZE=4]Application Blocked by Security Settings[/SIZE]

Name: Clock

From: file:/home/jcoles/dev/openjdk-demo/applets/Clock/

**Your security settings have blocked a local application from running**

Where are these security settings? How can I regain the ability to run these demo applets? I'm trying to learn about Java.

I like security until it stops me from doing the completely legitimate things that I want to do.

---

### Post by slickymaster on 2013-04-26
Search for the IcedTea Web Control Panel, and click on it and once the window opens check the security settings in it.

---

### Post by jcoles on 2013-04-26
Hi slickymaster, 

Everything in IcedTea Web Control Panel > Security is selected. The options are all positive (allow, show) and none of them imply blocking anything.

---

### Post by jcoles on 2013-04-26
I have solved the problem by re-installing the iced-tea-7-plugin and iced-tea-jre-jamvm packages. 

It's really confusing that there are so many kinds of Java present at the same time: icedtea, jdk, openjdk, jre-cacao, jre-jamvm, default-jre, with even more kinds available in Synaptic. Is it possible to dump everything and install a single Java implementation that will handle all things Java?

---

### Post by slickymaster on 2013-04-26
IMO you should use webupd8 PPA. Not only it provides Oracle Java JDK 7 (which includes Java JDK, JRE and the Java browser plugin), but also it adds an updater to your software sources and you'll always get the latest java update through ubuntu's software updater.

First you have to completely remove the OpenJDK/JRE from your system to prevent system conflicts and confusion between different vendor versions of Java.
Run the following at the command line:
```
sudo apt-get purge openjdk-\*
```
After that, ant to install webupd8 ppa:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

### Post by jcoles on 2013-04-27
I've installed Oracle Java JDK 7 and I'll give it a try. 

The "Application Blocked by Security Settings" warning only ever occurred with local applet examples from vendors. Java apps like muCommander always worked and so did Java apps embedded in web sites. At first the openJDK examples didn't work in Oracle, but then suddenly they started working again. Maybe I just needed to restart the browser a few times. 

The older applet examples that I have still don't work. But now I get "class not found" errors instead of "Application Blocked by Security Settings". I could swear they used to work. At least now I can examine the code and probably learn something.

---

